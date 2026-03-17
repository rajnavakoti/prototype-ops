# The Prototyping Operating Model

## The Problem You Already Have

Your people are prototyping. Right now. With AI tools, on weekends, between sprints, during lunch breaks. Engineers, analysts, designers, product managers -- anyone with access to Claude, ChatGPT, Copilot, or a dozen other tools is building things. They're not waiting for permission. They're not filing Jira tickets. They're solving problems they see every day and nobody is paying attention.

This is not a future trend. This is happening in your organization today.

As an enterprise, you have two instinctive responses, and both are wrong.

**Response 1: Pretend it's not happening.**
"If I don't look at it, it's not there." Meanwhile, someone three levels deep in your org has already solved a million-dollar problem and can't ship it because the PO says the Jira backlog is the priority. Or worse -- someone has unknowingly pushed confidential data to a public AI tool because nobody told them not to.

**Response 2: Lock it down.**
Big boss energy. Monitor everything. Block the tools. Kill all the innovation before the seeds even germinate. Congratulations, you've protected the company and demoralized every motivated person in it.

There is a third way. You channel it.

Not with a policy memo. Not with a governance committee. With an operating model that turns unstructured prototyping energy into structured value creation -- while handling the security and duplication problems as a side effect.

That's what this is.

---

## Why This Exists

Two forces are colliding in every enterprise right now:

**1. The prototyping explosion is real and accelerating.**
Every major AI release adds fuel. Context windows get larger, models get smarter, tools get easier. The barrier to building a working prototype has dropped from weeks to hours. It can be excitement, FOMO, or genuine problem-solving instinct -- but everyone wants to build the next big thing. That energy is valuable. Wasting it is a strategic failure.

**2. Shadow AI is the security risk nobody is managing effectively.**
When people prototype in the shadows, they make mistakes. They paste customer data into unauthorized tools. They deploy to personal cloud accounts. They share API keys in Slack. The excitement always brings security risk. Announcements about "be careful with unauthorized AI tools" don't work -- nobody reads them, nobody changes behavior. You need a model that makes the safe path the easy path.

---

## What You've Probably Already Tried

### Hackathons
Yes, everyone is doing them. A full day of high adrenaline, end-of-day presentations, a few standouts, investment promises, and then -- new dawn, new day, back to the same work.

Hackathons fail as an operating model because:

- **They're events, not systems.** One-off days of energy that don't compound. The Monday after a hackathon, nothing has changed.
- **They reward speed, not value.** The flashiest demo wins, not the most important problem solved.
- **They produce demos, not solutions.** Winning a hackathon means a trophy. It does not mean funding, staffing, or a path to production.
- **They don't solve shadow AI.** Hackathons are a separate event. Engineers go right back to prototyping in the shadows the next week.
- **They're top-down.** The org picks the date, the theme, the judges. The people with the best ideas might be busy that day. Or their idea doesn't fit the theme. Or they need three weeks, not eight hours.

Hackathons are fine for awareness and team building. They are not a strategy for capturing prototyping value.

### Security Announcements and Policy Memos
"Please be aware of our data protection policies when using AI tools." Nobody attends the meeting. Nobody reads the email. Behavior doesn't change.

### AI Awareness Events
Expensive. Low lasting value. People leave excited and then have no channel for that excitement.

### AI Governance and Adoption Teams
Most employees don't even know they exist in the company. These teams write policy for other teams to ignore.

---

## The Operating Model

A rolling submission system with quarterly selection cycles. No fixed event dates. No artificial time pressure. People prototype at their own pace and submit when they have something working. A cross-functional team evaluates quarterly. The best ideas get investment. Every submission gets closure.

Five phases. Here's how it works.

---

## Phase 1: DISCOVER

**What happens:** The submission window is always open. People identify problems, build prototypes, and prepare submissions on their own schedule.

**Duration:** Ongoing, continuous. There is no "submission period" -- the door is always open.

**Who's involved:**
- *Submitters* -- anyone in the organization. Not just engineers. "People" is the right word here because prototyping is no longer an engineering-only activity.
- *Organising team* -- available for informal guidance, coffee chats, and early feedback.

**How it works:**

Submitters identify a real problem they encounter in their work. They build a working prototype that demonstrates a solution. The emphasis is on *working* -- not a sketch on a napkin, not a slide deck, not a fully deployed application. The sweet spot: "I built this thing, it works, here's what it solves."

The organising team maintains transparency into existing submissions so people can see what's already been proposed. This prevents duplication and sparks collaboration -- if someone sees a submission close to their idea, they can team up rather than compete.

