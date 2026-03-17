# Prototype-Ops — Requirements

## Vision

Every enterprise has people prototyping in the shadows — with AI tools, on weekends, between sprints. The energy is already there. Prototype-Ops is a template GitHub repo that any organization can fork to channel that energy into structured value creation.

This is not a hackathon. It's a permanent operating model with cadence, evaluation, graduation paths, and governance — all managed through GitHub.

---

## The Operating Model (5 Phases)

### Phase 1: DISCOVER (Ongoing)
- Rolling submission window — people submit prototypes anytime, not during a one-day event
- Submissions are PRs to the repo following a standardized template
- Low barrier: "I built this thing, it works, here's what it solves"
- Transparency: all submissions visible so people don't duplicate efforts
- Organising team available for pika/coffee chats to help submitters sharpen their proposals

### Phase 2: PROPOSE (Submission Requirements)
Each submission PR must include:
- **Problem statement** (1-2 paragraphs): what real problem does this solve?
- **Dollar value framing**: is this saving money, generating revenue, or reducing risk? Rough estimate.
- **Working prototype**: not a sketch, not a deployed product. A minimum working demo.
- **Effort so far**: how much time/resources went into building this?
- **What's needed to graduate**: team size, time, budget to make this production-ready
- **Risk assessment**: data sensitivity, security implications, integration complexity
- **Demo**: link to video, screenshots, or live demo

### Phase 3: EVALUATE (Quarterly)
- Cross-functional review panel (4-5 people):
  - One executive (business alignment)
  - One technical leader (feasibility)
  - One ops/security person (risk)
  - One person from a different org/department (breaks silos)
- Standardized rubric scoring:
  - Business value (0-5)
  - Technical feasibility (0-5)
  - Resource efficiency (0-5)
  - Strategic alignment (0-5)
  - Innovation factor (0-5)
- Goal: narrow to top 20 from all submissions

### Phase 4: SELECT & INVEST
- **Top 5: Reward** — recognition, small prize, fast-track to graduation review
- **Top 15: Invest** — 2-3 months of dedicated time (1-2 engineers, part-time)
- Not "work on this when you have bandwidth" — actual allocated time
- Regular check-ins with organising team during build phase

### Phase 5: GRADUATE
Four possible outcomes for every invested prototype:
- **GRADUATE**: Fund it, staff it, integrate into product roadmap. It's real now.
- **ITERATE**: Good idea, needs refinement. Queue for next cycle with specific feedback.
- **SHELVE**: Valuable but not now. Archive code, document learnings, revisit later.
- **KILL**: Learned enough. Thank the team, archive the code, close the loop.

Every path has closure. No zombie prototypes.

---

## Documentation Requirements

### Operating Model Docs
1. **operating-model.md** — Full 5-phase model with timelines, responsibilities, examples
2. **graduation-paths.md** — Detailed criteria for each of the 4 outcomes
3. **review-process.md** — How quarterly reviews work, who's involved, how decisions are made
4. **rubric.md** — The scoring system with examples of what a 1 vs 5 looks like for each criterion

### Team Manifest Docs
3. **leadership-team.md** — Do's and Don'ts for leadership involvement
   - Do's: take time to learn what people are solving, show up to demo days, fund what works, give honest feedback on rejections
   - Don'ts: treat this as a PR exercise, promise funding without follow-through, pick winners based on politics, ignore submissions from non-engineering teams
4. **organising-team.md** — Do's and Don'ts for the operating team
   - Do's: be open-minded, use GitHub labels/tags to group similar ideas, merge overlapping submissions, look for patterns in what's getting built (that tells you the real problems), build Claude Code extensions to help people prototype faster, have a simple dashboard to visualize the pipeline
   - Don'ts: gatekeep submissions, add process for process sake, let evaluations pile up, play favorites
5. **submitters-guide.md** — How to submit, what's expected, tips for strong submissions

### Guidelines Docs
6. **problem-framing.md** — How to think about problems in dollar terms (saving X hours/week × Y people × hourly cost = annual value)
7. **effort-estimation.md** — How to estimate build effort honestly
8. **value-creation.md** — How to articulate the value your prototype creates
9. **approved-tools.md** — Template for listing AI tools the company provides and how to use them effectively. Helps with shadow AI by showing people the power of tools they already have.
10. **security-guidelines.md** — What you can and can't use. What data is off-limits. How to prototype safely. This is the shadow AI education layer — not a policy doc but practical guidance.

