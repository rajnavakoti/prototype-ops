# Approved AI Tools

> **This is a template.** Every section below contains placeholder examples. Your organization must customize this document with your actual approved tools, licensing details, and internal policies before distributing it. Delete this callout once customized.

---

## Why This Document Exists

People are already using AI tools. Some are using tools the company provides. Some are using personal accounts, free tiers, and tools nobody in IT has heard of. That is shadow AI, and the risk is not that people are using AI — it is that they are using it without guardrails.

This document serves two purposes:
1. Show people what tools they already have access to (most do not know the full list)
2. Help people choose the right tool for the job (so they stop reaching for unauthorized alternatives)

If the company-provided tools do not cover a legitimate need, that is valuable information. Report the gap to [INSERT TEAM/CHANNEL]. That feedback shapes future tool decisions.

---

## Approved Tool List

### Code Generation and Development

| Tool | Access | License Type | Best For |
|---|---|---|---|
| GitHub Copilot | All engineering roles | Enterprise seat | Code completion, boilerplate generation, test writing |
| Claude Code (CLI) | Teams with Claude Enterprise | Enterprise | Multi-file coding tasks, refactoring, code review, agentic workflows |
| [YOUR TOOL] | [WHO HAS ACCESS] | [LICENSE] | [USE CASE] |

### General AI Assistants

| Tool | Access | License Type | Best For |
|---|---|---|---|
| Claude (claude.ai) | All employees | Enterprise / Team | Writing, analysis, research, document review, brainstorming |
| ChatGPT | All employees | Enterprise | Writing, analysis, general questions |
| [YOUR TOOL] | [WHO HAS ACCESS] | [LICENSE] | [USE CASE] |

### Specialized Tools

| Tool | Access | License Type | Best For |
|---|---|---|---|
| Cursor / Windsurf | Engineering teams | Team license | AI-native code editors with integrated chat and generation |
| Notebook LM | All employees | Google Workspace | Research synthesis, document-based Q&A |
| [YOUR TOOL] | [WHO HAS ACCESS] | [LICENSE] | [USE CASE] |

### API Access (For Building Prototypes)

| API | Access | Rate Limits | Cost Model |
|---|---|---|---|
| Anthropic API (Claude) | Request via [TEAM/FORM] | [LIMITS] | Pay-per-token, charged to team budget |
| OpenAI API | Request via [TEAM/FORM] | [LIMITS] | Pay-per-token, charged to team budget |
| [YOUR API] | [ACCESS METHOD] | [LIMITS] | [COST MODEL] |

---

## When to Use What

### "I need to write or edit text"
Use a general AI assistant (Claude, ChatGPT). These handle drafting, editing, summarizing, and rewriting. Do not paste confidential documents into tools on personal accounts — use the enterprise versions.

### "I need to write or review code"
Use GitHub Copilot for inline code completion in your editor. Use Claude Code for larger tasks: multi-file changes, refactoring, understanding unfamiliar codebases, debugging. Use Cursor or Windsurf if your team has licenses and you prefer an AI-native editor.

### "I need to analyze data or documents"
Use Claude or ChatGPT with file upload for document analysis. For structured data, consider whether a Python script (which Copilot or Claude Code can help you write) is more appropriate than pasting data into a chat interface.

### "I need to build a prototype"
Use API access. Request API keys through the approved process. This gives you programmatic access to AI models — you can build pipelines, integrations, and workflows that a chat interface cannot support. See the security guidelines for what data you can and cannot send through APIs.

### "I need something not on this list"
Ask first. Contact [INSERT TEAM/CHANNEL] with what you need and why. The answer might be "we already have that" (common), "use this alternative" (also common), or "let us evaluate it" (takes time but the right path).

---

## What Is NOT Approved

This matters. Using unauthorized tools with company data creates real risk — data leakage, compliance violations, and security exposure.

**Not approved** means:
- Personal accounts on approved tools (use your enterprise account, not your personal Gmail-linked account)
- Free tiers of AI services (these often use your data for training)
- Open-source models running on personal hardware with company data
- Browser extensions that send page content to third-party AI services
- Any tool not on this list, until explicitly approved

**If you are unsure**, ask. Nobody will be penalized for asking. People get penalized for not asking and creating a data incident.

---

## Getting Access

| Need | How |
|---|---|
| Enterprise AI assistant account | [PROCESS — e.g., request via IT portal, auto-provisioned, ask your manager] |
| GitHub Copilot seat | [PROCESS] |
| API keys for prototyping | [PROCESS — include expected usage and budget approval] |
| A tool not on this list | [PROCESS — submit request to TEAM with use case] |
| Help choosing the right tool | [CHANNEL — e.g., #ai-tools Slack channel, office hours link] |

---

## Tool Updates

This document is reviewed and updated [quarterly / monthly / as needed]. Tools get added, removed, or change licensing. Check the date at the top of this document. If it is more than [3 months] old, ask [TEAM] for the current version.

Last updated: [DATE]
Maintained by: [TEAM]

---

## A Note on Shadow AI

If you are using an unauthorized tool because the approved tools do not meet your needs — that is a signal, not a crime. The goal of this document is to make the approved tools so visible and accessible that reaching for unauthorized alternatives becomes unnecessary.

But if you have found a tool that genuinely does something our approved stack cannot, tell us. Submit it for evaluation. That is how the approved list grows. What we cannot do is have 500 people independently deciding which AI services get access to company data.
