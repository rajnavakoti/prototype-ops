# Submitters Guide

You built something. It works. You think it solves a real problem. This guide tells you how to submit it, what's expected, and how to give your prototype the best chance of being selected.

---

## What Counts as a Prototype

A prototype is a working demonstration of a solution to a real problem. That's it. But the boundaries matter:

**Too early -- an idea:**
"I think we should use AI to classify support tickets." That's an idea. Ideas are free. We need something built.

**Just right -- a prototype:**
"I built a classifier that reads support tickets and tags them by intent and urgency. Here's a demo with 200 real tickets (anonymised). It gets 85% accuracy. It took me 12 hours to build using Claude and Python."

**Too late -- a product:**
"I've deployed this to production, it's handling live traffic, and 50 people use it daily." That's already a product. It doesn't need this program -- it needs a product team.

The sweet spot: **"I built this thing, it works, here's what it solves."**

You don't need to be an engineer. If you used approved AI tools to build a working automation, a functional dashboard, or a prototype that demonstrates the solution -- that qualifies. Prototyping is everyone's right, not just engineering's.

---

## How to Submit

### Step 1: Check existing submissions

Before you build, look at what's already been submitted. Check open PRs and issues in this repo. If someone already submitted something similar, consider reaching out to them and combining efforts instead of duplicating work.

### Step 2: Build your prototype

Use the company's [approved tools](../guidelines/approved-tools.md) and follow the [security guidelines](../guidelines/security-guidelines.md). No confidential data in public repos. No unauthorised AI tools. If you're unsure, ask the organising team.

### Step 3: Frame the problem and value

Before writing a single line in the submission template, read these:
- [Problem Framing](../guidelines/problem-framing.md) -- how to think about your problem in dollar terms
- [Effort Estimation](../guidelines/effort-estimation.md) -- how to honestly estimate what it took to build
- [Value Creation](../guidelines/value-creation.md) -- how to articulate the value your prototype creates

These guides exist to help you make a stronger case, not to create busywork.

### Step 4: Fill out the submission template

Create a PR to this repo using the submission template. Every field is there for a reason:

| Field | What's expected |
|---|---|
| **Problem statement** | 1-2 paragraphs. What real problem does this solve? Who has this problem? |
| **Dollar value framing** | Is this saving money, generating revenue, or reducing risk? Rough numbers. |
| **Working prototype** | Link to code, hosted demo, or video walkthrough. It must work. |
| **Effort so far** | Hours spent. Tools used. Team size (even if it's just you). |
| **What's needed to graduate** | Team size, time, and budget to make this production-ready. |
| **Risk assessment** | Data sensitivity, security implications, integration complexity. |
| **Demo** | Video, screenshots, or live link. Reviewers need to see it working. |

### Step 5: Submit and wait

Once your PR is open, the organising team will acknowledge it within a week and provide preliminary feedback within two weeks. Formal evaluation happens quarterly. You'll get a result with specific feedback regardless of outcome.

---

## Tips for Strong Submissions

### Solve a real problem, not an interesting one
The review panel scores on business value first. "This saves 400 hours per quarter across the support team" beats "This uses a novel transformer architecture" every time. Start with the problem, not the technology.

### Show your math
"This is valuable" is an opinion. "This saves 15 minutes per ticket x 200 tickets/day x $30/hour = $1.5M annually" is an argument. The numbers don't have to be precise, but they have to exist. See [Problem Framing](../guidelines/problem-framing.md).

### Make the demo undeniable
A 2-minute video of your prototype working is worth more than 10 pages of documentation. Show the input, show the process, show the output. If a reviewer can watch your demo and immediately understand the value, you're in good shape.

### Be honest about effort and limitations
"I built this in 8 hours and it handles 80% of cases" is more credible than "This took a weekend and it's production-ready." Reviewers know what's realistic. Honesty about limitations shows maturity. Every prototype has gaps -- name yours.

### Frame graduation realistically
"This needs 2 engineers for 3 months to be production-ready" is actionable. "This just needs some polish" is not. Leadership invests based on your graduation ask. Make it concrete enough to fund.

### Don't wait for perfection
Submit when it works, not when it's finished. A rough prototype submitted in Q1 beats a polished one submitted in Q3. You can always iterate in the next cycle if selected.

---

## What Happens After You Submit

1. **Acknowledgement** -- The organising team tags your submission and confirms receipt within a week.
2. **Preliminary feedback** -- Within two weeks, you'll get initial comments on your submission. This might include requests for clarification or suggestions for improvement.
3. **Quarterly evaluation** -- The review panel scores all submissions using the [evaluation rubric](../evaluation/rubric.md). Every submission gets scored, no exceptions.
4. **Results** -- You'll receive your score and specific feedback. If selected:
   - **Top 5**: Recognition and fast-track to graduation review.
   - **Top 15**: Allocated time (1-2 engineers, 2-3 months) to build it out.
   - **Not selected**: Clear feedback on why and what would make it stronger for resubmission.
5. **Graduation** -- Invested prototypes go through a [graduation review](../evaluation/graduation-paths.md) with four possible outcomes: graduate, iterate, shelve, or kill. Every outcome has closure.

---

## Common Questions

**Can I submit more than one prototype?**
Yes. Submit as many as you want. Each one is evaluated independently.

**Can I submit as a team?**
Yes. List all contributors in the submission. Credit is shared.

**What if someone already submitted something similar?**
Talk to them. The organising team can help connect you. Combined submissions with multiple perspectives are often stronger than competing ones.

**Do I need my manager's approval to submit?**
No. This is open to everyone. You don't need permission to solve problems.

**What if my prototype uses confidential data?**
Follow the [security guidelines](../guidelines/security-guidelines.md). Use anonymised or synthetic data in your demo. Never put confidential data in the repo or any public location.

**Can I resubmit a rejected prototype?**
Yes. Address the feedback from the previous evaluation and resubmit in the next cycle. Iteration is expected and encouraged.
