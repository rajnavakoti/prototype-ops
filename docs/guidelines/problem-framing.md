# Problem Framing

How to think about the problem your prototype solves — in terms that justify investment.

---

## Why Dollar Values Matter

"It saves time" is not a business case. "It saves 4,200 hours per year across the support team, worth $210,000 in labor cost" is a business case. The review panel scores on business value. Give them numbers they can evaluate, not feelings they have to guess at.

You do not need exact figures. You need defensible estimates with stated assumptions. A rough number beats no number every time.

---

## The Core Formula

```
Annual Value = Hours Saved per Week x Number of People Affected x Weeks per Year x Hourly Cost
```

This is the baseline. It works for the majority of prototypes because most prototypes save time doing something that humans currently do manually.

**Hourly cost rule of thumb**: If you do not know the loaded cost (salary + benefits + overhead), use 1.5x the base hourly rate. For a knowledge worker making $80,000/year, that is roughly $60/hour loaded.

---

## Three Value Frameworks

Not every prototype saves time directly. Use whichever framework fits your situation. If multiple apply, pick the strongest one and mention the others.

### Framework 1: Time Savings (Most Common)

Use when your prototype automates, accelerates, or eliminates manual work.

**Formula**: `hours_saved_per_week x people x 50 weeks x hourly_cost`

**What counts as time saved**:
- Tasks eliminated entirely
- Tasks reduced from X minutes to Y minutes
- Rework avoided (fewer errors means fewer corrections)
- Meetings shortened or removed
- Waiting time eliminated (approvals, handoffs, searches)

**What does NOT count**:
- "People could use the time for higher-value work" — that is speculative. Stick to the hours freed up.
- Time saved in theory that nobody actually experiences. If you automate a 5-minute task done once a month, that is not material.

### Framework 2: Revenue Impact

Use when your prototype directly affects top-line revenue — faster sales cycles, better conversion, reduced churn, new capabilities that unlock revenue.

**Formula**: `revenue_at_risk x improvement_percentage` or `new_revenue_enabled x probability_of_capture`

**Be honest about attribution**: If your prototype improves one step in a 20-step sales process, you cannot claim credit for the entire deal. Estimate your contribution to the outcome.

### Framework 3: Risk Reduction

Use when your prototype reduces the probability or cost of bad outcomes — compliance failures, security incidents, outages, data loss, regulatory fines.

**Formula**: `probability_of_incident x cost_of_incident x reduction_factor`

**Risk is harder to quantify** but often has the highest dollar values. A single data breach costs millions. A compliance fine can be existential. If your prototype moves the needle on risk, frame it clearly.

---

## Worked Example 1: Support Ticket Classification

**Problem**: Customer support agents manually read and categorize every incoming ticket. This takes 3-5 minutes per ticket. The team handles 200 tickets per day across 15 agents.

**Calculation**:
- Time per ticket currently: 4 minutes (average)
- Time with prototype: 30 seconds (agent reviews AI classification, confirms or corrects)
- Time saved per ticket: 3.5 minutes
- Tickets per day: 200
- Daily time saved: 200 x 3.5 min = 700 minutes = 11.7 hours/day
- Weekly time saved: 58.3 hours
- Annual time saved: 58.3 x 50 = 2,915 hours
- Hourly cost (loaded): $45/hour (support team rate)
- **Annual value: $131,175**

**Stated assumptions**:
- Average ticket classification time based on sampling 50 tickets across 3 agents
- 30-second review time based on prototype testing with 2 agents over 1 week
- AI accuracy is 87%, meaning ~13% of tickets need manual reclassification (already factored into the 30-second average)

This is a strong submission. The assumptions are stated, the numbers are grounded in observation, and the reviewer can challenge any specific assumption without throwing out the whole case.

## Worked Example 2: Meeting Action Item Extraction

**Problem**: After every meeting, someone (usually a junior team member) writes up action items and decisions from notes or recordings. This takes 15-30 minutes per meeting. The organization runs ~60 meetings per week that require documented outcomes.

**Calculation**:
- Time per meeting for write-up: 20 minutes (average)
- Time with prototype: 3 minutes (review AI-generated summary, edit, send)
- Time saved per meeting: 17 minutes
- Meetings per week: 60
- Weekly time saved: 60 x 17 min = 1,020 minutes = 17 hours/week
- Annual time saved: 17 x 50 = 850 hours
- Hourly cost (loaded): $55/hour (average across roles doing this work)
- **Annual value: $46,750**

**Secondary value (risk reduction)**:
- 30% of action items are currently lost or forgotten because write-ups are late or incomplete
- Average cost of a missed action item: impossible to quantify precisely, but two incidents in the last quarter resulted in project delays costing an estimated $15,000 each
- If the prototype reduces missed action items by half: $15,000 x 2 incidents/quarter x 4 quarters x 0.5 = **$60,000 in avoided project delays**

**Combined annual value: ~$107,000**

---

## Common Mistakes

**Inflating the numbers**: Do not assume 100% adoption, 100% accuracy, or 100% time savings. Build in realistic adoption rates (start with 60-70%) and error rates. Reviewers will catch inflated numbers and it undermines your credibility on everything else.

**Counting the wrong baseline**: Compare against what people actually do today, not what the process documentation says they should do. If the official process takes 10 steps but everyone skips 4 of them, your baseline is 6 steps.

**Ignoring the cost of change**: Your prototype saves 2,000 hours a year, but graduating it requires 6 months of engineering time. That is a cost. Acknowledge it. The review panel will factor it in regardless — better that you show you have thought about it.

**Double-counting**: If three prototypes all claim to save the same team's time, those savings overlap. Frame your value in terms of your specific contribution.

---

## Quick Reference

| Value Type | Formula | Example |
|---|---|---|
| Time savings | hours/week x people x 50 x hourly rate | 5 hrs x 20 people x 50 x $50 = $250,000 |
| Revenue impact | revenue at risk x improvement % | $2M pipeline x 5% faster close = $100K |
| Risk reduction | probability x cost x reduction | 10% chance x $500K x 50% reduction = $25K |

---

## Final Note

Your estimate does not need to be perfect. It needs to be honest, grounded in observable data, and clear about its assumptions. The review panel would rather see "$50,000 with these 3 assumptions" than "$2 million because AI."
