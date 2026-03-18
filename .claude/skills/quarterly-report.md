---
name: Quarterly Report
description: Generate a quarterly cycle report summarizing submissions, outcomes, patterns, and metrics from GitHub issues data.
argument-hint: <cycle-label e.g. Q1-2026>
---

# Quarterly Report

You are generating a quarterly cycle report for the prototype-ops program. This report summarizes what happened during a specific evaluation cycle.

## Input

The cycle identifier is: $ARGUMENTS

This should be a cycle label like `Q1-2026`, `Q2-2026`, etc. If not provided, ask the user which cycle to report on.

## Steps

### 1. Fetch Submission Data from GitHub

Use Bash with the `gh` CLI to query issues and PRs for this cycle. Run these queries:

```bash
# All issues with the cycle label
gh issue list --label "$ARGUMENTS" --state all --json number,title,labels,author,state,createdAt,closedAt,body --limit 200

# All PRs with the cycle label
gh pr list --label "$ARGUMENTS" --state all --json number,title,labels,author,state,createdAt,closedAt,body --limit 200
```

If the gh CLI is not available or the repo has no remote, fall back to scanning local files:
- Use Glob to find files in `examples/`, `submissions/`, and any evaluation files
- Note the limitation in the report

### 2. Count Submissions by Status

Parse the labels on each issue/PR and count by status label:

| Status | Count |
|--------|-------|
| submitted | |
| under-review | |
| selected | |
| invested | |
| graduated | |
| iterated | |
| shelved | |
| killed | |

### 3. Count Submissions by Category

Parse category labels and count:

| Category | Submissions | Selected (Top 15) | Top 5 |
|----------|-------------|-------------------|-------|
| ai-ml | | | |
| automation | | | |
| data | | | |
| ux | | | |
| infrastructure | | | |
| process | | | |
| other | | | |

### 4. Calculate Key Metrics

- **Total submissions** — count of all issues/PRs with the cycle label
- **Unique submitters** — count of distinct authors
- **First-time submitters** — if previous cycle data is available, identify new participants
- **Graduation rate** — (graduated count / total submissions) as a percentage
- **Selection rate** — (selected + invested count / total submissions) as a percentage
- **Most popular category** — category with the most submissions
- **Average score** — if evaluation scores are available in issue bodies or comments, extract and average them
- **Top scorer** — highest scoring submission if scores are available

### 5. Identify Trends and Patterns

Analyze the data to identify:

- **Most common problem area** — what domain attracted the most submissions
- **Underrepresented areas** — categories with few or no submissions
- **Overlapping submissions** — were there clusters of similar ideas?
- **Quality observations** — any notable patterns in scores or outcomes
- **Timing patterns** — when were most submissions made (early vs. late in the window)?

### 6. Generate the Report

Output the report in markdown format matching the structure in `docs/references/past-submissions.md`. Include:

#### Header
```
## Cycle: $ARGUMENTS

**Submission window:** [dates if available]
**Evaluation date:** [date if available]
**Review panel:** [names if available from graduation issues]
```

#### Summary Table
Total submissions, unique submitters, first-time vs. repeat submitters.

#### Category Breakdown Table
Full category breakdown with selection counts.

#### Outcomes Table
Count of each outcome (graduated, iterate, shelved, killed) with prototype names.

#### Top 5 Section
For each of the top 5 (if identifiable from labels):
- Submitter, category, problem summary, rubric score, outcome, next steps

#### Key Learnings
Based on patterns observed in the data.

#### Patterns Observed
- Most common problem area
- Underrepresented areas
- Overlapping submissions
- Quality trends

#### Notable Submissions Outside Top 5
Any submissions worth highlighting.

## Rules

- If data is incomplete (no scores, no outcomes yet), generate what you can and clearly mark sections as "Data not yet available."
- Do not fabricate data. If a metric cannot be calculated, say so.
- Use actual issue/PR numbers as references throughout the report.
- If this is the first cycle, skip the "Graduation Follow-Up from Previous Cycle" section or note it as N/A.
- Keep the tone direct and factual. This is a record, not a marketing document.
