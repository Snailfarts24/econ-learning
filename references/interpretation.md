# Stage 6: Interpretation

Claude does not interpret results for the user. It asks the user to state what the estimates mean, what they rule out, and whether the paper delivers what the aspirational introduction promised.

## Contents
1. Before believing a result
2. Magnitudes
3. Uncertainty and nulls
4. Back to the mechanism
5. Robustness
6. Heterogeneity
7. External validity
8. Back to the introduction
9. Common errors to probe for
10. Worked checkpoints

## 1. Before believing a result

- Is the sign what the mechanism predicts? Is the size plausible?
- If the result is surprising, what would a coding error that produces this result look like? Check that first.
- Does the estimate change sharply with small changes to the sample? Which observations drive it?

## 2. Magnitudes

- Express the estimate in economically meaningful units. A one-unit change in X is how large relative to its standard deviation, or to typical policy changes?
- Compare it to a benchmark: the mean of the outcome, prior estimates, the cost of the policy.
- Run a back-of-envelope calculation: if the estimate is right, what does it imply in aggregate? Is that implication believable?
- With logs or elasticities, state what the coefficient means in one sentence a non-economist could follow.

## 3. Uncertainty and nulls

- What range of effects does the confidence interval rule out? What does it fail to rule out?
- For a null result: is it a precise zero or an imprecise estimate? Could it rule out the effect sizes your mechanism or prior work implies?
- Is the result statistically significant but economically small, or economically large but imprecise? Which matters for your question?

## 4. Back to the mechanism

- Which mechanisms are consistent with the result? Which does it rule out?
- Did the implications that distinguish your mechanism from the rival come out as predicted?
- If not all implications held, what does that say about the mechanism?

## 5. Robustness

Each robustness check should target an assumption.

- For each check: which assumption does it test? What result would have worried you?
- Are you adding checks that can only pass? A check that couldn't fail tests nothing.
- How many specifications did you try before settling on the main one? Are all of them reported or summarized?
- If results differ across specifications, which specification is most defensible, and why, independent of the result it gives?

## 6. Heterogeneity

- Were the subgroups chosen before seeing results, based on the mechanism? Or found by looking?
- How many subgroups were tested? How many would show significant differences by chance?
- Does the heterogeneity pattern distinguish your mechanism from the rival, or do both predict it?

## 7. External validity

- Whose effect did you estimate? (Compliers, units near a threshold, early adopters, the population in your data.)
- Would the effect be the same elsewhere? What about the setting might make it larger or smaller?
- Is the parameter portable to other settings, or specific to this one?

## 8. Back to the introduction

Return to the aspirational introduction and rewrite it as a contract with the reader: the paper promises only what it delivers.

- Which claims in the original introduction do the results support?
- Which claims would you like to make but can't? Do you need more analysis, or a weaker claim?
- Does the findings paragraph connect to the motivation paragraph?

## 9. Common errors to probe for

- A null result read as "no effect" when the confidence interval includes large effects.
- Statistical significance treated as economic importance.
- Robustness checks that don't target any assumption.
- Heterogeneity found by search and presented as a test of the mechanism.
- Claims about mechanisms the design didn't test.
- Generalizing from compliers or a local sample to everyone.
- A surprising result accepted without first ruling out a coding error.

## 10. Worked checkpoints

**Interpreting a null**

> `Checkpoint (interpretation): what a null rules out`
> Claude: Your estimate is 0.02 with a 95% confidence interval of [-0.15, 0.19], where the outcome is log employment. What can you conclude?
> User: The policy had no effect on employment.
> Claude: That's stronger than the estimate supports. What effect sizes are still inside that interval?

Consolidation: the interval includes employment changes of roughly ±15–20%. The data can't distinguish no effect from a large one in either direction. The defensible statement is about which effects are ruled out, and here few are.

**Robustness that tests nothing**

> `Checkpoint (interpretation): robustness`
> Claude: You've added a specification with state-specific linear trends. Which assumption does that check address, and what result would have worried you?
> User: It shows the result is robust.
> Claude: Robust to what? Name the threat this specification is meant to address.

**Claim vs. evidence**

> `Checkpoint (interpretation): back to the introduction`
> Claude: Your introduction says the paper shows firms gain regulatory favors through lobbying. Your design estimates the effect of lobbying on contract awards. Does the result support the introduction's claim?
> User: Yes, contracts are a regulatory favor.
> Claude: Partly. Contract awards are one outcome, but the claim also includes the mechanism: that lobbying causes the favor. Which part of that did your design identify, and which part is interpretation?
