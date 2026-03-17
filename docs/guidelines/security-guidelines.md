# Security Guidelines for Prototyping

Practical guidance for handling data and tools when building prototypes. This is not a policy document — your organization's security policy still applies. This is the "how to actually do it" companion that helps you prototype without creating incidents.

---

## The Core Rule

**Never use real sensitive data in a prototype unless you have explicit approval and the tools are authorized for that data classification level.**

Most prototypes can be built and demonstrated with synthetic data, anonymized data, or small sanitized samples. If your prototype requires real sensitive data to prove it works, that is a conversation to have before you build — not after.

---

## Data Classification

Your organization likely has a data classification scheme. If not, use this framework and map it to whatever your company uses.

### Public
Data that is already publicly available or intended for public release.
- Published product information, marketing content, public documentation
- **Prototyping**: Use freely in any approved tool

### Internal
Data meant for internal use but not sensitive if exposed.
- Internal process docs, meeting notes (without sensitive decisions), team structures, general project plans
- **Prototyping**: Use in enterprise-licensed tools only. Never in personal accounts or free-tier services.

### Confidential
Data that would cause harm if exposed. This is where most mistakes happen.
- Customer data (names, emails, purchase history, support interactions)
- Employee data (performance reviews, compensation, personal details)
- Financial data (revenue figures, forecasts, margins, pricing)
- Strategic data (M&A activity, unreleased roadmaps, competitive analysis)
- Source code of proprietary systems
- **Prototyping**: Use ONLY in tools explicitly approved for confidential data. When in doubt, use synthetic data.

### Restricted
Data with regulatory or legal requirements governing its handling.
- PII subject to GDPR, CCPA, or similar regulations
- Payment card data (PCI-DSS)
- Health data (HIPAA)
- Data covered by NDA or contractual obligations
- **Prototyping**: Do not use in prototypes without written approval from your security/legal/compliance team. Full stop.

---

## How to Prototype Safely

### Step 1: Identify what data your prototype needs

Before writing a line of code, list:
- What data does the prototype ingest or process?
- What classification level is that data?
- Where does the data come from?
- Where does the data go (including API calls to third-party services)?

### Step 2: Use synthetic or anonymized data wherever possible

For most prototypes, you do not need real data to prove the concept works. You need data that looks like real data.

**Synthetic data**: Generate fake but realistic data. Use libraries like Faker (Python), or ask an AI assistant to generate sample datasets matching your schema.

**Anonymized data**: Take real data and strip or replace identifying information. This means:
- Replace names with random names
- Replace emails with generated emails
- Replace account numbers, IDs, phone numbers
- Remove or generalize location data (city instead of street address)
- Remove any field that could identify an individual alone or in combination

**Sampled data**: If you need a small set of real data for accuracy testing, get explicit approval and document who approved it, what data was used, and where it was processed.

### Step 3: Check your tools against the data level

| Data Level | Enterprise AI (Claude/ChatGPT Enterprise) | API Access (Anthropic/OpenAI API) | Personal/Free Tools |
|---|---|---|---|
| Public | Yes | Yes | Yes |
| Internal | Yes | Yes (with enterprise agreement) | No |
| Confidential | Check your enterprise agreement | Check your enterprise agreement | No |
| Restricted | No (unless explicitly approved) | No (unless explicitly approved) | No |

### Step 4: Handle API keys and credentials properly

- Never hardcode API keys in source code
- Use environment variables or a secrets manager
- Never commit `.env` files to a repository (add to `.gitignore`)
- If your prototype needs access to internal systems, use service accounts with minimum necessary permissions — not your personal credentials
- Rotate any API keys used during prototyping before graduation

---

## Common Scenarios

### "I want to build a tool that classifies our support tickets"
You need ticket data to train/test your classifier. Do not dump your real ticket database into an AI tool.

**Do this instead**:
1. Get 50-100 tickets from your support team lead (with their approval)
2. Anonymize them: replace customer names, emails, order numbers with fake ones
3. Keep the text content and categories (that is what matters for classification)
4. Use this anonymized set for development and testing
5. Document that you used anonymized data and who approved it

### "I want to build a RAG system over our internal documents"
You need internal documents to build the knowledge base. These documents may contain confidential information.

**Do this instead**:
1. Start with documents that are already broadly shared internally (company wiki, public-facing docs, general process guides)
2. Avoid documents with financial data, personnel information, or strategic plans
3. If you need higher-classification documents, get approval and use only tools authorized for that level
4. In your submission, clearly state what document types were indexed and their classification level

### "I need to demo with real data to show it works"
Sometimes stakeholders will not be convinced by synthetic data. That is fair.

**Do this instead**:
1. Get approval for a small, controlled sample of real data
2. Use it only in approved tools
3. Delete the sample after the demo
4. Document what you used and that it was deleted
5. In your submission, note that the demo used approved real data and describe the controls you applied

---

## What To Do If Something Goes Wrong

### You accidentally sent sensitive data to an unauthorized tool
1. Stop using the tool immediately
2. Report it to your security team or IT within 24 hours (sooner is better)
3. Document what data was sent, to which tool, and when
4. This is an incident, but reporting it promptly and honestly is always the right move. Covering it up is worse.

### You found sensitive data in a shared repository
1. Do not share it further
2. Notify the repository owner immediately
3. If it contains credentials (API keys, passwords), those credentials need to be rotated now, not later

### You are unsure whether data is sensitive
Ask. Contact your security team, your manager, or the data owner. The 5 minutes it takes to ask is worth it compared to the weeks a data incident investigation takes.

---

## Checklist Before Submitting Your Prototype

Before submitting to the prototype review process, verify:

- [ ] No real PII, customer data, or restricted data in your codebase or demo
- [ ] No hardcoded API keys, passwords, or credentials in source code
- [ ] `.env` files are in `.gitignore`
- [ ] Data sources are documented: where it came from, classification level, who approved it
- [ ] All tools used are on the approved tools list
- [ ] If you used real data for testing, it is documented and the sample was handled per guidelines
- [ ] Screenshots and demo videos do not expose sensitive data (check those terminal outputs and browser tabs)

---

## Final Note

Security in prototyping is not about preventing innovation. It is about innovating without creating risk. The fastest way to get a promising prototype killed is a security incident during development. Protect your own work by handling data correctly from the start.
