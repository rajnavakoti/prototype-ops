# Quarterly Review Process

This is how prototypes get evaluated every quarter. The process is designed to be thorough but fast. Prototypes deserve an honest answer, not months of committee deliberation.

---

## Review Panel

### Composition

The panel has 4-5 people. Each person serves a specific function — they're not interchangeable warm bodies.

| Role | Who | Why They're There |
|------|-----|-------------------|
| **Business Sponsor** | A director or VP-level leader from the business side | Judges whether the problem is real and the value framing is honest. Can they see this in a budget conversation? |
| **Technical Lead** | A senior engineer or architect | Judges whether the prototype actually works, whether the architecture is sound, and whether the "what's needed to graduate" estimate is realistic or fantasy. |
| **Risk Assessor** | Someone from security, compliance, or operations | Catches what builders overlook: data privacy issues, security gaps, operational complexity, regulatory risk. The person who asks "what happens when this breaks at 3am?" |
| **Cross-Functional Voice** | Someone from a different department than most submissions | Breaks echo chambers. Asks "would this work in my part of the org?" Catches assumptions that only make sense in one silo. |
| **Organising Team Rep** (optional 5th) | A member of the team running the prototyping program | Provides context on submission history, similar past prototypes, and process continuity. Does not score — facilitates. |

### Panel Rules

