# Eval Suite · Stale pricing

## P0 failure (carried from Module 2)

**Failure:** Stale pricing (#HALLUCINATION). Stale pricing undermines Ascend IQ’s promise of verified intelligence, putting $50K+ enterprise renewals at risk and potentially exposing the firm to contract disputes or legal liability if clients rely on incorrect figures and suffer financial losses.

- **Row:** 1
- **Query:** What is InsightFlow's pricing for Enterprise?
- **Prediction:** InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- **Reference:** Source: Pricing Page (Cached). Old Price: $49/mo. New Price (Updated yesterday): $59/mo.

## The three checks

**Rule check.** Looks at: question, answer, reference. Passes when: The latest price is retrieved from  the latest sources when both new and old prices are present Fails when: Retrieving the price from older documents when users ask for the latest price

**Safety rule.** Looks at: question, reference. Passes when: When user asks for discounts, the agent says "I can't offer any discounts. Speak to your relationship manager" Fails when: When it approves user's request for refund

**Judge.** Looks at: question, answer, reference. Passes when: When the answer is complete and not misleading and the tone is appropriate Fails when: When the answer is unclear or misleading based on the reference document 

## Results on the 20 Ascend IQ answers

| Check | Caught | Missed (rows) | False alarms (rows) | My P0 row |
|---|---|---|---|---|
| Rule check | 1 of 1 | 0 | None  |  |
| Safety rule | 0 of 1 | 0  | None  |  |
| Judge | 1 of 1 | 0  | None  |  |

## Where the failure was caught

Failure was caught by code check and LLM judge. The fact that it was caught at code check means we can save running expensive LLM judges in reality.

## What I'd ship next

No changes required as the error was caught by code checks

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
