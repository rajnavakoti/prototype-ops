# Scoring Rubric

This is how prototypes get scored. Five criteria, each 0-5. No gut feelings, no politics, no "I just like this one." Every score has a reason. Every reason maps to evidence in the submission.

---

## How Scoring Works

- Each reviewer scores independently before discussion
- Scores are integers: 0, 1, 2, 3, 4, or 5. No half-points.
- 0 means "not addressed at all" — the submission doesn't even attempt this dimension
- Final score per criterion = average across all panel members, rounded to one decimal
- Total score = sum of all five criteria (max 25)
- Reviewers MUST write a one-sentence justification for each score. A number without reasoning is worthless.

---

## Criteria

### 1. Business Value (0-5)

**What it measures:** Does this prototype solve a real problem that costs the organization real money, time, or risk? Not "would be nice" — actually painful today.

| Score | What it looks like |
|-------|-------------------|
| **1** | Solves a problem nobody actually has, or solves a real problem in a way that saves negligible time. "I automated something that takes 2 minutes once a month." No quantified impact. |
| **3** | Solves a genuine pain point with reasonable scale. The submitter can articulate who benefits and roughly how much. "This saves our 12-person support team about 3 hours per person per week on ticket triage." Numbers are plausible even if estimates are rough. |
| **5** | Addresses a well-documented, high-impact problem. Clear dollar framing with defensible math. "Customer churn analysis currently takes 2 analysts 3 weeks per quarter. This does it in 2 hours. At loaded cost, that's $180K/year in recovered capacity." Multiple teams or business units would benefit. |

**Red flags that cap this at 2:** No problem statement at all. "I thought it would be cool." Solution looking for a problem. Only benefits the submitter personally.

---

### 2. Technical Feasibility (0-5)

**What it measures:** Can this actually be built to production quality with reasonable effort? Is the prototype evidence that the hard parts are solved, or is it duct tape and demo magic?

| Score | What it looks like |
|-------|-------------------|
| **1** | The prototype is a mockup or slideware. Key technical challenges are hand-waved ("we'll figure out the data pipeline later"). Depends on technology the org doesn't have and can't easily acquire. No consideration of scale, latency, or reliability. |
| **3** | Working prototype that demonstrates the core functionality. The hard technical problem is visibly solved, even if rough. Submitter acknowledges remaining gaps honestly. "Auth and multi-tenancy aren't built yet, but the classification engine works on real data." Uses technology the org already has or can reasonably adopt. |
| **5** | Prototype is surprisingly close to production-ready. Handles edge cases. Tested on realistic data volumes. Architecture is sound — not just a script that works on the submitter's laptop. Clear, honest assessment of what's left to build, with realistic estimates. Security and data concerns are addressed, not ignored. |

**Red flags that cap this at 2:** "Works on my machine" with no path to deployment. Relies on API keys to services the org hasn't approved. Ignores data privacy entirely. Demo only works on the happy path.

---

### 3. Resource Efficiency (0-5)

**What it measures:** How much bang for the buck? What's the ratio of investment needed to value delivered? A brilliant prototype that needs 20 engineers for 18 months is a different proposition than one that needs 2 engineers for 6 weeks.

| Score | What it looks like |
|-------|-------------------|
| **1** | Massive investment required relative to impact. "We need a dedicated team of 8 for a year to save one department 5 hours a week." Or: the prototype itself took enormous effort, suggesting the full build will be even harder. No consideration of alternatives — there might be an off-the-shelf tool that does this. |
| **3** | Reasonable investment for meaningful return. "2 engineers, 2-3 months, part-time. ROI positive within 6 months." The submitter has thought about build vs. buy. Effort estimate is honest and detailed, not wishful thinking. Maintenance burden is acknowledged. |
| **5** | Exceptional leverage. Small team, short timeline, high impact. "One engineer, 4 weeks full-time. Already 80% built. Saves 200+ hours per month across the org." Uses existing infrastructure. Low ongoing maintenance. The prototype itself was built efficiently — that's evidence the team can ship. |

