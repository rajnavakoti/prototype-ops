---
name: Group Submissions
description: Scan all open submissions to identify clusters of similar or overlapping ideas and suggest merges. Use when preparing for quarterly review to consolidate the pipeline.
---

# Group Submissions

You are analyzing all current prototype submissions to identify thematic clusters, overlapping solutions, and merge opportunities. This helps the organising team consolidate the pipeline before quarterly review.

## Steps

### 1. Gather All Submissions

Collect submissions from all available sources:

- Use Glob to find all submission files:
  - `examples/*.md` — example submissions
  - `submissions/*.md` — if a submissions directory exists
  - Any other markdown files that follow the submission template format

- Use Bash with `gh issue list --label submitted --json number,title,body,labels,author` to fetch open submission issues from GitHub (if the repo has a remote configured).

- Use Bash with `gh pr list --label submitted --json number,title,body,labels,author` to fetch open submission PRs from GitHub (if the repo has a remote configured).

If GitHub CLI commands fail (no remote, no auth), proceed with local files only and note the limitation.

### 2. Extract Key Information from Each Submission

For each submission found, extract:

- **Title / Name**
- **Problem domain** — what area of the business does this target? (e.g., customer support, inventory, HR, reporting, data processing)
- **Problem statement** — the core problem being solved
- **Technical approach** — what tools, technologies, or methods are used
- **Category** — ai-ml, automation, data, ux, infrastructure, process, other
- **Target users** — who benefits from this prototype

Use Read to examine each submission file. Use Grep to search for thematic keywords across all submissions.

### 3. Identify Thematic Clusters

Group submissions that target the same problem domain or business area. A cluster is 2+ submissions that:

- Address the same underlying business problem (even if from different angles)
- Target the same user group or department
- Operate in the same functional domain (e.g., "customer communication" encompasses chatbots, email automation, and ticket routing)

### 4. Identify Overlapping Solutions

Within and across clusters, find submissions that:

- Use similar technical approaches to different problems (potential shared infrastructure)
- Solve the same specific problem with different implementations (candidates for merge)
- Have complementary capabilities that could be stronger combined

### 5. Generate Grouping Report

Output a structured report with the following sections:

#### Thematic Clusters

For each cluster:
```
### Cluster: [Theme Name]

**Common thread:** [One sentence describing what unites these submissions]

**Submissions:**
- [Submission 1 title] (source: file/issue/PR #) — [one-line summary]
- [Submission 2 title] (source: file/issue/PR #) — [one-line summary]

**Recommendation:** MERGE / KEEP SEPARATE / DISCUSS
**Reasoning:** [Why merge or keep separate. Consider: do they solve the exact same problem? Would combining them create something stronger? Are the teams compatible?]
```

#### Overlap Analysis

For any pair of submissions with significant overlap:
```
- **[Submission A]** vs **[Submission B]**
  - Overlap type: Same problem / Same approach / Complementary
  - Key difference: [What distinguishes them]
  - Recommendation: [Merge into one / Keep both / One subsumes the other]
```

#### Standalone Submissions

List submissions that do not cluster with anything. These are unique and should be evaluated independently.

#### Summary Statistics

- Total submissions scanned: X
- Clusters identified: X
- Submissions in clusters: X
- Standalone submissions: X
- Recommended merges: X

#### Recommendations for Organising Team

- Prioritized list of merge conversations to have before evaluation
- Any gaps observed (problem areas with no submissions)
- Any oversaturated areas (too many submissions solving the same thing)

## Rules

- Do not force clusters. If submissions are only tangentially related, they are standalone.
- Be specific about WHY you recommend merging or keeping separate.
- A merge recommendation means the organising team should facilitate a conversation between submitters, not unilaterally combine them.
- If there are fewer than 3 total submissions, note that clustering is not meaningful at this scale.