The organising team also makes themselves available for informal chats. Not gatekeeping sessions. Conversations to help submitters sharpen their proposals, think about value framing, and avoid common pitfalls.

**Supporting resources available to submitters:**
- Problem framing guidelines -- how to think about problems in dollar terms
- Effort estimation guidance -- how to honestly estimate what it took to build
- Value creation frameworks -- how to articulate the value created
- Approved tools list -- what AI tools the company provides and how to use them effectively
- Security guidelines -- what you can and can't do, what data is off-limits, how to prototype safely
- Reference problems -- example org-level problems to inspire submissions

These docs serve a dual purpose. They help submitters create stronger proposals, and they educate the organization about safe AI usage. Shadow AI shrinks when the safe path is the well-documented, well-supported path.

**Expected outputs:**
- A growing pipeline of prototype submissions
- Increased awareness of approved tools and security boundaries
- Reduced duplication through transparency
- Informal knowledge sharing between submitters and organising team

---

## Phase 2: PROPOSE

**What happens:** Submitters formally submit their prototype for evaluation by opening a Pull Request to the repository following the standardized submission template.

**Duration:** Whenever the submitter is ready. No deadline pressure beyond the quarterly evaluation cutoff.

**Who's involved:**
- *Submitters* -- preparing and submitting their proposals.
- *Organising team* -- validating submissions are complete and well-formed, tagging and categorizing.

**What a submission must include:**

1. **Problem statement** (1-2 paragraphs) -- What real problem does this solve? Not a technology looking for a problem. A problem that exists today, experienced by real people.

2. **Dollar value framing** -- Is this saving money, generating revenue, or reducing risk? A rough estimate is fine. "This saves ~40 hours/week across 12 support agents at $35/hour = ~$87,000/year" is infinitely better than "this improves efficiency."

3. **Working prototype** -- A minimum viable demo. It runs. It does the thing. You can show it to someone and they understand what it does in under two minutes.

4. **Effort so far** -- How much time and resources went into building this? Be honest. "Two weekends and ~20 hours" is a perfectly good answer.

5. **What's needed to graduate** -- Team size, time, and budget to make this production-ready. This forces submitters to think beyond the demo.

6. **Risk assessment** -- Data sensitivity, security implications, integration complexity. What could go wrong if this goes to production?

7. **Demo** -- Link to a video, screenshots, or a live demo. Reviewers need to see it work, not just read about it.

**Why PRs and not a custom app:**
Submissions are Pull Requests to a GitHub repository. Not a form in ServiceNow. Not a Jira ticket. Git is the universal tool engineers already use. PRs give you version control, discussion threads, approval workflows, and an audit trail. Decisions are recorded, challenged, approved or rejected -- all in one place. You don't need a multi-tenant application with user auth and databases to manage this. GitHub already does it.

**What the organising team does:**
- Validates that submissions follow the template (automated via GitHub Actions where possible)
- Applies labels: category (ai-ml, automation, data, ux, infrastructure, process), cycle (Q1-2026, etc.)
- Identifies overlapping or similar submissions and connects those submitters
- Flags incomplete submissions and helps submitters fill gaps

**Expected outputs:**
- Complete, well-formed submission PRs ready for evaluation
- Categorized and labeled pipeline visible to all
- Similar submissions identified and potentially merged
- Submitters prepared to present during evaluation

---

## Phase 3: EVALUATE

**What happens:** A cross-functional review panel scores all submissions from the current cycle using a standardized rubric.

**Duration:** 2-3 weeks per quarterly cycle. Enough time for thorough review, not so much that decisions drag.

**Cadence:** Quarterly. Four cycles per year. Submissions from the rolling window are batched for the next quarterly evaluation.

**Who's involved:**
- *Review panel* (4-5 people, cross-functional):
  - One executive sponsor -- for business alignment and investment authority
  - One technical leader -- for feasibility and architecture assessment
  - One ops/security representative -- for risk evaluation
  - One person from a different department or org -- to break silos and bring outside perspective
- *Organising team* -- facilitating the process, preparing materials, tracking scores
- *Submitters* -- available for questions, presenting demos if requested

**Scoring rubric (each criterion 0-5):**

| Criterion | What it measures |
|---|---|
| **Business Value** | Does this solve a real, significant problem? Is the dollar value framing credible? |
| **Technical Feasibility** | Can this actually be built to production quality? Is the architecture sound? |
| **Resource Efficiency** | Is the ask reasonable relative to the value? Is the effort-to-impact ratio good? |
| **Strategic Alignment** | Does this fit where the organization is heading? Does it support key initiatives? |
| **Innovation Factor** | Is this a new approach? Does it solve the problem in a way nobody else is doing? |