**Red flags that cap this at 2:** No effort estimate at all. "We just need resources" without specifics. Requires hiring specialists the org doesn't have. Ongoing costs are hand-waved.

---

### 4. Strategic Alignment (0-5)

**What it measures:** Does this push the organization in a direction it actually wants to go? Does it align with stated priorities, or is it a pet project dressed up in strategy language?

| Score | What it looks like |
|-------|-------------------|
| **1** | No connection to organizational priorities. Solves a problem in a domain the org is actively exiting. Contradicts current strategic direction. Or worse: the submitter claims alignment but can't explain how when asked. |
| **3** | Connects to a real organizational priority. The link is genuine, not forced. "Our department's OKR is reducing manual data processing by 40% — this prototype automates the biggest manual process we have." Reasonable people would agree this fits. |
| **5** | Directly advances a top-level strategic initiative. Multiple leadership stakeholders would immediately see the relevance. "The CEO said in the last all-hands that customer response time is our #1 priority. This cuts first-response time from 4 hours to 12 minutes, with data to prove it." Creates capabilities the org will need regardless of which specific strategy wins. |

**Red flags that cap this at 2:** Strategy name-dropping without substance. "This supports our digital transformation" with no specifics. Solves yesterday's strategic priority, not today's.

---

### 5. Innovation Factor (0-5)

**What it measures:** Is this a genuinely new approach, or is it something the org could buy off the shelf? Innovation doesn't mean "uses AI" — it means the prototype brings a novel perspective or solution to the problem.

| Score | What it looks like |
|-------|-------------------|
| **1** | This is a known solution that already exists commercially. "I built a chatbot" — okay, so did every SaaS vendor. No unique insight about the problem domain. The prototype doesn't leverage any organizational knowledge or data advantage. |
| **3** | Takes an existing concept but applies it in a genuinely useful way specific to the org. "Yes, sentiment analysis exists, but we trained it on our specific product taxonomy and customer language, and it catches issues our vendor tool misses." Combines existing tools in a novel way. Shows creative problem-solving. |
| **5** | Genuinely new approach that makes people say "why didn't we think of this before?" Leverages unique organizational data or domain knowledge that no vendor could replicate. "We connected our supply chain data with weather patterns and social media trends to predict regional demand shifts 3 weeks earlier than our current model." Creates intellectual property or competitive advantage. |

**Red flags that cap this at 2:** "I just connected two APIs." Reimplementation of a well-known tutorial. No domain-specific insight.

---

## Score Calculation

```
Total Score = Business Value + Technical Feasibility + Resource Efficiency + Strategic Alignment + Innovation Factor

Maximum possible: 25
```

### Selection Thresholds

These thresholds guide the panel. They are starting points for discussion, not hard cutoffs. Context matters — a cycle with 50 submissions is different from one with 12.

| Tier | Score Range | Outcome |
|------|-------------|---------|
| **Top 5 (Reward)** | Typically 20-25 | Recognition, fast-track to graduation review. These are clearly strong. |
| **Top 15 (Invest)** | Typically 15-19 | Allocated time and resources for 2-3 months of dedicated development. |
| **Not Selected** | Below 15 | Feedback provided. Encouraged to resubmit in a future cycle with specific improvements noted. |

### Tie-Breaking

When submissions have the same total score:

1. Higher Business Value score wins (we bias toward impact)
2. If still tied: higher Resource Efficiency score wins (we bias toward leverage)
3. If still tied: the panel discusses and votes. Majority rules.

### Conflict of Interest

If a panel member submitted a prototype, or their direct report did, they recuse from scoring that submission. They can answer factual questions about it but do not score or advocate.

---

## What Good Scoring Looks Like

A good evaluation reads like this:

> **Business Value: 4** — Solves ticket routing, which the support team has flagged as their #1 pain point in the last two engagement surveys. Estimated 15 hours/week saved across the team. Would score 5 if the dollar framing were more rigorous.

Not like this:

> **Business Value: 4** — Seems useful.

If your justification is less than one sentence, your score is not ready for the panel.
