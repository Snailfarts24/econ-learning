# Stage 5: Design and estimation

Claude does not propose identification strategies. It asks the user to state the estimand, the assumption that identifies it, and why that assumption is credible here. Implementation details (packages, staggered-DiD estimators, IV diagnostics) are covered by econ-data-pipeline's estimation reference when it is available.

## Contents
1. The four questions
2. Estimand
3. Identifying assumptions
4. Design-specific probes
5. Controls
6. Inference
7. Validity checks and pre-specification
8. Common errors to probe for
9. Worked checkpoints

## 1. The four questions

Every design should answer these, in order:
1. What is the causal relationship of interest?
2. What experiment would ideally capture it?
3. What is the identification strategy: how does the observational comparison approximate that experiment?
4. What is the mode of inference: standard errors, clustering, sample, representativeness?

If the user jumps to a method ("I'll run a DiD"), go back to 1 and 2 first.

## 2. Estimand

- What quantity, for whom? Average effect for everyone, for the treated, for units whose treatment responds to an instrument, at a threshold?
- Is that the quantity your question and mechanism are about? (See mechanisms.md, section 4.)
- Is the effect likely the same for everyone? If not, which units does your design weight most?

## 3. Identifying assumptions

- State the assumption in words: what must be true about the units that didn't receive treatment for them to stand in for the treated units' untreated outcomes?
- What story would make the assumption fail? Be specific to this setting.
- If you need several assumptions, rank them from most to least credible. Which one would a skeptical referee attack first?
- What facts about the setting support the assumption? What would you need to see in the data?

## 4. Design-specific probes

**Difference-in-differences and event studies**
- What would make treated and control trends diverge even without treatment?
- Is treatment timing staggered? If effects change over time, what happens to a standard two-way fixed effects estimate? (Already-treated units can act as controls.)
- Could units anticipate treatment and respond early?
- Which period is the reference, and why? How are distant leads and lags handled?

**Instrumental variables**
- Tell the story of how the instrument could affect the outcome other than through the treatment. Why don't you believe that story?
- Is the first stage strong? How will you check?
- Could the instrument push some units toward treatment and others away?
- Who are the compliers, and is their effect the one you care about?

**Regression discontinuity**
- Can units manipulate which side of the cutoff they land on? How would you check?
- Does anything else change at the cutoff?
- How far from the cutoff does the estimate generalize?

**Selection on observables**
- Which variables drive selection into treatment? Are they all observed?
- What unobserved factor would most plausibly bias the estimate, and in which direction?
- How large would it need to be to overturn the result?

**Shift-share / exposure designs**
- Where does identification come from: the shares or the shocks? Which needs to be as good as random?

## 5. Controls

- For each control: why is it in the regression? What confounding does it address?
- Could treatment affect this control? If so, conditioning on it can create bias rather than remove it.
- Which fixed effects, and what variation do they leave for identification?

## 6. Inference

- At what level is treatment assigned? Errors should be clustered at least at that level.
- How many clusters? If few, what is the plan?
- Could outcomes be correlated across space or networks beyond the clusters?
- How many outcomes or subgroups will you test? How will you handle multiple testing?

## 7. Validity checks and pre-specification

- Which tests address your most vulnerable assumption? (Pre-trends, balance, placebo outcomes, placebo timing, first-stage strength, density at the cutoff.)
- What result from those tests would make you abandon or change the design?
- Before seeing the main estimates, write down the main specification: outcome, treatment, controls, sample, clustering. Changes after that point should be recorded with their reason.
- Could you simulate data where you know the true effect and check that your code recovers it?

## 8. Common errors to probe for

- Choosing a method before stating the estimand and ideal experiment.
- An identifying assumption stated generically ("parallel trends hold") without saying what could break it here.
- Post-treatment variables used as controls.
- Clustering below the level of treatment assignment.
- Staggered timing with a standard two-way fixed effects estimator and heterogeneous effects.
- An exclusion restriction defended by assertion.
- Specification chosen after seeing which one gives significance.

## 9. Worked checkpoints

**Bad control**

> `Checkpoint (design): controls`
> Claude: You're estimating the effect of a college degree on earnings and including occupation as a control. Why is occupation in the regression?
> User: Different occupations pay differently, so it removes noise.
> Claude: That doesn't work here. Ask yourself: does getting a degree affect which occupation someone ends up in?

Consolidation: occupation is an outcome of the degree. Conditioning on it compares graduates and non-graduates within the same occupation, which removes part of the effect and compares groups that selected into occupations differently. A control must be determined before treatment.

**Exclusion restriction**

> `Checkpoint (design): exclusion`
> Claude: Your instrument is distance to the nearest college. Tell the story of how distance could affect earnings other than through schooling.
> User: I can't think of one.
> Claude: Think about what else differs between places that are near and far from colleges.

Rung 2 if needed: "This is an exclusion-restriction problem. Places near colleges tend to be urban, with different labor markets."

**Clustering**

> `Checkpoint (design): inference`
> Claude: Treatment is assigned by state, your data is individual workers, and you've clustered by individual. What does that assume about workers in the same state?
> User: That their errors are independent.
> Claude: Correct. Is that plausible for workers in the same state facing the same policy and labor market? What does it do to your standard errors if it isn't?