Maximum score: 25 points per reviewer. Scores are averaged across the panel.

**How evaluation works:**
1. Organising team prepares a review package for each submission -- the PR content, demo links, category context
2. Panel members independently score each submission against the rubric
3. Panel convenes to calibrate scores, discuss disagreements, and rank submissions
4. Goal: narrow the field to the top 20 submissions

**What makes a strong submission:**
- Clear problem that the reviewer can immediately relate to
- Credible dollar value estimate (doesn't have to be exact, has to be honest)
- Working demo that actually demonstrates the solution
- Reasonable graduation ask -- not "give me 10 engineers for a year"
- Honest risk assessment -- reviewers trust submitters who acknowledge challenges

**Expected outputs:**
- Scored and ranked list of all submissions
- Written feedback for every submission -- including those not selected
- Top 20 shortlist for the selection phase
- Patterns identified: what problems keep coming up, what categories are trending

---

## Phase 4: SELECT & INVEST

**What happens:** The top submissions are divided into two tiers -- rewarded and invested. Investment means actual allocated time, not a vague promise.

**Duration:** 2-3 months of dedicated build time for invested prototypes.

**Who's involved:**
- *Leadership team* -- approving investment allocation
- *Organising team* -- coordinating, check-ins, removing blockers
- *Submitters and assigned team members* -- building

**Two tiers:**

**Top 5: REWARD**
- Public recognition across the organization
- Tangible reward (the organization decides what -- bonus, time off, conference tickets, whatever is meaningful)
- Fast-track to graduation review -- these go directly into the next evaluation for production readiness
- The reward matters, but the fast-track matters more

**Top 6-15: INVEST**
- 2-3 months of dedicated time with 1-2 engineers assigned (part-time is fine, but it must be *allocated* time, not "work on this when you have bandwidth")
- Regular check-ins with the organising team -- biweekly minimum
- Access to resources: staging environments, test data, design support
- Goal: evolve the prototype toward production-readiness for graduation review

**This is the part most organizations get wrong.** They select winners and then leave them to figure it out on their own alongside their day jobs. That's not investment, that's abandonment with a trophy. Allocated time means it's in the sprint. It's in the OKRs. The manager knows. The team knows.

**Expected outputs:**
- Top 5 recognized and fast-tracked
- Top 6-15 actively building with dedicated resources
- Biweekly progress updates visible in the repository
- Blockers identified and escalated quickly
- Prototypes evolving toward production readiness

---

## Phase 5: GRADUATE

**What happens:** Every invested prototype receives a definitive outcome. No zombie prototypes. No "we'll get back to you." Every path has closure.

**Duration:** Graduation reviews happen at the end of the investment period, typically aligned with the next quarterly cycle.

**Who's involved:**
- *Review panel* -- same cross-functional group from evaluation
- *Leadership team* -- for graduation decisions that require budget and staffing
- *Submitters and build teams* -- presenting progress and readiness

**Four possible outcomes:**

### GRADUATE
The prototype is production-ready (or close enough). Fund it. Staff it. Integrate it into the product roadmap. It's real now.

- Assigned a product owner and engineering team
- Proper production infrastructure provisioned
- Integrated into the organization's development lifecycle
- The submitter is involved in the transition (they built it, they understand it)

### ITERATE
The idea is strong but the prototype needs more work. Not ready for production, but worth continued investment.

- Specific, actionable feedback provided -- not "needs improvement" but "needs to handle X edge case and integrate with Y system"
- Queued for the next cycle with clear success criteria
- May receive continued (reduced) resource allocation
- Submitter knows exactly what "done" looks like for next time

### SHELVE
Valuable idea, wrong timing. Maybe the infrastructure isn't ready. Maybe the priority landscape shifted. Maybe the market isn't there yet.

- Code archived in the repository with full documentation
- Learnings documented -- what worked, what didn't, why it's shelved
- Tagged for future review -- explicitly revisited when conditions change
- Submitter thanked and recognized for the work

### KILL
The experiment ran its course. The idea didn't pan out, or the problem turned out to be smaller than expected, or the technical approach hit a dead end.

- This is not failure. This is learning. The operating model explicitly validates killing prototypes as a positive outcome.
- Code archived, learnings documented
- Thank the team, close the loop cleanly
- What was learned informs future submissions

**Expected outputs:**
- Every invested prototype has a documented outcome
- Graduated prototypes have staffing and roadmap integration
- Iterated prototypes have clear next-cycle criteria
- Shelved prototypes are archived with context for future review
- Killed prototypes have learnings captured
- Zero zombie prototypes

---

## Key Principles

These aren't guidelines. They're the load-bearing walls of the model. Remove any one and the structure collapses.

### 1. Prototypes, Not Ideas
The submission bar is a working prototype. Not a pitch deck. Not a napkin sketch. Not "wouldn't it be cool if." You have to build the thing. This single requirement filters out 80% of noise and ensures every submission represents real effort and real understanding of the problem.

### 2. Prototypes, Not Products
Equally important: submissions should not be fully built, deployed applications. If you've already spent six months and have production users, you don't need this operating model -- you need a product team. The sweet spot is the space between idea and product. That's where this model operates.

### 3. Rolling Submissions, Quarterly Decisions
People submit when they're ready. The organization decides on a cadence. This decouples individual creativity from organizational process. You don't lose ideas because someone wasn't available on hackathon day. You don't rush prototypes to meet an arbitrary deadline.

### 4. GitHub Is the Platform
No custom application. No Jira integration. No ServiceNow tickets. GitHub provides version control, discussion, approval workflows, labels, project boards, actions, and a complete audit trail. Every decision is recorded, challengeable, and visible. If your organization uses Git (and it does), this works on day one.

### 5. Every Submission Gets Closure
Selected or not. Invested or not. Every submission gets written feedback. Every invested prototype gets a definitive outcome -- graduate, iterate, shelve, or kill. No silence. No "we'll circle back." People stop submitting when they feel ignored. They keep submitting when they feel heard.

### 6. Investment Means Allocation, Not Permission
Telling someone "you can work on this" while keeping their sprint load unchanged is not investment. It's a lie. Investment means allocated time in the sprint, in the OKRs, with manager awareness. If the organization isn't willing to do this for 10-15 prototypes per quarter, the model won't work. Scale it to what you can actually commit to.

### 7. Transparency Defeats Duplication
All submissions are visible to everyone. This isn't just about preventing duplicates (though it does that). It's about enabling collaboration. When three people independently identify the same problem, that's a signal. The organising team's job is to spot these patterns and connect people.

### 8. Security Through Structure, Not Restriction
The operating model addresses shadow AI not by blocking tools or lecturing people, but by providing clear documentation on approved tools, security boundaries, and safe prototyping practices. When the official path is well-lit and well-supported, fewer people wander into the shadows.

### 9. The Organising Team Reads the Signals
The submissions themselves are data. What problems keep coming up? What tools are people reaching for? What categories are overrepresented? The organising team doesn't just manage the pipeline -- they read it. The patterns in submissions tell you what your organization actually needs, which is often different from what leadership thinks it needs.

### 10. This Is a System, Not an Event
The operating model runs continuously. Discover never stops. Propose is always open. Evaluate happens quarterly. Select and Invest follow every evaluation. Graduate closes every investment. It's a cycle, not a moment. The value compounds over time as the organization builds muscle memory for channeling prototyping energy into outcomes.

---

## Timeline Overview

| Phase | Cadence | Duration |
|---|---|---|
| DISCOVER | Ongoing | Continuous |
| PROPOSE | Ongoing (cutoff before each quarterly review) | Continuous |
| EVALUATE | Quarterly | 2-3 weeks |
| SELECT & INVEST | Post-evaluation | 2-3 months |
| GRADUATE | End of investment period | 1-2 weeks |

A typical annual cycle:

- **Q1 Evaluation:** Review submissions accumulated since last cycle. Select top 20. Reward top 5. Invest in top 6-15. Investment period runs through Q1-Q2.
- **Q2 Evaluation:** Review new submissions + iterate-track prototypes from Q1. Graduate Q1 investments. New investment round begins.
- **Q3 and Q4:** Same pattern. Each cycle builds on the last.

By the end of year one, you have data: graduation rates, category trends, investment ROI, submitter participation rates. That data makes year two significantly better.

---

## Getting Started

If you've forked this repo, here's the minimum viable setup:

1. **Assemble your organising team.** 2-3 people, cross-functional. They don't need to be full-time on this.
2. **Identify your review panel.** 4-5 people for quarterly evaluations. Get executive sponsorship -- someone who can actually approve resource allocation.
3. **Customize the templates.** Adjust the submission template, rubric weights, and graduation criteria to fit your organization.
4. **Announce it.** Not with a policy memo. With a demo. Show the repo. Show the submission process. Show the example submissions. Make it obvious that this is real and that leadership is behind it.
5. **Open the door.** Start accepting submissions. Don't wait for perfection. The first cycle will be messy. That's fine. You'll learn more from running one cycle than from planning three.

The operating model works because it respects the energy that already exists in your organization. People want to build things. Give them a channel, give them feedback, give them a path to impact -- and get out of the way.
