# Effort Estimation

How to estimate what it took to build your prototype and what it would take to make it production-ready. Honest estimation is one of the strongest signals of a mature submission.

---

## Two Estimates, Two Purposes

Every submission requires two effort estimates:

1. **Prototype effort** — What you already spent building this. This is retrospective. Be accurate.
2. **Graduation effort** — What it would take to go from prototype to production. This is prospective. Be realistic.

These serve different purposes. Prototype effort shows the review panel how capital-efficient you were. Graduation effort helps them decide whether to invest.

---

## Prototype Effort: What You Already Spent

### How to Track It

Count actual hours, not elapsed time. "I worked on this for two weeks" means nothing. "I spent 24 hours over two weeks, mostly evenings and one Saturday" is useful.

Break it down:

| Activity | Hours |
|---|---|
| Problem research and scoping | X |
| Building the core logic | X |
| UI/interface work | X |
| Testing and debugging | X |
| Writing the submission | X |
| **Total** | **X** |

### What Counts

- Your time building, testing, iterating
- Time from anyone who helped you (credit them)
- Time spent learning a new tool or framework specifically for this prototype
- Cloud costs, API costs, or any money spent

### What Does NOT Count

- Time spent thinking about the problem before you started building (that is background, not effort)
- Your regular job tasks that happen to overlap with the problem space
- Time reading documentation you would have read anyway

---

## Graduation Effort: What Production Would Take

This is where most submissions fall apart. People underestimate graduation effort by 3-5x because they confuse "it works on my laptop" with "it works in production."

### The Graduation Estimate Template

```
Team size:        X engineers + Y other roles
Duration:         X months
Total effort:     X person-months
Key costs:        infrastructure ($X/mo), licenses ($X/mo), other ($X)
Dependencies:     list systems/teams you need access to or cooperation from
```

### What Graduation Actually Requires

Your prototype probably skipped most of these. That is fine — it is a prototype. But graduation means handling all of them:

- **Authentication and authorization**: Who can use this? How do they log in? Role-based access?
- **Data pipeline**: Your prototype uses a CSV or a hardcoded API key. Production needs a real data pipeline.
- **Error handling**: Your prototype crashes gracefully or not at all. Production needs structured error handling, logging, alerting.
- **Security review**: API keys, data handling, PII, compliance with company security standards.
- **Infrastructure**: Where does this run? Who maintains the servers/containers/functions?
- **Monitoring**: How do you know it is working? How do you know it broke?
- **Documentation**: Runbooks, onboarding docs, API docs if applicable.
- **Integration**: Connecting to existing systems (SSO, data warehouse, communication tools).
- **Testing**: Unit tests, integration tests, load tests if user-facing.
- **Support model**: Who do users contact when it breaks?

### The Multiplier Rule

If you are unsure, use this rough multiplier:

- **Prototype hours x 5-8** = graduation effort for internal tools
- **Prototype hours x 8-15** = graduation effort for customer-facing products
- **Prototype hours x 10-20** = graduation effort for anything touching regulated data

These are rough. But they are closer to reality than most first estimates.

---

## Worked Example 1: Customer Feedback Classifier

**Prototype effort**:

| Activity | Hours |
|---|---|
| Researching classification approaches | 4 |
| Building prompt pipeline with Claude API | 8 |
| Creating test dataset from real tickets (anonymized) | 3 |
| Testing and tuning classification accuracy | 6 |
| Building simple Streamlit UI for demo | 5 |
| Writing submission | 2 |
| **Total** | **28 hours** |

Cost: $12 in API calls during development.

**Graduation effort**:

| Item | Estimate |
|---|---|
| Team | 2 engineers (1 backend, 1 frontend), 1 support team liaison (part-time) |
| Duration | 3 months |
| Total effort | ~5 person-months |
| Infrastructure | Cloud hosting ~$200/mo, API costs ~$400/mo at production volume |
| Key work | Integrate with Zendesk API (ticket ingestion), build admin dashboard for support leads, implement feedback loop (agents correct misclassifications, model improves), security review for PII handling, load testing at 500 tickets/day |
| Dependencies | Zendesk API access (need IT approval), support team for UAT, security team for PII review |

**Multiplier check**: 28 hours x 8 = 224 hours. 5 person-months at ~160 hours/month = 800 hours. The actual estimate is higher than the multiplier suggests because of the Zendesk integration and PII requirements. That is a signal to explain why, which this submission does.

## Worked Example 2: Internal Knowledge Search

**Prototype effort**:

| Activity | Hours |
|---|---|
| Setting up vector database (local Chroma instance) | 3 |
| Writing document ingestion scripts | 6 |
| Building RAG pipeline | 10 |
| Indexing 500 internal documents (Confluence export) | 4 |
| Building chat-style interface | 4 |
| Accuracy testing with 30 known questions | 5 |
| Writing submission | 2 |
| **Total** | **34 hours** |

Cost: $8 in embedding API calls, $0 infrastructure (runs locally).

**Graduation effort**:

| Item | Estimate |
|---|---|
| Team | 2 engineers, 1 knowledge management lead (part-time) |
| Duration | 4 months |
| Total effort | ~7 person-months |
| Infrastructure | Vector database hosting ~$300/mo, LLM API costs ~$800/mo at scale, compute for re-indexing ~$150/mo |
| Key work | Confluence/SharePoint live sync (not one-time export), access control (users should only search docs they have permission to view), scaling to 50,000+ documents, citation and source linking, usage analytics, content freshness management |
| Dependencies | IT for Confluence API access, legal review for data handling, identity team for access control integration |

**Why 4 months**: The hard part is not the search — it is the access control. Users must not find documents they are not authorized to see. This requires integrating with the company's permission model, which adds significant complexity that the prototype intentionally skipped.

---

## Common Underestimation Pitfalls

### 1. "The hard part is done"
No. The hard part of a prototype is the core insight — proving the idea works. The hard part of graduation is everything else: security, integration, reliability, support. These are different kinds of hard.

### 2. "We just need to make it look nicer"
UI polish is 10% of graduation effort. The other 90% is plumbing you cannot see: auth, error handling, monitoring, data pipelines, edge cases.

### 3. "It already works with real data"
Your prototype works with a sample of real data that you manually prepared. Production means handling all the data, including the messy parts: missing fields, unicode issues, duplicate records, data arriving late or out of order.

### 4. "We can reuse the prototype code"
Sometimes. Often the prototype was built for speed, not maintainability. Budget for rewriting 50-70% of the code during graduation. That is normal and healthy.

### 5. "One engineer can do it"
One engineer can build a lot, but production systems need code review, on-call rotation, bus factor greater than one, and domain expertise that may require involving other teams. If your graduation plan is "me, alone, for 6 months" — reconsider.

### 6. Forgetting non-engineering work
Graduation is not just code. Factor in: security review process (2-4 weeks at many companies), procurement for new tools or services, user training and documentation, change management if this replaces an existing process.

---

## What the Review Panel Looks For

- **Prototype effort is reasonable for the output**: 30 hours for a working demo is impressive. 300 hours for the same demo raises questions.
- **Graduation estimate acknowledges complexity**: "2 weeks and we are done" is a red flag. The panel wants to see that you understand what production means.
- **Assumptions are stated**: "This assumes we get Zendesk API access within 2 weeks" is useful. Unstated assumptions become surprises.
- **Dependencies are identified**: What teams, systems, or approvals do you need? This affects timeline more than coding effort.

---

## Final Note

Under-promising and over-delivering is better than the reverse. If you estimate 4 months and finish in 3, everyone is happy. If you estimate 2 months and need 5, you have a credibility problem — even if the end result is good.
