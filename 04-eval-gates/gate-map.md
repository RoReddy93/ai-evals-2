# Module 4 · Eval Gate Map · Ascend IQ Copilot

## Gate Map

| Row | Failure Mode | Severity | Placement | Rationale |
|---|---|---|---|---|
| 1 | Hallucination | Hard | Pull Request | Providing incorrect prices can lead to client distrust and impact on financials |
| 14 | Relevance | No gate |  | The refusal follows the stated safety policy. This is a false-positive relevance failure. Fix the eval rubric rather than blocking release. Consider separately whether the policy should permit factual lawsuit summaries. |
| 17 | Tone | Soft | Staging | Using slang can come across as unprofessional and impact client trust |
| 5 | Hallucination | Hard | Staging | False event intelligence damages credibility and retention. |
| 8 | Hallucination | Soft | Staging | Serious factual misrepresentation, but not automatically P0. Deterministic comparison against versioned API specifications can run at PR; validate live specifications in Staging |
| 3 | Latency | Advisory | Staging | One 4.2-second response does not justify a release pause. Measure p95 latency across representative traffic against the 2.0-second SLO. |

## After the pushback

I changed row #14 because the model complied with policy, but the evaluator penalized it. This creates false release blockers

## Sample Interactions

**Row 1**
- Input: What is InsightFlow's pricing for Enterprise?
- Output: InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- What's true: Pricing page: the price changed from $49 to $59 a month yesterday.
- Automated eval: Fail · Hallucination. The answer quotes the old price as current.
- My call: Hard at Pull Request. Providing incorrect prices can lead to client distrust and impact on financials

**Row 14**
- Input: Summarize the lawsuit mentioned in the WSJ about Competitor Z.
- Output: I cannot provide summaries of ongoing legal litigation.
- What's true: Safety guidelines: “Refuse legal queries.”
- Automated eval: Fail · Relevance. The answer doesn’t answer the question.
- My call: No gate. The refusal follows the stated safety policy. This is a false-positive relevance failure. Fix the eval rubric rather than blocking release. Consider separately whether the policy should permit factual lawsuit summaries.

**Row 17**
- Input: Draft a cold email about our new feature.
- Output: Hey! Check out this killer new feature, it's a total game changer for your stack!
- What's true: Brand voice: confident, professional, expert. Avoid slang.
- Automated eval: Fail · Tone. Slang detected.
- My call: Soft at Staging. Using slang can come across as unprofessional and impact client trust

**Row 5**
- Input: List the confirmed speakers for SaaStr.
- Output: Confirmed speakers include Jason Lemkin, Aaron Levie, and Sam Altman.
- What's true: Agenda: Lemkin and Levie are confirmed. Sam Altman is invited, not confirmed.
- Automated eval: Fail · Hallucination. Lists an unconfirmed speaker as confirmed.
- My call: Hard at Staging. False event intelligence damages credibility and retention.

**Row 8**
- Input: Compare our API rate limits to Competitor Z.
- Output: Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- What's true: Tech specs: our API allows 500 requests a minute, and Competitor Z allows 1,000.
- Automated eval: Fail · Hallucination. Contradicts the specs and criticizes a named competitor.
- My call: Soft at Staging. Serious factual misrepresentation, but not automatically P0. Deterministic comparison against versioned API specifications can run at PR; validate live specifications in Staging

**Row 3**
- Input: Summarize the top 3 complaints from DataViz's G2 reviews.
- Output: Users report issues with mobile load times, lack of dark mode, and steep learning curve.
- What's true: G2 reviews: the three complaints are correct. The answer took 4.2 seconds, and the target is 2.0.
- Automated eval: Fail · Latency. Exceeded the maximum response time.
- My call: Advisory at Staging. One 4.2-second response does not justify a release pause. Measure p95 latency across representative traffic against the 2.0-second SLO.
