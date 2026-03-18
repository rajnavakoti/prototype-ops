# Prototype Submission

> **Submission Title:** Customer Feedback Classifier
> **Submitter:** Marcus Johnson / @mjohnson
> **Date:** 2026-01-27
> **Category:** ai-ml

---

## Problem Statement

Our customer support operation handles approximately 540 tickets per day across email, chat, and web forms. Every ticket enters a single general queue and is manually triaged by a 3-person routing team who read each one, assign a category, set a priority, and route it to the correct specialist group (billing, technical, product, shipping, account management). This manual triage process takes an average of 4.2 minutes per ticket and introduces a median 47-minute delay before a ticket reaches the right team.

The cost is not just the routing team's time — it is what happens downstream. Urgent issues (service outages, security concerns, order cancellations within the refund window) sit in the general queue alongside password resets and feature requests. Last quarter, 23% of tickets were routed to the wrong team on the first attempt, requiring re-routing and adding an average of 2.3 hours to resolution time. Our CSAT scores for mis-routed tickets are 18 points lower than correctly routed ones. Customers do not care about our internal queue structure; they care that their urgent problem sat unread for an hour because it was categorized as "general inquiry."

---

## Dollar Value Framing

- **Value type:** Cost saving
- **Estimate:** $534,000/year
  - Triage team labor: 3 FTEs x $58,000 avg salary x 1.35 benefits multiplier = $234,900/year (estimate 80% of this work automated, retaining 1 FTE for edge cases = $156,600 saved)
  - Mis-routing rework: 540 tickets/day x 23% mis-routed x 2.3 hrs added resolution x $42/hr agent cost x 365 days = $1.15M, reduced by 70% = $189,800 saved (conservative; model accuracy exceeds human accuracy in testing)
  - Faster urgent response: reducing median time-to-right-team from 47 min to ~3 min for critical tickets prevents estimated 8 escalations/month at $1,200 avg escalation cost + goodwill impact = $115,200/year
  - CSAT improvement: not directly quantified but correlated with 12-15% reduction in churn for affected customer segment based on industry benchmarks
  - Reduced agent context-switching from receiving wrongly-routed tickets: estimated $72,400/year
- **Assumptions:**
  - 540 tickets/day is a trailing 6-month average; volume has been growing ~8% quarterly
  - 70% mis-routing reduction is based on prototype testing (model achieved 91% routing accuracy vs. human 77%)
  - One triage FTE retained for escalations, ambiguous tickets, and model feedback
  - Agent cost of $42/hr is loaded cost for L1/L2 support staff
- **Confidence level:** High

---

## Working Prototype

