---
name: Evaluate Submission
description: Score a specific prototype submission against the evaluation rubric and generate structured evaluation output matching the evaluation template format.
argument-hint: <submission-file-path-or-issue-number>
---

# Evaluate Submission

You are evaluating a prototype submission against the prototype-ops scoring rubric. Your goal is to produce a rigorous, evidence-based evaluation that matches the evaluation template format.

## Input

The submission reference is: $ARGUMENTS

This can be:
- A file path (e.g., `examples/example-submission-1.md` or an absolute path)
- A GitHub issue number (e.g., `#5` or `5`)

## Steps

### 1. Read the Submission

- If $ARGUMENTS looks like a file path, use the Read tool to read the submission file.
- If $ARGUMENTS looks like an issue number, use Bash with `gh issue view <number>` to fetch the issue content.
- If the submission cannot be found, stop and report the error clearly.

### 2. Read the Rubric

Read the scoring rubric for reference:

```
docs/evaluation/rubric.md
```

### 3. Read the Evaluation Template

Read the output format template:

```
templates/evaluation-template.md
```

### 4. Score Against All 5 Criteria

For each criterion, score on a 0-5 integer scale. Follow the rubric definitions exactly.

#### Criterion 1: Business Value (0-5)
- Does this solve a real, measurable problem?
- Is the dollar value framing credible and defensible?
- Who benefits and at what scale?
- Red flags that cap at 2: no problem statement, solution looking for a problem, only benefits the submitter.

#### Criterion 2: Technical Feasibility (0-5)
- Is the prototype working, not slideware?
- Are the hard technical problems solved or hand-waved?
- Is the tech stack reasonable for the org?
- Red flags that cap at 2: "works on my machine" only, unapproved APIs, no data privacy consideration, happy-path-only demo.

#### Criterion 3: Resource Efficiency (0-5)
- What is the ratio of investment needed to value delivered?
- Has the submitter considered build vs. buy?
- Is the effort estimate honest and detailed?
- Red flags that cap at 2: no effort estimate, vague "we just need resources," requires hiring specialists.

#### Criterion 4: Strategic Alignment (0-5)
- Does this connect to real organizational priorities?
- Is the alignment genuine or name-dropping?
- Red flags that cap at 2: strategy buzzwords without substance, solves yesterday's priority.

#### Criterion 5: Innovation Factor (0-5)
- Is this a genuinely new approach or off-the-shelf replication?
- Does it leverage unique organizational data or domain knowledge?
- Red flags that cap at 2: reimplementation of a tutorial, just connecting two APIs.

### 5. Calculate Total and Determine Recommendation

- Total Score = sum of all five criteria (max 25)
- Apply selection thresholds:
  - 20-25: **Strong Yes** — Top-tier, prioritize for investment
  - 15-19: **Yes** — Solid, worth investing this cycle
  - 10-14: **Maybe** — Has potential, needs specific improvements
  - Below 10: **No** — Not ready for investment this cycle

### 6. Write Summary and Suggested Actions

- Write a 2-3 sentence summary capturing the overall assessment.
- List 2-4 specific, actionable suggestions for the submitter regardless of outcome.
- Identify key strengths (what stands out positively).
- Identify key weaknesses (what concerns you).

## Output Format

Output the evaluation in the exact format of `templates/evaluation-template.md`, filling in all fields:

- Header block with submission title, issue/PR number, reviewer (Claude Code), review date (today), cycle
- All 5 scoring sections with score and detailed comments (minimum one full sentence per criterion)
- Total score table
- Overall recommendation (exactly one checkbox marked)
- Summary paragraph
- Suggested actions list

Every score MUST include reasoning that references specific evidence from the submission. A number without justification is not acceptable.

## Rules

- Be honest and direct. Do not inflate scores.
- Reference specific parts of the submission as evidence for your scores.
- If the submission is missing required fields (problem statement, dollar value, demo, effort estimate, risk assessment), note this explicitly and score accordingly.
- If information is ambiguous, state the ambiguity and score conservatively.
- Do not add scores for criteria where the submission provides zero information — score those as 0 or 1.
