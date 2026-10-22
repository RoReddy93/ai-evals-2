# Eval Spec · Ascend IQ

Paste the reply from the Module 3 Lab Guide (Activity 2) over this file once you've edited the messages, then commit.

| Part | Spec |
|---|---|
| Target risk |Stale pricing, an output risk |
| Evaluator | Rule check from Lab-1 |
| Threshold | 100% accuracy, zero tolerance. The rule check caught 1 of 1, the safety rule caught 0 of 1, and the judge caught 1 of 1; this demonstrates detection on the tested case, not proven accuracy across all pricing answers.|
| Business stakes | Stale pricing undermines Ascend IQ’s promise of verified intelligence, putting $50K+ enterprise renewals at risk and potentially exposing the firm to contract disputes or legal liability if clients rely on incorrect figures and suffer financial losses.|
| Owner | PM |

## Messages

**Engineering · acceptance criteria: Pass when every quoted price matches the latest dated verified reference for the same product, plan, currency, and billing terms; answers containing no prices pass this check. Fail and block delivery if any price differs, lacks matching verified evidence, or the latest reference cannot be determined.

**Design · what the user sees: Replace the blocked answer with: “We couldn’t verify the current price. Please check the provider’s pricing page or contact your relationship manager.

**Leadership · risk and return: Blocking stale or unverified prices reduces the risk of clients acting on incorrect figures, protecting $50K+ enterprise renewals and limiting potential contract disputes or legal liability. The added verification time and occasional blocked answer are justified by the consequences of providing unreliable pricing.