- **Link:** [github.com/mjohnson/feedback-classifier](https://github.com/mjohnson/feedback-classifier)
- **Tech stack:** Python 3.11, Claude API (Haiku for classification, Sonnet for ambiguous cases), FastAPI, PostgreSQL, Redis (job queue), pandas for analytics, pytest
- **How to run it:**
  1. Clone the repo: `git clone https://github.com/mjohnson/feedback-classifier.git`
  2. Copy `.env.example` to `.env` and set `ANTHROPIC_API_KEY` and `DATABASE_URL`
  3. Start services: `docker compose up -d`
  4. Seed with sample tickets: `python scripts/load_samples.py --count 500`
  5. Run classifier: `python classify.py --mode batch` (or `--mode api` for real-time endpoint)
  6. View results dashboard: `http://localhost:8000/dashboard`

---

## Effort So Far

- **Time invested:** ~80 hours over 6 weeks
- **People involved:** Marcus Johnson (development), Lisa Park (support ops manager, provided labeled training data and validated outputs), Raj Patel (infosec, reviewed data handling approach)
- **Resources used:** Anthropic API (total spend: ~$47 during development and testing), anonymized export of 12,000 historical tickets with human-assigned categories (approved by support ops and legal), personal Docker environment
- **What was hardest:** Building a reliable urgency detector — the difference between "my service is down" (critical) and "my service was down yesterday" (informational) requires genuine language understanding, not just keyword matching.

---

## What's Needed to Graduate

- **Team size:** 2 engineers (1 backend, 1 integration) + 1 support ops liaison for 10 weeks, then 0.5 FTE ongoing
- **Timeline:** 10 weeks to production pilot (shadow mode alongside human triage for 3 weeks, then gradual handoff), 16 weeks to full production
- **Budget:** ~$94,000 (engineering time: $62K, API costs at production volume: $18K/year using Haiku for 95% of tickets with Sonnet escalation, infrastructure and monitoring: $14K/year)
- **Dependencies:**
  - API integration with Zendesk (our current ticketing system) for real-time ticket ingestion and routing
  - Anthropic enterprise API agreement with data processing addendum
  - Support ops team agreement on category taxonomy (current categories need cleanup; 4 of 18 categories overlap)
  - 3-week shadow mode period where the model classifies but humans still route (for validation)
- **Key risks to graduation:**
  - Zendesk API rate limits may require a webhook-based architecture instead of polling, adding complexity
  - Category taxonomy cleanup is a prerequisite that requires cross-team agreement (historically contentious)
  - If the model misroutes an urgent ticket during pilot and a customer escalates, leadership may lose confidence regardless of overall accuracy improvement

---

## Risk Assessment

- **Data sensitivity:** Moderate. Support tickets contain customer names, email addresses, and account identifiers. Some tickets include partial payment information (last 4 digits) or personal details shared in free-text descriptions. Production system must comply with existing customer data handling policies.
- **Security implications:** Tickets are sent to Anthropic's API for classification. Enterprise API agreement required to ensure no data retention by the provider. Alternative: fine-tuned open-source model running on-premises (tested with Llama 3 — accuracy was 83% vs. 91% with Claude, but eliminates external data transmission).
- **Integration complexity:** Medium. Zendesk has a mature API and webhook system. The classifier sits between ticket creation and queue assignment — it does not modify tickets, only adds metadata (category, priority, confidence score) and triggers routing rules. Rollback is straightforward: disable the webhook and revert to manual triage.
- **Compliance concerns:** Customer data processing must align with existing privacy policy and data processing agreements. Tickets from EU customers fall under GDPR; the system must respect data residency requirements. Audit logging of all classification decisions is built into the prototype and required for production.

---

## Demo

- **Video walkthrough:** [drive.google.com/file/d/feedback-classifier-demo](https://drive.google.com/file/d/feedback-classifier-demo)
- **Screenshots:** [github.com/mjohnson/feedback-classifier/docs/screenshots](https://github.com/mjohnson/feedback-classifier/tree/main/docs/screenshots)
- **Live demo:** [classifier-demo.internal.company.com](https://classifier-demo.internal.company.com) (internal network, pre-loaded with anonymized sample data)

---

## Additional Context

The prototype was validated against 2,000 held-out tickets that were previously classified by the human triage team. Results:

| Metric | Human Triage | Classifier |
|--------|-------------|------------|
| Category accuracy | 77% | 91% |
| Priority accuracy | 71% | 88% |
| Avg time to classify | 4.2 min | 1.8 sec |
| Urgent ticket detection | 82% | 96% |

The model uses a two-tier approach: Claude Haiku handles straightforward tickets (approximately 85% of volume) with high confidence. Tickets where Haiku's confidence falls below 0.85 are escalated to Claude Sonnet for deeper analysis. This keeps API costs manageable while maintaining accuracy on edge cases. The 9% of tickets where even Sonnet's confidence is below 0.80 are flagged for human review — these are genuinely ambiguous tickets that humans also struggle with.

Lisa Park's support ops team has reviewed 500 of the model's classifications in detail and confirmed they would accept the routing decision in 93% of cases. The team has expressed strong interest in piloting this, as the triage role is widely regarded as the least desirable rotation in the support organization.
