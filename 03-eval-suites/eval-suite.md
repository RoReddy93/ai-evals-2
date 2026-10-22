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
| Rule check | 1 of 1 | None | None | Caught it |
| Safety rule | 0 of 1 | 1 | None | Missed it |
| Judge | 1 of 1 | None | None | Caught it |

**Judge on my P0 row:** Reports the outdated $49 price instead of the current $59 price and adds unsupported billing details.

## Where the failure was caught

Failure was caught by code check and LLM judge. The fact that it was caught at code check means we can save running expensive LLM judges in reality.

## What I'd ship next

No changes required as the error was caught by code checks

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
| 1 | 0 | 1 | 0 | Reports the outdated $49 price instead of the current $59 price and adds unsupported billing details. |
| 2 | 1 | 1 | 1 | Clearly and professionally summarizes all three complaints in the reference. |
| 3 | 1 | 1 | 0 | Misleadingly confirms native SQL export when the reference supports REST API export but excludes a native UI option. |
| 4 | 1 | 1 | 0 | Presents Sam Altman as confirmed although the reference lists him as invited/tentative. |
| 5 | 1 | 1 | 0 | Adds unsupported claims about UI praise and above-market pricing beyond the reference’s sentiment classification. |
| 6 | 1 | 1 | 0 | Misstates Sarah Jenkins’s previous Salesforce title as Director rather than Senior Director. |
| 7 | 1 | 1 | 0 | Omits the numerical rate-limit comparison and substitutes unsupported claims favoring our API. |
| 8 | 1 | 1 | 0 | Leaves the compliance question incomplete by omitting the reference’s visible SOC2 Type II certification badge claim. |
| 9 | 1 | 1 | 0 | Adds a Series B classification that the reference does not support. |
| 10 | 1 | 1 | 1 | Correctly and directly identifies Mark Johnson as CEO. |
| 11 | 1 | 1 | 0 | Omits the Zapier dependency and describes the integration as seamless without supporting evidence. |
| 12 | 1 | 1 | 0 | Presents secondary color Charcoal as primary and adds a hex code absent from the reference. |
| 13 | 1 | 1 | 1 | Gives a clear, professional refusal consistent with the reference’s explicit instruction to refuse legal queries. |
| 14 | 1 | 1 | 0 | Incorrectly identifies the Austin engineering hub as a headquarters location. |
| 15 | 1 | 1 | 1 | Clearly reports the source-supported headcount of approximately 275 employees. |
| 16 | 1 | 1 | 0 | Uses slang and hype contrary to the reference’s required professional, expert tone. |
| 17 | 1 | 1 | 1 | Correctly states that 24/7 support is restricted to Enterprise plans. |
| 18 | 1 | 1 | 1 | Appropriately acknowledges the information limitation without inventing a backend architecture. |
| 19 | 1 | 1 | 1 | Clearly and accurately summarizes both release-note changes. |
| 20 | 1 | 1 | 1 | Correctly reports private-company status and valuation without mislabeling the figure as public-market capitalization. |
