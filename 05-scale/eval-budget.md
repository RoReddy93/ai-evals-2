# Module 5 · Eval Budget · Ascend IQ

**Quarterly budget cap:** $200,000
**Online eval spend:** $110,000 (2 of at most 3 online evals)

## Budget

| Failure | Trust metric | Risk | Level | Cost |
| --- | --- | :---: | :---: | ---: |
| Data Fabrication | Hallucination Rate | P0 | Online eval | $85,000 |
| Context Specificity | Robustness | P1 | Periodic audit | $7,000 |
| Overconfident Tone | UX Trust | P1 | Periodic audit | $6,500 |
| Data Bias | Fairness | P2 | Periodic audit | $5,500 |
| Slow Answers | Latency | P3 | Online eval | $25,000 |

## Downgrades

### Periodic audit · Context Specificity (Robustness · P1)
- **Cheaper check:** weekly audit to ensure we don't provide poor response quality to the user
- **Why it’s enough:** The risk is P2 because it doesn't cause reputation damage. We may not always provide a user the response they're seeking; i.e. sometimes it may be verbose and not to the point

### Periodic audit · Overconfident Tone (UX Trust · P1)
- **Cheaper check:** Weekly audit using LLM judge to check if the tone is not risky or over confident 
- **Why it’s enough:** The risk is P2 so we will run periodic audits using an LLM judge with human in the loop

### Periodic audit · Data Bias (Fairness · P2)
- **Cheaper check:** Weekly audit to check if production data is statistically similar to reference/training data class distribution
- **Why it’s enough:** The risk is P2 because it's rare that data bias will occur in one week assuming there is no bias in the training data. We usually see this happen if we don't check for bias over a period of time.

