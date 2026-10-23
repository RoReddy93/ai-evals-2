# Module 4 · Launch Strategy · Ascend IQ Copilot

## 4.0 Release Criteria

| Gate | Failure | Metric | Threshold | Dataset | Method | Runs at |
|---|---|---|---|---|---|---|
| Hard | Stale pricing | % answers that quote a price and match the live pricing API/page | 100% accuracy, zero tolerance | Ascend IQ golden set | Code-based check | Pull Request |
| Soft | Row 8 · Hallucination: contradicts the specs and criticizes a named competitor | % of answers that contradicts the information in trusted sources | 90% | Ascend IQ golden set | LLM judge | Staging |
| Advisory | Row 3 · Latency: exceeded the maximum response time | P95 latency  | 2s | Ascend IQ golden set | Code-based check | Staging |

## CI Gate Request for Engineering

- **Hard gate · Stale pricing.** Check: the code-based check, run on the Ascend IQ golden set at Pull Request. Measures: % answers that quote a price and match the live pricing API/page. Passes when: 100% accuracy, zero tolerance. On a fail: block the merge.
- **Soft gate · Row 8 · Hallucination: contradicts the specs and criticizes a named competitor.** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: % of answers that contradicts the information in trusted sources. Passes when: 90%. On a fail: pause the release until the PM signs off on an override.
- **Advisory gate · Row 3 · Latency: exceeded the maximum response time.** Check: the code-based check, run on the Ascend IQ golden set at Staging. Measures: P95 latency . Passes when: 2s. On a fail: post a warning, and don't block.

## Mitigation Plan · Soft Gate

If our Soft gate fails, do a staged rollout to check if the issues persist in production data as well. If the eval score drops in production too, roll back; fix the issue and then ship the change again.