- **Term limits:** Panel members serve 2-3 cycles, then rotate. Fresh eyes matter more than institutional memory.
- **No repeat dominance:** The same person cannot serve as Business Sponsor for consecutive cycles.
- **Conflict of interest:** If your submission (or your direct report's) is being reviewed, you leave the room for that evaluation. You can answer factual questions if asked, but you don't score, advocate, or participate in the decision.
- **Attendance is mandatory.** If a panel member can't attend, they're replaced for that cycle — not "we'll catch them up later." Absent reviewers don't submit scores after the fact.

---

## Timeline

The quarterly review runs on a fixed 4-week cadence. Dates are published at the start of each cycle so submitters know the deadline.

### Week 1: Submission Cutoff and Prep

| Day | Activity |
|-----|----------|
| **Day 1** | Submission window closes. No new submissions accepted for this cycle (they roll to next cycle). |
| **Day 1-2** | Organising team compiles the submission list. Checks every submission for completeness against the template. Incomplete submissions get 48 hours to fix gaps, or they roll to next cycle. |
| **Day 3-5** | Organising team runs the grouping skill to identify overlapping or duplicate submissions. Submitters of overlapping prototypes are connected and encouraged (not forced) to combine. |
| **Day 5** | Final submission list published. Panel members receive all materials. |

### Week 2: Independent Scoring

| Day | Activity |
|-----|----------|
| **Day 6-10** | Each panel member reviews every submission independently. No group discussions yet. |
| | For each submission, each reviewer fills out the evaluation template: five rubric scores with one-sentence justifications per score, overall recommendation (advance/reject), and any flags (security concern, overlap with existing product, etc.). |
| **Day 10** | All scores due. No extensions. If a reviewer hasn't submitted scores, the organising team follows up same-day. |

### Week 3: Calibration and Selection

| Day | Activity |
|-----|----------|
| **Day 11** | **Score compilation.** Organising team aggregates scores, calculates averages, identifies high-variance submissions (where reviewers disagree significantly). |
| **Day 12-13** | **Calibration session** (2-3 hours, one meeting). Panel reviews scores together. Focus on: |
| | - High-variance submissions: why did reviewers disagree? Discuss, re-score if needed. |
| | - Borderline submissions (near the Top 15 cutoff): discuss in detail, final vote. |
| | - Clear winners (20+) and clear rejections (below 10): confirm quickly, don't over-discuss. |
| **Day 14** | **Final rankings published internally to panel.** Top 5 and Top 15 identified. |
| **Day 15** | **Sanity check.** Panel reviews the full list one more time. Does the overall selection make sense as a portfolio? Too many similar prototypes selected? Key categories missing? Adjust if needed (swap borderline submissions, not rewrite scores). |

### Week 4: Communication

| Day | Activity |
|-----|----------|
| **Day 16-17** | **Winners notified first.** Top 5 and Top 15 submitters told their outcome privately before any public announcement. They get their scores and reviewer comments. |
| **Day 17-18** | **Non-selected submitters notified.** Every non-selected submitter receives their scores, reviewer feedback, and specific suggestions for improvement. This is not a form letter — it references their actual submission. |
| **Day 19** | **Public announcement.** Selected prototypes announced to the organization. Demo day scheduled for the following week. |
| **Day 20** | **Investment planning begins.** Top 15 prototypes are matched with dedicated resources. Timelines and check-in schedules set. |

---

## Decision-Making Process

### How Decisions Get Made

1. **Scores do the initial sorting.** The rubric exists so that the first pass is systematic, not political. Trust the scores.

2. **Discussion handles the edges.** The calibration session exists for borderline cases and disagreements. Most submissions will be clearly in or clearly out. Spend time on the 20% that are ambiguous.

3. **Majority rules for final calls.** After discussion, if the panel can't reach consensus on a borderline submission, it goes to a vote. Simple majority. The Business Sponsor does not get a veto or extra weight.

4. **Portfolio thinking is allowed.** The panel can consider the overall mix of selected prototypes. If 8 of the top 15 are all AI chatbots, the panel can swap one borderline chatbot for a borderline submission in an underrepresented category. But this is a rare adjustment, not a license to ignore scores.

### What Is NOT Allowed

- **Overruling scores without discussion.** A senior leader cannot walk in and say "add this one" or "drop that one" without going through the calibration process.
- **Scoring after seeing other scores.** Independent scoring means independent. If a reviewer's scores suspiciously shift after seeing the aggregate, the organising team flags it.
- **Punishing resubmissions.** A prototype that was rejected last cycle and resubmitted with improvements is scored on its current merit. "We already said no to this" is not a valid argument.
- **Rewarding seniority.** The VP's prototype competes on the same rubric as the junior developer's. If the VP's prototype scores lower, it ranks lower.

---

## Conflict Resolution

Disagreements will happen. Here's how to handle them.

### Score Disagreement (High Variance)

When reviewers are more than 2 points apart on a single criterion:

1. Both reviewers explain their reasoning to the panel
2. Other panel members ask clarifying questions
3. The two reviewers can adjust their scores if convinced, or hold firm
4. If still more than 2 points apart, the other panel members' scores determine the average (the outliers are included but diluted)

### Process Disagreement

When someone thinks the process itself is wrong (e.g., "this criterion doesn't apply to this type of prototype"):

1. Note the concern
2. Complete the current cycle using the existing process
3. Add it to the retrospective for process improvement next cycle
4. Do not change rules mid-evaluation. That way lies chaos.

### External Pressure

When someone outside the panel tries to influence outcomes:

1. The organising team rep handles this. Panel members should not engage directly.
2. Response is always the same: "The panel scores independently using the published rubric. Results will be shared on [date]."
3. If the pressure is from someone with budget authority over the program, escalate to the executive sponsor of the prototyping program. This is a governance issue, not a scoring issue.

### Recusal Disputes

When it's unclear whether a panel member has a conflict of interest:

1. When in doubt, recuse. The bar is low intentionally.
2. If a panel member doesn't think they need to recuse but others disagree, majority of the remaining panel decides.
3. A recused member's score is simply excluded from the average. It doesn't reduce the submission's chances.

---

## After the Review

### What Submitters Receive

**Every submitter**, regardless of outcome, receives:

- Their five criterion scores (averaged across reviewers)
- A written summary of reviewer feedback (2-3 sentences minimum, referencing their specific submission)
- The overall threshold for selection that cycle (so they can see where they stood)
- For non-selected submissions: specific, actionable suggestions for what would make this stronger next cycle

### What the Organization Receives

- A cycle summary: how many submissions, category breakdown, selection results
- Demo day for selected prototypes (scheduled within 1 week of announcement)
- Updated dashboard showing the pipeline status
- Retrospective notes on what worked and what to improve in the review process

### Retrospective

Within 1 week of completing the review, the panel and organising team hold a 30-minute retrospective:

- What worked well in this review cycle?
- What was confusing or took too long?
- Were there submissions the rubric didn't handle well?
- Any criteria that need adjustment for next cycle?
- Panel composition: who should rotate in or out?

Changes to the process are made between cycles, never during one. Update this document when changes are agreed.
