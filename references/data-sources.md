# Stage 3: Setting and data sources

The question should choose the data, not the reverse. Ask in this order: the ideal setting, the ideal dataset, then what exists or could be collected. Claude does not suggest datasets first. Once the user names a source, Claude can give facts about it (coverage, years, unit, access). On the hint ladder, Claude names a category of source before any specific dataset.

## Contents
1. Setting
2. From ideal data to available data
3. Measurement
4. Coverage and selection into the data
5. Variation and power
6. Linkage
7. Access and timeline
8. Answerability check
9. Common errors to probe for
10. Worked checkpoints

## 1. Setting

- What concrete settings could host your question: an industry, a population affected by a policy, a set of institutions?
- What makes each a good environment for the question? Sharp variation, good measurement, institutional detail you understand?
- Who else has studied this setting, and what did they ask?
- What would a finding in this setting tell us about other settings? Is the parameter portable?

## 2. From ideal data to available data

- Describe the ideal dataset: unit, variables, time span, frequency, sample.
- Now list what exists or could be collected. For each candidate, how far is it from the ideal, and in which direction?
- Could you collect or construct the missing piece (scraping, digitizing, a survey, an FOIA request)?
- Have you read the codebook? What does it say about how each key variable is defined and recorded?

## 3. Measurement

- What concept does your question need, and what variable measures it? How far apart are they?
- Who records this variable, and why? What incentives shape what gets recorded? (Administrative data reflects the rules and incentives of whoever collects it.)
- Is the measurement error likely random, or correlated with the treatment or outcome?
- Did definitions, thresholds, or coding schemes change during your period?
- Is a zero a true zero, or a missing report?

## 4. Coverage and selection into the data

- Which units appear in the data, and which don't? Is appearing in the data related to the treatment or outcome?
- Are there reporting thresholds, survivorship, or opt-in rules that determine who is observed?
- Do units enter and exit? Why?
- Is the data revised over time? Which vintage will you use?

## 5. Variation and power

- Where does the variation that identifies your effect come from, and how much of it is there?
- How many treated units or events are there? How many clusters at the level of treatment assignment?
- What effect size does your mechanism imply? Could the data detect it? A rough check: the minimum detectable effect at 5% significance and 80% power is about $2.8 \times SE(\hat\beta)$. What SE would you expect, given clustering?
- Do you have enough pre-periods to assess pre-trends, if your design needs them?

## 6. Linkage

- Will you need to link datasets? On what identifiers?
- If the link is by name or fuzzy match, what fraction do you expect to match?
- Suppose only 30% of records link. Is the sample still large enough? Are linked records different from unlinked ones in ways that matter?

## 7. Access and timeline

- What does access require: purchase, a data use agreement, IRB approval, a restricted computing environment?
- How long will that take, and what can you do in the meantime with public data?
- Has anyone used this data before? Could you learn its quirks from them or from their replication files?

## 8. Answerability check

Before committing, ask the user to map each element of the question to the data:
- the outcome → which variable?
- the treatment or key explanatory variable → which variable, measured when?
- the comparison group → which units?
- the identifying variation → where in the data?
- the validity tests the design will need → is the data there for them?

Then: what is the simplest descriptive figure you could make in two weeks that would tell you whether this is worth pursuing?

## 9. Common errors to probe for

- Data chosen because it's available, with the question bent to fit.
- A proxy far from the concept, treated as if it were the concept.
- Ignoring how units get into the data (disclosure thresholds, survivorship).
- Treatment varies at a level with too few clusters for inference.
- Too few pre-periods for the design.
- Assuming a link will work without estimating the match rate.
- Missing reports treated as zeros, or zeros treated as missing.
- Comparing across years when a definition changed.

## 10. Worked checkpoints

**Measurement and selection into the data**

> `Checkpoint (data sources): does the variable measure the concept?`
> Claude: You're measuring a firm's political influence with its federal lobbying spending. Which kinds of influence would that variable miss?
> User: It misses campaign contributions, but I can add PAC data.
> Claude: That's one gap. Think about how lobbying is reported: who files the report, and is there a threshold below which nothing appears?

Rung 2 if needed: "This is a selection-into-the-data problem: spending through trade associations or below the reporting threshold doesn't show up under the firm's name."

**Clusters and power**

> `Checkpoint (data sources): enough variation?`
> Claude: The policy you're studying was adopted by 12 states. At what level is treatment assigned, and how many units is that for inference?
> User: I have 3,000 counties, so plenty.
> Claude: That doesn't work for inference: the county count isn't what limits you. Where does the variation in treatment come from?

Consolidation: with treatment assigned at the state level, there are effectively 12 treated clusters. Standard cluster-robust errors perform poorly with few clusters, so the design may need wild cluster bootstrap or randomization inference, or a setting with more variation.

**Linkage**

> `Checkpoint (data sources): linkage`
> Claude: You'll link firms across the two datasets by name. Suppose 30% link. Which firms are most likely to be in that 30%?
> User: Probably a random subset.
> Claude: Name matching usually isn't random. Which firms have clean, consistent names across sources?
