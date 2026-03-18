# Prototype Submission

> **Submission Title:** AI-Powered Inventory Alert System
> **Submitter:** Alex Chen / @achen
> **Date:** 2026-02-14
> **Category:** ai-ml

---

## Problem Statement

Our regional warehouse network (12 locations) relies on manual stock checks and static reorder thresholds to manage inventory across 8,400 SKUs. Warehouse coordinators spend 2-3 hours daily reviewing spreadsheets and ERP dashboards to identify items approaching stockout or accumulating excess. Despite this effort, we averaged 340 stockout events per quarter last year, each taking 3-5 days to resolve through emergency reorders at premium freight costs. On the other side, slow-moving overstock tied up an estimated $2.1M in dead inventory across all locations.

The core issue is that static thresholds cannot account for seasonal demand shifts, promotional spikes, or regional variation. A coordinator in Portland sets the same reorder point year-round for sunscreen that a coordinator in Miami does, despite fundamentally different demand curves. By the time a human notices the pattern, the damage — lost sales or wasted capital — is already done.

---

## Dollar Value Framing

- **Value type:** Cost saving
- **Estimate:** $680,000/year
  - Stockout reduction: 340 events/quarter x 60% reduction x $320 avg emergency freight premium = $261,120/year
  - Overstock reduction: $2.1M dead inventory x 35% reduction x 18% annual carrying cost = $132,300/year
  - Labor savings: 12 coordinators x 1.5 hrs/day saved x 250 working days x $48/hr avg = $216,000/year
  - Waste reduction (perishables): ~$70,000/year based on current spoilage rates reduced by 40%
- **Assumptions:**
  - 60% stockout reduction is conservative; academic benchmarks for ML-based demand forecasting show 30-70% improvement over static methods
  - Carrying cost of 18% is standard for warehoused goods (storage, insurance, depreciation, opportunity cost)
  - Coordinators will reallocate saved time to exception handling and supplier negotiations, not be eliminated
  - Model accuracy improves with 6+ months of feedback data
- **Confidence level:** Medium

---

## Working Prototype

- **Link:** [github.com/achen/inventory-alert](https://github.com/achen/inventory-alert)
- **Tech stack:** Python 3.11, scikit-learn (Random Forest + Gradient Boosting), pandas, PostgreSQL, Slack SDK, Streamlit (dashboard), Docker
- **How to run it:**
  1. Clone the repo and run `docker compose up` to start PostgreSQL and the app
  2. Load sample data: `python scripts/seed_data.py --source sample_data/`
  3. Train model: `python train.py --lookback 90 --horizon 14`
  4. Start alert service: `python alert_service.py` (sends to configured Slack channel)
  5. View dashboard at `http://localhost:8501`

---

## Effort So Far

- **Time invested:** ~60 hours over 5 weekends
- **People involved:** Alex Chen (ML engineering), Dana Torres (warehouse ops, provided domain expertise and test data)
- **Resources used:** Personal laptop, anonymized 18-month sales history export (approved by data team), free-tier Slack workspace for testing
- **What was hardest:** Getting the demand signal right for promotional periods — the model initially treated promo spikes as anomalies rather than predictable patterns, which required adding a promotional calendar feature.

---

## What's Needed to Graduate

- **Team size:** 2 engineers (1 ML, 1 backend) + 1 warehouse ops lead for 3 months, then 0.5 FTE ongoing maintenance
- **Timeline:** 12-14 weeks to production pilot at 2 locations, 6 months for full rollout
- **Budget:** ~$85,000 (engineering time: $60K, infrastructure: $15K/year for compute and monitoring, Slack Enterprise integration: $10K)
- **Dependencies:**
  - Read access to live ERP inventory and sales data (SAP RFC or API gateway)
  - Slack Enterprise Grid approval for bot integration
  - Warehouse ops team buy-in for a 4-week parallel-run validation period
  - Data engineering team to set up a nightly ETL pipeline
- **Key risks to graduation:**
  - ERP API access may require a 6-8 week procurement and security review cycle
  - Model retraining pipeline needs MLOps infrastructure we do not currently have
  - If coordinators do not trust the alerts, adoption will stall regardless of accuracy

---

## Risk Assessment

- **Data sensitivity:** Uses historical sales volumes and SKU metadata. No customer PII. Data was anonymized for prototyping; production would use internal data behind existing access controls.
- **Security implications:** Slack bot requires write access to specific channels only. No external data egress. Model runs on internal infrastructure.
- **Integration complexity:** Medium. Requires read-only connection to SAP and write access to Slack. No modifications to source systems. Dashboard is standalone.
- **Compliance concerns:** None identified. No customer data, no regulated data categories. Standard internal tooling approval process applies.

---

## Demo

- **Video walkthrough:** [drive.google.com/file/d/inventory-alert-demo](https://drive.google.com/file/d/inventory-alert-demo)
- **Screenshots:** [github.com/achen/inventory-alert/docs/screenshots](https://github.com/achen/inventory-alert/tree/main/docs/screenshots)
- **Live demo:** Available on request (requires VPN access to demo environment)

---

## Additional Context

The prototype was tested against 18 months of historical data from 3 warehouse locations. Backtesting showed the model would have flagged 78% of actual stockout events with a 5-day lead time, compared to the current process which catches roughly 30% before they become critical. False positive rate was 12%, which is within the acceptable range for actionable alerts (coordinators indicated they would rather investigate a false alert than miss a real one). Dana Torres from warehouse ops has agreed to champion a pilot if this moves forward.
