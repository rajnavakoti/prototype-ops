# Prototype-Ops

**An enterprise prototyping operating model you can fork and run.**

People in your organization are already prototyping -- with AI tools, on weekends, between sprints, in the shadows. You cannot stop it. You can channel it.

Prototype-Ops is a GitHub-based template repository that gives you a complete system for collecting, evaluating, selecting, and graduating prototypes. No custom apps. No Jira plugins. No vendor contracts. Just GitHub, markdown, and a process that works.

---

## Who This Is For

- **Innovation leads** who need a structured way to run prototyping cycles without building a platform
- **Engineering managers** who want to give their teams a legitimate channel for side projects
- **CTOs and VPs** who know their people are building things in the shadows and want to capture that value
- **Anyone** tasked with "setting up an innovation program" who does not want to spend 6 months on tooling

---

## What You Get

When you fork this repo, you get a fully operational prototyping pipeline:

| Component | What It Does |
|---|---|
| [Operating Model](docs/operating-model.md) | The 5-phase system from submission to graduation |
| [Team Manifests](docs/team-manifest/) | Do's and don'ts for leadership, organising teams, and submitters |
| [Evaluation Rubric](docs/evaluation/rubric.md) | Scoring criteria with concrete examples of what good looks like |
| [Graduation Paths](docs/evaluation/graduation-paths.md) | Four outcomes for every prototype: graduate, iterate, shelve, kill |
| [Guidelines](docs/guidelines/) | Problem framing, effort estimation, value articulation, security, approved tools |
| [Issue Templates](.github/ISSUE_TEMPLATE/) | Structured forms for submissions, evaluations, and graduation decisions |
| [PR Template](.github/PULL_REQUEST_TEMPLATE.md) | Standardized format for prototype submissions via pull request |
| [GitHub Actions](.github/workflows/) | Automated submission validation and quarterly reporting |
| [Dashboard](dashboard/) | Static single-page frontend showing pipeline status and metrics |
| [Example Submissions](examples/) | Three complete examples showing exactly what a good submission looks like |

---

## The 5-Phase Model

### 1. DISCOVER (Ongoing)
Rolling submission window. People submit prototypes whenever they are ready -- not during a forced 24-hour hackathon. Submissions are pull requests or issues following a standardized template. All submissions are visible so people do not duplicate effort.

### 2. PROPOSE (Submission)
Every submission must include: a problem statement, dollar value framing, a working prototype (not a slide deck), effort spent so far, what is needed to graduate, risk assessment, and a demo. The bar is "I built this thing, it works, here is what it solves."

### 3. EVALUATE (Quarterly)
A cross-functional review panel scores submissions on five criteria: business value, technical feasibility, resource efficiency, strategic alignment, and innovation factor. Each scored 0-5. The goal is to narrow all submissions down to the top 20.

### 4. SELECT and INVEST
The top 5 get recognition and fast-tracked graduation review. The top 15 get actual allocated time -- 1-2 engineers for 2-3 months. Not "work on this when you have bandwidth." Real investment.

### 5. GRADUATE
Every invested prototype gets one of four outcomes:
- **GRADUATE** -- Fund it, staff it, put it on the product roadmap.
- **ITERATE** -- Good idea, needs refinement. Resubmit next cycle with specific feedback.
- **SHELVE** -- Valuable but not now. Archive code, document learnings, revisit later.
- **KILL** -- Learned enough. Thank the team, close the loop. No zombie prototypes.

---

## Get Started in 5 Steps

### Step 1: Fork this repo
Click "Use this template" or fork it into your organization's GitHub. This is your prototyping pipeline now.

### Step 2: Customize the docs
Update the following for your organization:
- `docs/guidelines/approved-tools.md` -- list the AI and dev tools your company provides
- `docs/guidelines/security-guidelines.md` -- your data and security boundaries
- `docs/references/org-level-problems.md` -- problems specific to your org (or use ours as a starting point)
- `.github/labels.yml` -- adjust cycle labels to match your quarterly timeline

### Step 3: Set up the GitHub infrastructure
- Enable GitHub Issues and Projects on the repo
- Apply the labels from `.github/labels.yml`
- Create a GitHub Project board with columns: Submitted, Under Review, Selected, Invested, Graduated, Shelved, Killed

### Step 3b: Preview the dashboard
The dashboard is a static site that needs an HTTP server (it fetches JSON via `fetch()`). To preview locally:
```bash
npx serve dashboard/
```
Then open the URL shown in your terminal.

### Step 4: Announce it
Send the repo link to your engineering org. Point them to `docs/team-manifest/submitters-guide.md` and the example submissions in `examples/`. The lower the friction, the more submissions you get.

### Step 5: Run your first cycle
Set a submission deadline (e.g., end of quarter). Assemble a review panel (see `docs/evaluation/review-process.md`). Score submissions using the rubric. Announce results. Allocate time to the top 15. Follow up.

---

## Project Structure

```
prototype-ops/
  docs/
    operating-model.md              Full 5-phase operating model
    team-manifest/                  Guides for leadership, organisers, submitters
    guidelines/                     Problem framing, effort estimation, security, tools
    evaluation/                     Rubric, graduation paths, review process
    references/                     Example problems, past cycle records
  templates/                        Submission, evaluation, and graduation templates
  .github/                          Issue templates, PR template, labels, workflows
  .claude/                          Claude Code agents and skills for review automation
  dashboard/                        Static HTML/CSS dashboard
  examples/                         Three complete example submissions
```

---

## Design Decisions

**Why GitHub and not [other tool]?**
Git is the universal tool engineers already use. PRs give you built-in review, discussion, and approval workflows. Issues give you tracking. Labels give you categorization. Projects give you pipeline visualization. Everything is version controlled, auditable, and in one place. No new tool to adopt.

**Why working prototypes and not ideas?**
Ideas are cheap. Execution is what matters. Requiring a working prototype -- even a rough one -- filters for people who have actually engaged with the problem deeply enough to build something. It also means the review panel can evaluate something real, not a pitch deck.

**Why rolling submissions and not a hackathon?**
Hackathons create artificial urgency and exclude people who cannot dedicate a weekend. Rolling submissions let people work at their own pace, think deeply about the problem, and submit when the prototype is actually ready.

**Why quarterly evaluation?**
Frequent enough to maintain momentum. Infrequent enough to accumulate a meaningful pool of submissions. Aligned with how most organizations already plan and budget.

---

## Notes for Maintainers

- **Claude Code permissions**: `.claude/settings.json` ships with broad permissions for development convenience. Review and tighten before giving write access to contributors.
- **Dashboard serving**: The dashboard uses `fetch()` so it needs an HTTP server. Use `npx serve dashboard/` locally.

---

## What This Is NOT

- Not a product with auth, databases, or multi-tenancy
- Not a hackathon management platform
- Not an AI governance framework (though it helps with shadow AI by giving it a legitimate channel)
- Not theoretical -- everything in this repo is designed to be used immediately after forking

---

## License

MIT. Fork it, use it, make it yours.
