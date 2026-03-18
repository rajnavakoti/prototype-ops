# Prototype Submission

> **Submission Title:** Meeting Decision Recorder
> **Submitter:** Priya Sharma / @psharma
> **Date:** 2026-03-03
> **Category:** automation

---

## Problem Statement

In a 500-person organization running an average of 180 meetings per day, decisions and action items routinely disappear into the void. Meeting notes — when they exist — live in personal notebooks, scattered Google Docs, or Slack threads that no one revisits. A recurring pattern has emerged: teams spend 15-20 minutes in follow-up meetings re-establishing what was decided in the previous one because no one can locate the record. When disputes arise about what was agreed, there is no authoritative source.

This is not a note-taking problem. People take notes. The problem is extraction and accountability: pulling structured decisions and action items (with owners and deadlines) out of unstructured conversation, and making them findable after the fact. Our Q4 internal survey showed that 67% of employees reported "unclear action items after meetings" as a top-3 productivity blocker. Engineering managers estimated they spend 3-4 hours per week chasing down whether decisions from prior meetings were actually executed.

---

## Dollar Value Framing

- **Value type:** Cost saving
- **Estimate:** $412,000/year
  - Re-discussion time eliminated: 180 meetings/day x 22% with re-discussion x 15 min avg x 3.2 avg attendees x $62/hr avg loaded cost x 250 days = $246,000/year
  - Manager follow-up time: 85 managers x 2 hrs/week saved x 48 working weeks x $78/hr avg loaded cost = $127,300/year
  - Missed deadline reduction (downstream impact): estimated $38,700/year based on 23% reduction in slipped commitments at current rework cost rates
- **Assumptions:**
  - 22% re-discussion rate is from the Q4 survey (self-reported, likely conservative)
  - Not all 180 daily meetings will use the tool immediately; estimate assumes 60% adoption within 6 months
  - Dollar values use loaded cost (salary + benefits + overhead), not just salary
  - Savings compound as the searchable decision archive grows over time
- **Confidence level:** Medium

---

## Working Prototype

- **Link:** [github.com/psharma/meeting-decision-recorder](https://github.com/psharma/meeting-decision-recorder)
- **Tech stack:** Python 3.12, OpenAI Whisper (large-v3) for transcription, Claude API (Sonnet) for decision/action extraction, FastAPI, SQLite, Jinja2 templates for the web UI
- **How to run it:**
  1. Clone the repo and install dependencies: `pip install -r requirements.txt`
  2. Set environment variables: `ANTHROPIC_API_KEY`, `OPENAI_API_KEY`
  3. Start the server: `uvicorn app.main:app --reload`
  4. Upload an audio file or paste a transcript at `http://localhost:8000`
  5. View extracted decisions and action items in the web UI; search past meetings at `/search`

---

## Effort So Far

- **Time invested:** ~45 hours over 3 weeks (evenings and one weekend sprint)
- **People involved:** Priya Sharma (backend development), Tomoko Hayashi (tested with her team's actual meeting recordings, provided feedback on extraction accuracy)
- **Resources used:** Personal API keys for Whisper and Claude (total API spend: ~$34), laptop with 16GB RAM for local Whisper inference testing, 22 meeting recordings donated by volunteers (with consent)
- **What was hardest:** Distinguishing between actual decisions ("we will ship this by March 10") and hypothetical discussions ("we could potentially ship by March 10") — required careful prompt engineering and a two-pass extraction approach.

---

## What's Needed to Graduate

- **Team size:** 1 backend engineer + 1 frontend engineer for 8 weeks, then 0.25 FTE maintenance
- **Timeline:** 8 weeks to production MVP (calendar integration, SSO, persistent storage), 4 additional weeks for Google Meet/Zoom bot integration
- **Budget:** ~$52,000 (engineering time: $38K, API costs at scale: $8K/year estimate based on 100 meetings/day x avg 30 min, infrastructure: $6K/year)
- **Dependencies:**
  - Google Workspace admin approval for Calendar API and Meet recording access
  - SSO integration with corporate Okta instance
  - Legal review of meeting recording consent requirements (varies by jurisdiction)
  - Claude API enterprise agreement or upgrade from individual plan
- **Key risks to graduation:**
  - Recording consent is the biggest blocker — some jurisdictions require all-party consent, which changes the UX significantly
  - Whisper transcription accuracy drops noticeably in meetings with heavy accents, cross-talk, or poor audio quality
  - If the tool produces inaccurate decisions even 5% of the time, trust will erode quickly and people will stop using it

---

## Risk Assessment

- **Data sensitivity:** High. Meeting audio and transcripts may contain sensitive business discussions, personnel matters, or strategic plans. Production system must enforce same access controls as the meeting itself (only attendees can view outputs).
- **Security implications:** Audio files must be encrypted at rest and in transit. API calls to external services (Whisper, Claude) send meeting content to third-party servers — enterprise API agreements with data processing addendums are required. On-premises Whisper deployment is feasible and recommended.
- **Integration complexity:** Medium-high. Calendar integration is straightforward, but meeting bot injection into Google Meet/Zoom requires platform-specific APIs and admin-level permissions. Real-time processing adds latency and reliability requirements.
- **Compliance concerns:** GDPR and local privacy laws govern recording of conversations. Must implement: explicit recording consent mechanism, data retention policies (auto-delete after configurable period), right-to-deletion for individuals, and audit logging of who accessed what.

---

## Demo

- **Video walkthrough:** [drive.google.com/file/d/meeting-recorder-demo](https://drive.google.com/file/d/meeting-recorder-demo)
- **Screenshots:** [github.com/psharma/meeting-decision-recorder/docs/demo](https://github.com/psharma/meeting-decision-recorder/tree/main/docs/demo)
- **Live demo:** [meeting-recorder-demo.internal.company.com](https://meeting-recorder-demo.internal.company.com) (internal network only, pre-loaded with sample data)

---

## Additional Context

Tested with 22 real meeting recordings across 4 teams (engineering, product, operations, HR). Extraction accuracy benchmarked by having meeting participants verify outputs: 89% of actual decisions were captured, 94% of action items were captured with correct owners. The 11% missed decisions were predominantly implicit ones ("so we're not doing that then" — negation-based decisions where no explicit statement was made). The two-pass extraction approach (first pass: identify candidate decisions, second pass: validate and structure) reduced false positives from 31% to 7%. Tomoko's product team has been using it informally for 2 weeks and reported it "changed how they run meetings" — they now state decisions more explicitly because they know the tool is listening.
