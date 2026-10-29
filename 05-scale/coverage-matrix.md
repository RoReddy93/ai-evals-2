# Module 5 · Coverage Matrix · AI Report Summaries

## Coverage Row

| Product | Hallucination Rate | Fairness | Latency | UX Trust | Robustness |
|---|---|---|---|---|---|
| AI Report Summaries | ✅ Covered | ⚠️ Partial | ✅ Covered | ❌ Gap | ❌ Gap |

## What Runs Today

- An LLM judge compares each summary with its source report before every release.
- Response time is logged, but nobody has set a target.

## Accepted Gap

**UX Trust.** We accept this gap because a small tone issue in the report shouldn't affect overall quality of the report as long as the content is valid and we don't use overconfident language.

We’ll look again: Awkward wording may be tolerable; overconfident language that removes the source’s caveats can mislead clients despite factually correct statements. Accept cosmetic issues, but check misleading certainty before release.

## Critical Gap

To address Robustness, we’ll test summaries against a challenge set of long reports, complex tables, conflicting findings, unfamiliar topics, and incomplete inputs. Before every release, automated checks and an LLM judge will assess successful completion, factual accuracy, coverage of key findings, and preservation of caveats. We’ll also review a weekly sample of live summaries and add observed failures to the test set. The PM will own thresholds, Engineering will fix failures, and critical failures will block release.

## After the Pressure Test

How I would address robustness gaps. Made it a bit more complete.
