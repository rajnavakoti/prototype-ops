# Org-Level Problems Worth Solving

These are real categories of problems that exist in most enterprises. They are not hypothetical. If you work in a large organization, you have at least five of these right now.

Use this list as inspiration. The best submissions come from people who felt the pain firsthand and built something to fix it.

---

## AI / Machine Learning

### 1. Customer Support Ticket Classification
Support teams manually read and route thousands of tickets per week. An ML classifier that auto-categorizes by intent, urgency, and department could reclaim 15-20 hours/week of human triage time. At scale, that is $150K-$300K/year in labor costs alone, plus faster resolution times.

### 2. Demand Forecasting for Inventory
Stockouts cost revenue. Overstocking ties up capital. Historical sales data combined with external signals (weather, events, trends) can predict demand more accurately than spreadsheet-based planning. A 5% improvement in forecast accuracy can translate to $1M+ annually in reduced waste and lost sales for a mid-size retailer.

### 3. Internal Document Search and Retrieval
Employees spend an average of 1.8 hours per day searching for information across wikis, SharePoint, Confluence, Slack, and email. A semantic search layer over internal knowledge bases could recover 20-30 minutes per person per day. Multiply by headcount and hourly cost -- this is one of the largest hidden costs in any enterprise.

---

## Automation

### 4. Invoice Processing and Matching
Finance teams manually match purchase orders to invoices to delivery receipts. An automated three-way matching system reduces processing time from 15 minutes to under 1 minute per invoice. Organizations processing 10,000+ invoices/month can save $500K-$1M/year in AP labor and late-payment penalties.

### 5. Employee Onboarding Workflow
New hire onboarding involves 10+ systems (IT provisioning, badge access, benefits enrollment, training assignments, team introductions). Most of this is manual coordination via email and spreadsheets. Automating the orchestration layer saves 3-5 hours per new hire and reduces the "productive on day one" timeline from weeks to days.

### 6. Meeting Action Item Extraction
The average enterprise employee attends 15+ hours of meetings per week. Action items get lost in notes or forgotten entirely. An automated system that extracts decisions and action items from meeting transcripts and pushes them to task management tools could recover 2-3 hours/week per manager. Across a 500-person org, that is roughly $2M/year in recovered productivity.

---

## Data and Analytics

### 7. Data Quality Monitoring
Bad data costs the average enterprise $12.9M per year (Gartner). Most organizations discover data quality issues when a report looks wrong or a downstream system breaks. Automated data quality monitoring that checks for schema drift, missing values, outlier spikes, and freshness issues catches problems at ingestion -- not at the dashboard.

### 8. Self-Service Reporting for Non-Technical Teams
Business teams submit 50-100 ad hoc data requests per month to analytics teams. Average turnaround: 3-5 business days. A natural language query interface over structured data lets business users answer their own questions in minutes. This frees analytics teams for strategic work and eliminates the reporting bottleneck.

---

## User Experience

### 9. Internal Tool Consolidation
Most enterprises have 5-10 internal tools that employees use daily, each with its own login, UI, and mental model. A unified interface layer (even a simple portal or command palette) that aggregates the most common actions across tools reduces context-switching overhead and training costs. The dollar value is hard to quantify precisely, but employee satisfaction surveys consistently rank "too many tools" in the top 3 frustrations.

---

## Infrastructure and Operations

### 10. Incident Response Runbook Automation
When production incidents occur, on-call engineers follow runbooks -- step-by-step diagnostic and remediation procedures. Most runbooks are markdown files that humans read and execute manually. Automating even the diagnostic steps (log collection, service health checks, recent deployment correlation) reduces mean time to resolution by 30-50%. For organizations where downtime costs $10K+/minute, this is significant.

### 11. Cloud Cost Anomaly Detection
Cloud bills creep up invisibly. A forgotten dev environment, an autoscaler that never scales down, a misconfigured storage policy. Automated anomaly detection on cloud spend -- flagging unexpected spikes within hours instead of at month-end -- typically identifies 10-20% in recoverable waste. On a $5M/year cloud bill, that is $500K-$1M back.

---

## Process and Compliance

### 12. Regulatory Change Tracking
Companies in regulated industries (finance, healthcare, energy) must track regulatory changes and assess impact. This is currently done by compliance teams manually monitoring government publications. An automated tracker that ingests regulatory feeds, classifies relevance, and flags impacted business processes could reduce compliance review cycles from weeks to days and avoid $100K+ in penalties from missed updates.

### 13. Contract Clause Extraction
Legal teams review hundreds of contracts per quarter, manually identifying key clauses (termination, liability, SLA commitments, auto-renewal). An extraction tool that parses contracts and surfaces critical terms saves 2-4 hours per contract and reduces the risk of missed obligations. At $400/hour for legal review time, this adds up fast.

---

## How to Use This List

1. **Find the one that makes you angry.** The best prototypes come from personal frustration, not top-down strategy decks.
2. **Scope it down.** You do not need to solve the whole problem. Solve one slice of it with a working demo.
3. **Frame the value.** Use the dollar hints above as a starting point, then adjust for your organization's actual numbers. See [problem-framing.md](../guidelines/problem-framing.md) for the formula.
4. **Build it.** Not a slide deck. Not a proposal. A working prototype. Then submit it.
