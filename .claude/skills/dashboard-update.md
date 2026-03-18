---
name: Dashboard Update
description: Parse prototype submission data from GitHub issues and update the dashboard's submissions.json data file.
---

# Dashboard Update

You are updating the dashboard data file by fetching current submission data from GitHub issues and PRs.

## Steps

### 1. Fetch All Submission Issues and PRs

Use Bash with the `gh` CLI to fetch all issues that have any submission-related status label:

```bash
# Fetch issues with any status label
gh issue list --state all --json number,title,labels,author,body,url,createdAt --limit 500

# Fetch PRs with submission labels
gh pr list --state all --json number,title,labels,author,body,url,createdAt --limit 500
```

Filter results to only include items that have at least one of these status labels:
`submitted`, `under-review`, `selected`, `invested`, `graduated`, `iterated`, `shelved`, `killed`

If the `gh` CLI is not available or the repo has no remote configured, report the error and stop. This skill requires GitHub data access to function.

### 2. Extract Data from Each Issue/PR

For each qualifying issue or PR, extract:

- **id** — the issue or PR number
- **title** — the issue/PR title
- **submitter** — the author's GitHub login
- **status** — derived from status labels (submitted, under-review, selected, invested, graduated, iterated, shelved, killed). Use the most advanced status if multiple are present. Priority order: graduated > killed > shelved > iterated > invested > selected > under-review > submitted
- **category** — derived from category labels (ai-ml, automation, data, ux, infrastructure, process, other). Default to "other" if no category label is present
- **score** — look for a score in the issue body or comments. Search for patterns like "Total: X/25", "Score: X/25", or a total score table. Set to `null` if no score is found
- **cycle** — derived from cycle labels (e.g., Q1-2026, Q2-2026). Set to `null` if no cycle label is present
- **summary** — extract the first paragraph of the issue body (after any YAML frontmatter or heading). Truncate to 200 characters if longer
- **url** — the HTML URL of the issue or PR

### 3. Read Existing Data

Check if `dashboard/data/submissions.json` already exists:

- If it exists, read it with the Read tool
- Parse the existing entries
- Identify any manually-added entries (entries with IDs that do not match any GitHub issue/PR number, or entries with an `"id"` that starts with `"manual-"`)
- Preserve manually-added entries in the output

### 4. Merge and Generate Updated JSON

Build the updated JSON file:

- Start with an empty array
- Add all entries fetched from GitHub (updating any existing entries with the same id)
- Append any manually-added entries from the existing file that were preserved
- Sort the array by id (numeric ascending)

The schema for each entry:
```json
{
  "id": 1,
  "title": "AI-Powered Inventory Alert System",
  "submitter": "githubuser",
  "status": "submitted",
  "category": "ai-ml",
  "score": null,
  "cycle": "Q1-2026",
  "summary": "A prototype that monitors stock levels and predicts shortages using historical data.",
  "url": "https://github.com/org/prototype-ops/issues/1"
}
```

Field types:
- `id`: number (issue/PR number) or string (for manual entries like `"manual-1"`)
- `title`: string
- `submitter`: string (GitHub login)
- `status`: string, one of: submitted, under-review, selected, invested, graduated, iterated, shelved, killed
- `category`: string, one of: ai-ml, automation, data, ux, infrastructure, process, other
- `score`: number (0-25) or null
- `cycle`: string (e.g., "Q1-2026") or null
- `summary`: string (max 200 characters)
- `url`: string (full URL)

### 5. Write the Updated File

Ensure the `dashboard/data/` directory exists (create it if needed using Bash: `mkdir -p dashboard/data`).

Write the updated JSON array to `dashboard/data/submissions.json` using the Write tool. Format the JSON with 2-space indentation for readability.

### 6. Report Changes

After writing, output a summary:

```
## Dashboard Update Summary

- **Total entries:** X
- **Added:** X new submissions
- **Updated:** X existing submissions refreshed
- **Unchanged:** X entries with no changes
- **Manual entries preserved:** X
- **Data source:** GitHub Issues & PRs via gh CLI
```

List each added or updated entry by title and what changed (new entry, status change, score added, etc.).

## Rules

- Never overwrite manually-added entries. Preserve them.
- If an issue/PR has no status label at all, skip it — it is not a submission.
- Always format the JSON output with 2-space indentation.
- If the `dashboard/data/submissions.json` file does not exist yet, create it as a new file with just the GitHub-sourced entries.
- Do not include issue/PR body content beyond the summary field. Keep the data file lean.
- If no qualifying submissions are found on GitHub, write an empty array `[]` and report that no submissions were found.
