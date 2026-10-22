# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).

## 1. Product Strategy, The Context

**Who it's for:** VP-level strategists and product leaders at Fortune 500 companies who pay upward of $50,000 a year for verified market intelligence.

**What they use it for:** Asking plain-language questions, like “Compare the pricing models of Stripe and Adyen,” and getting answers in seconds instead of digging through the platform.

**What's at stake:** Engagement is dropping, Q4 retention is at risk, and the CPO wants Ascend IQ live for the top 50 enterprise accounts next month. One poor answer to the wrong client can do lasting damage to the relationship.

## 2. Measurements, The Execution

**User promise.** For VP-level enterprise strategists, Ascend IQ delivers source-supported answers to competitor-research questions, reducing research time versus manual search and synthesis. We target delivery within five seconds for 95% of supported queries, with additional verification time when needed.

**Top 3 trust metrics:**
- **Latency**, Response speed (P95 / P99). Slow kills engagement.
- **Hallucination Rate**, % of outputs that are confidently false or fabricated.
- **Fairness**, Quality consistency across user groups, geos, languages.

**Why these three:** • Hallucination, VP-level clients pay $50k+ for verified data; one fabricated stat ends the contract.
• Latency, <5s response is the only thing that beats manual digging.
• Fairness, consistent factual quality across English, German & French etc. underpins our quality across the globe,

## 3. Strategic Trade-Offs, The Cost

### Trade-off 1 · Hallucination Rate ↔ Latency
We prioritize factual reliability over the five-second latency target when additional verification is necessary. Our users rely on competitor intelligence for consequential roadmap and investment decisions, so an unsupported pricing claim creates greater risk than a modest delay. If verification takes longer, we communicate progress; if evidence remains insufficient, we explicitly say so.

### Trade-off 2 · Fairness ↔ Latency
We allow additional retrieval and verification time for German and French queries when testing shows this improves factual accuracy or citation support. European customers pay for the same dependable intelligence as English-speaking customers, so faster responses should not come at the expense of a lower quality standard. We measure completion and abandonment by language to ensure the added wait remains acceptable.

---
_Generated from the AI Evaluation Strategy Canvas, M1 lab tool, AI Evals Certification._