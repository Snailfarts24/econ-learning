# Stage 4: Data construction

This stage covers the analytical decisions in building the dataset. Implementation and enforcement (audited merges, row-count logging, schema validation) belong to econ-data-pipeline when it is available; this file covers the questions the user should answer before that code is written.

## Contents
1. Unit of observation and panel structure
2. Keys and merges
3. Sample restrictions
4. Variable construction
5. Consistency over time
6. Aggregation and weights
7. Common errors to probe for
8. Worked checkpoints

## 1. Unit of observation and panel structure

- What is one row in the analysis dataset? (e.g. firm-year, county-month, legislator-vote)
- At what level is treatment assigned, and at what level is the outcome measured? Do they match?
- Should the panel be balanced? What happens to units that enter or exit, and is entry or exit related to treatment?
- What does it mean for a unit to be absent in a given period: it didn't exist, it existed but wasn't recorded, or its value was zero?

## 2. Keys and merges

- For each merge: what is the expected relationship (one-to-one, many-to-one)? Why?
- What share of rows do you expect to match? What would a much lower share mean?
- What does an unmatched row represent in each dataset? Should it be dropped, kept with a missing value, or kept as a zero?
- Do the time dimensions align? Fiscal vs. calendar year, election year vs. term year, reporting date vs. event date?
- Could the keys have changed over time (renamed firms, mergers, redrawn boundaries)?

## 3. Sample restrictions

For each restriction, ask:
- Why is this unit excluded? State the reason before seeing how the restriction affects results.
- Does the restriction depend on a variable that could be affected by the treatment? If so, it can create a difference between groups that the treatment didn't cause.
- Does it depend on the outcome? Selecting on the outcome biases the estimate.
- Restricting to units that survive the whole period: is survival related to treatment?
- Trimming outliers: decided by a rule fixed in advance, or after looking at the estimates?

## 4. Variable construction

- Treatment timing: in which period does treatment start, and when could the outcome first respond? Is there an off-by-one risk?
- Leads and lags: are they built on the full sample, before restrictions drop periods?
- Denominators: per capita, per worker, per dollar of assets? Does the denominator respond to treatment?
- Nominal or real? Deflated with which index?
- Missing vs. zero: for each key variable, which one does an absent value mean?
- Logs: what happens to zeros? Does the transformation choice change what the coefficient means?

## 5. Consistency over time

- Did variable definitions, reporting thresholds, or coding schemes change during the sample?
- Industry classifications (e.g. SIC to NAICS), geographic boundaries (county or district changes), survey redesigns: how will you handle them?
- Is a jump in a series a real change or a definitional break?

## 6. Aggregation and weights

- If you aggregate, what weights are implied? Does an unweighted average over units of very different size answer your question?
- Should regressions be weighted? Weighting changes the estimand. What population is your question about?

## 7. Common errors to probe for

- A missing report coded as zero, or a true zero coded as missing.
- A sample restriction based on a post-treatment variable (e.g. keeping only firms that survive to the end).
- Treatment timing off by one period.
- Leads or lags built after restricting the sample, creating spurious missings.
- A denominator that itself responds to the treatment.
- Treatment assigned at a level different from the analysis unit, with no thought about what that implies for inference.
- Definitional breaks treated as real changes.

## 8. Worked checkpoints

**Missing vs. zero**

> `Checkpoint (data construction): missing vs. zero`
> Claude: Some firms have no lobbying report in a given year. What value should lobbying spending take for them?
> User: Missing, so they drop out of the regression.
> Claude: Dropping them changes who's in your sample, and the change isn't random. What does the absence of a report mean under the disclosure rules?

Consolidation: when a report is required above a threshold, absence usually means spending below that threshold, so zero (or "below threshold") is closer to the truth than missing. Coding it as missing restricts the sample to active lobbyists, which conditions on part of the outcome.

**Conditioning on a post-treatment variable**

> `Checkpoint (data construction): sample restriction`
> Claude: You're keeping only firms present in every year from 2005 to 2020. Could treatment affect which firms make it to 2020?
> User: Maybe, but a balanced panel is cleaner.
> Claude: Cleaner to estimate, but what does it do to the comparison? If treatment drives some firms out, who is left in the treated group?

**Timing**

> `Checkpoint (data construction): treatment timing`
> Claude: The law passed in November 2012. Your data is annual. Which year is the first treated year?
> User: 2012.
> Claude: The law existed for less than two months of 2012. What fraction of 2012 outcomes could it have affected, and what does that do to an effect estimated for "2012"?
