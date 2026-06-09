# Linen Connections — IT & Automation Roadmap

*Prepared by the IT & Automation contractor · for internal review*

---

## 1. Executive summary

Linen Connections is investing in automation to reduce manual customer-service
load and modernise its web presence. This document frames the work as **one
coherent program** rather than scattered projects, shows what is live, what is
in progress, and what the highest-value next steps are.

Guiding principle across everything:

> **Automation should reduce repetitive, low-judgement work — and keep a human
> in the loop for anything involving money, risk, or customer emotion.**

---

## 2. Where things stand today

| Workstream | Status | Value | Owner |
|---|---|---|---|
| A. AI customer-service triage (n8n) | **Live / pilot** | Cuts triage + blank-page time | IT + support |
| B. Customer sentiment analysis / light CRM (n8n) | **In progress** | Visibility into customer mood & themes | IT |
| C. Website v2 rebuild | **In progress** | Modern, faster, owned front-end | IT |
| D. Inbox & operations quick wins | **Ready to start** | Immediate, low-risk relief | IT |

---

## 3. Workstreams in detail

### A. AI customer-service triage (n8n) — *live / pilot*

Reads `orders@linenconnections.com.au`, classifies each email, and either drafts
a reply for human review, flags it for a human, or labels it as no-reply. It
**never auto-sends**. Currently safest on sizing questions.

- **Strengths:** draft-only, conservative routing, logging, kill switch.
- **Known limits (from audit):** product data and fulfilment records aren't yet
  reliable enough for broad order-status / product Q&A automation.
- **Next:** lock down risky categories to summary-only, add source-priority
  guardrails to the prompts (see §5).

### B. Customer sentiment analysis / lightweight CRM (n8n) — *in progress*

Tags incoming customer mail by sentiment and theme (e.g. delivery delay, quality
complaint, sizing) and logs it for trend visibility.

- **Value:** turns the inbox into a dashboard — "what are customers actually
  unhappy about this month?" — without hiring an analyst.
- **Natural extension:** a lightweight CRM view (customer → past orders → past
  issues → sentiment history) that the support team and AI can both reference.
- **Next:** define the sentiment + theme taxonomy, decide where it's logged
  (Google Sheets now, a proper store later), and connect it to the triage flow
  so sentiment informs routing (angry → human).

### C. Website v2 rebuild — *in progress*

A rebuilt front-end, with the existing Shopify store content captured/backed up
as the source material.

- **Status:** content backed up; research/scraping scripts in place.
- **Housekeeping done:** cleanup tooling prepared to dedupe the backup and strip
  redundant theme locale files (see `tools/`).
- **Next:** confirm the v2 stack/hosting decision, and treat product data quality
  (structured fields) as shared groundwork with workstream A.

### D. Inbox & operations quick wins — *ready to start*

Low-effort, zero-risk improvements that pay off immediately.

- **Gmail noise filters** — 65–75% of the support inbox is system/marketing
  noise. Filtering it is the single biggest perceived-load reduction, with no
  dependencies and no customer risk. (Pitch deck + importable rules prepared.)
- **Support identity cleanup** — standardise one support-facing name/signature
  (Sash for support, Sweta for marketing) to stop customer confusion.

---

## 4. Quick-wins pipeline (effort vs impact)

| Initiative | Effort | Impact | Risk |
|---|---|---|---|
| Gmail noise filters | Low | High | None |
| Lock risky AI categories to summary-only | Low | High | None |
| Source-priority guardrails in AI prompts | Low | High | None |
| Single support identity / signature | Low | Medium | None |
| Sentiment + theme tagging live | Medium | High | Low |
| Policy knowledge base (returns/refunds/exchange) | Medium | High | Low |
| Product metafields for top 50 products | Medium | High | Low |
| Record damaged-at-dispatch substitutions in Shopify | Medium | High | Low |

---

## 5. Dependencies & blockers (from the audit)

These are **business/operational** decisions that gate further automation. They
are not coding tasks — they need owner sign-off:

1. **PJ sizing contradiction** — Shopify lists S/M/L/XL; support has told a
   customer "only S/M and L/XL". One is wrong. Resolve before AI answers PJ sizing.
2. **Damaged-at-dispatch substitutions aren't recorded** — Shopify can show the
   original item shipped when a replacement was actually sent. This makes order-
   status automation unsafe until substitutions are recorded (order edit, note,
   or tracker).
3. **Product data isn't structured** — material, dimensions, care, "what's
   included", reliable stock are missing/buried. Needed before product Q&A.
4. **Policy isn't written down** — refund timeline, return address, postage
   responsibility, replacement-before-refund stance. Needed before returns drafts.

---

## 6. Suggested 90-day plan

**Days 0–30 — relief & safety (no dependencies)**
- Roll out Gmail noise filters (label-first, then archive).
- Lock AI risky categories to summary-only; add prompt guardrails.
- Stand up sentiment + theme tagging.

**Days 30–60 — foundations**
- Build the one-page policy KB (with owner).
- Add structured metafields to the top 50 products.
- Decide + start website v2 stack.

**Days 60–90 — guarded expansion**
- Resolve PJ sizing; enable sizing drafts at scale.
- Record substitutions; pilot guarded order-status summaries.
- First CRM/sentiment trend report to the business.

---

## 7. How I can keep helping (ongoing engagement)

As your IT & automation partner I can own:

- **Run & harden** the n8n workflows (reliability, error handling, dedupe).
- **Build out** sentiment analysis → lightweight CRM.
- **Deliver** website v2 and keep it maintained.
- **Operations automation** beyond email — reporting, data hygiene, integrations
  between Shopify, Gmail, Sheets, and carriers.
- **Advisory** — translate business decisions (policy, fulfilment) into safe,
  automatable processes.

The through-line: each piece compounds. Clean inbox → better data → safer AI →
more automation the business can actually trust.