### Reference Docs
11. **org-level-problems.md** — Template with example org-level problems to inspire submissions (e.g., "customer support ticket classification", "internal knowledge search", "meeting action item tracking")
12. **past-submissions.md** — Template for documenting what happened in previous cycles, what graduated, what was killed, and why

---

## GitHub Infrastructure

### Issue Templates (YAML forms)
13. **submission.yml** — Structured form matching the submission template fields (problem, value, prototype link, effort, ask, risk, demo)
14. **evaluation.yml** — Reviewer scoring form (the 5 rubric criteria, comments, recommendation)
15. **graduation.yml** — Post-evaluation outcome form (outcome type, reasoning, next steps, team assignment)

### PR Template
16. **PULL_REQUEST_TEMPLATE.md** — For prototype submissions via PR (mirrors submission template)

### Labels
17. **labels.yml** — Predefined label set:
    - Status: `submitted`, `under-review`, `selected`, `invested`, `graduated`, `iterated`, `shelved`, `killed`
    - Category: `ai-ml`, `automation`, `data`, `ux`, `infrastructure`, `process`, `other`
    - Priority: `top-5`, `top-15`, `not-selected`
    - Cycle: `Q1-2026`, `Q2-2026`, etc.

### GitHub Actions Workflows
18. **submission-check.yml** — Validates that submission PRs/issues follow the template format (all required fields present)
19. **quarterly-report.yml** — Generates a summary of the current cycle: total submissions, categories breakdown, status distribution, graduation rate

---

## Claude Code Extensions

### Agent
20. **reviewer.md** — Agent that reviews prototype submissions
    - Reads submission against the rubric
    - Flags missing fields
    - Suggests category labels
    - Identifies similar/overlapping submissions in the repo
    - Provides a preliminary score with reasoning
    - Read-only: Glob, Grep, Read tools only (purple, opus)

### Skills
21. **evaluate-submission.md** — Score a specific submission against the rubric, generate structured evaluation output
22. **group-submissions.md** — Scan all open submissions, identify clusters of similar/overlapping ideas, suggest merges
23. **quarterly-report.md** — Generate the quarterly cycle report from GitHub issues data
24. **dashboard-update.md** — Parse submissions data and update the dashboard's submissions.json

---

## Frontend Dashboard

25. **index.html** — Single-page static dashboard showing:
    - Current cycle status (open/closed, submission count, days remaining)
    - Pipeline view: submissions → under review → selected → invested → outcome
    - Category breakdown (how many AI/ML vs automation vs data vs other)
    - Historical graduation rate across cycles
    - Individual submission cards with status, score, category

26. **styles.css** — Monochrome neo-brutalist styling
    - Heavy borders, no rounded corners
    - Black/white/gray palette only
    - Dense data display
    - CSS custom properties for theming

27. **submissions.json** — Data file that the dashboard reads from. Generated/updated by the dashboard-update skill from GitHub issues/PRs.

---

## Example Submissions

28. **example-submission-1.md** — "AI-Powered Inventory Alert System" — a prototype that monitors stock levels and predicts shortages using historical data
29. **example-submission-2.md** — "Meeting Decision Recorder" — a prototype that extracts action items and decisions from meeting transcripts
30. **example-submission-3.md** — "Customer Feedback Classifier" — a prototype that categorizes support tickets by intent and urgency

Each example should follow the submission template exactly — they serve as reference for real submitters.

---

## Milestones

### Milestone 1: Foundation (Issues 1-12)
- Repository structure, README, all documentation
- This is the core value — the operating model in markdown

### Milestone 2: GitHub Infrastructure (Issues 13-19)
- Issue templates, PR template, labels, GitHub Actions
- Makes the repo functional as a submission pipeline

### Milestone 3: Claude Code Extensions (Issues 20-24)
- Reviewer agent, evaluation/grouping/reporting skills
- Makes the organising team's job easier with AI assistance

### Milestone 4: Dashboard & Examples (Issues 25-30)
- Static frontend, example submissions
- Makes the repo visually compelling and immediately understandable

---

## Success Criteria
- Someone can fork this repo and run their first prototyping cycle within a week
- All documentation is practical and actionable, not corporate fluff
- The Claude Code extensions genuinely save the organising team time
- The dashboard tells the story at a glance
- The examples make it obvious how to submit
