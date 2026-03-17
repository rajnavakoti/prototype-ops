# Prototype-Ops

## What This Is
An enterprise prototyping operating model — a GitHub-based template repo that any organization can fork to channel prototyping energy into structured value creation. NOT an app. A system.

The core thesis: people in enterprises are prototyping constantly (with AI tools, on weekends, in shadows). You can't stop it. You can channel it. This repo IS the channel.

## Architecture

This is a **template repository**, not a product. The value is in:
1. **Documentation** — the operating model, team manifests, guidelines
2. **GitHub native workflows** — issue templates, PR templates, labels, project boards
3. **Submission templates** — standardized format for prototype submissions (as PRs)
4. **Evaluation rubrics** — how to score and select prototypes
5. **Claude Code extensions** — agents/skills for submission review, evaluation, grouping, dashboard generation
6. **Simple frontend** — a single-page dashboard to visualize submissions, status, and outcomes

## Key Design Decisions

### GitHub as the Management Layer
- No Jira, no ServiceNow, no custom app
- Git is the universal tool engineers already use
- PRs = submissions (decisions recorded, challenged, approved/rejected)
- Issues = tracking evaluation and graduation
- Labels = categorization and status
- GitHub Projects = pipeline visualization
- Everything is version controlled, auditable, in one place

### Submission = Prototype (Not Idea, Not Product)
- Submissions must include a WORKING prototype (minimum viable demo)
- Not sketches or slide decks (too early)
- Not deployed applications (too late)
- The sweet spot: "I built this thing, it works, here's what it solves"

### Rolling Submissions, Quarterly Selection
- People submit at their own pace (not one-day hackathon pressure)
- Quarterly evaluation cycles by a cross-functional review panel
- Top 5 rewarded, top 15 invested in

## Project Structure

```
prototype-ops/
├── CLAUDE.md
├── REQUIREMENTS.md
├── README.md                          # What this repo is, how to fork and use it
├── docs/
│   ├── operating-model.md             # The full operating model (5 phases)
│   ├── team-manifest/
│   │   ├── leadership-team.md         # Do's and don'ts for leadership
│   │   ├── organising-team.md         # Do's and don'ts for organising team
│   │   └── submitters-guide.md        # Guide for people submitting prototypes
│   ├── guidelines/
│   │   ├── approved-tools.md          # AI tools offered by the company
│   │   ├── security-guidelines.md     # What you can and can't use/share
│   │   ├── problem-framing.md         # How to think about problems (dollar value)
│   │   ├── effort-estimation.md       # How to estimate build effort
│   │   └── value-creation.md          # How to articulate value created
│   ├── evaluation/
│   │   ├── rubric.md                  # Scoring criteria for submissions
│   │   ├── graduation-paths.md        # 4 paths: graduate, iterate, shelve, kill
│   │   └── review-process.md          # How the quarterly review works
│   └── references/
│       ├── org-level-problems.md      # Example org-level problems to solve
│       └── past-submissions.md        # Template for documenting past cycles
├── templates/
│   ├── submission-template.md         # What a PR-based submission looks like
│   ├── evaluation-template.md         # Reviewer scoring template
│   └── graduation-template.md         # Post-evaluation outcome template
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── submission.yml             # GitHub issue form for submissions
│   │   ├── evaluation.yml             # Issue form for evaluation tracking
│   │   └── graduation.yml             # Issue form for graduation decisions
│   ├── PULL_REQUEST_TEMPLATE.md       # PR template for prototype submissions
│   ├── labels.yml                     # Predefined labels for categorization
│   └── workflows/
│       ├── submission-check.yml       # Validate submission format
│       └── quarterly-report.yml       # Generate quarterly summary
├── .claude/
│   ├── settings.json
│   ├── agents/
│   │   └── reviewer.md               # Agent that reviews submissions
│   └── skills/
│       ├── evaluate-submission.md     # Skill to score a submission against rubric
│       ├── group-submissions.md       # Skill to identify overlapping/similar submissions
│       ├── quarterly-report.md        # Skill to generate cycle summary report
│       └── dashboard-update.md        # Skill to update the frontend dashboard
├── dashboard/                         # Simple static frontend
│   ├── index.html                     # Single-page dashboard
│   ├── styles.css                     # Monochrome neo-brutalist styling
│   └── data/
│       └── submissions.json           # Data file generated from GitHub issues/PRs
└── examples/
    ├── example-submission-1.md        # Example: AI-powered inventory alerting
    ├── example-submission-2.md        # Example: Meeting summary automation
    └── example-submission-3.md        # Example: Customer feedback classifier
```

## Tech Stack
- Documentation: Markdown (everything is markdown)
- Workflows: GitHub Actions
- Dashboard: Static HTML/CSS/JS (no framework, no build step — forkable simplicity)
- Extensions: Claude Code agents and skills
- Styling: Monochrome neo-brutalist (from global design system)

## Content Tone
- Direct, practical, no corporate fluff
- Written for the person who has to actually set this up
- Opinionated — this repo takes positions, doesn't try to please everyone
- Examples are concrete, not abstract

## Commit Strategy
- Small, focused commits
- Use conventional commit prefixes: feat:, docs:, chore:, fix:
- Never commit to main directly — use feature branches
- Reference issue numbers in commits and PRs

## What This Is NOT
- Not a product with user auth, databases, multi-tenancy
- Not a hackathon management tool
- Not an AI governance framework (though it helps with shadow AI)
- Not theoretical — everything should be immediately usable when forked
