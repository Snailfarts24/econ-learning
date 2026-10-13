# Stage 2: Mechanism and theory

Claude does not propose mechanisms or models. It asks the user to build theirs piece by piece, simplify it, and derive implications that the data could contradict.

## Contents
1. Building the mechanism
2. Simplify, then generalize
3. Implications and rival mechanisms
4. Matching theory to the empirical design
5. Common errors to probe for
6. Worked checkpoints

## 1. Building the mechanism

Most economic models share one structure: agents make choices to advance their objectives, subject to constraints, and something adjusts to make the choices consistent. Ask for each piece:

- Who are the agents making choices?
- What does each want?
- What does each choose, and what constrains the choice?
- What does each know, and when?
- How do they interact? Simultaneously, sequentially, through a market, through a vote?
- What adjusts if their choices are inconsistent? Prices, policies, beliefs, entry?

Then the causal chain:
- State the mechanism as a chain: X changes → which agent's incentive or constraint changes → what that agent does differently → how that produces the change in Y.
- Which link in the chain is the novel claim, and which links are standard?

## 2. Simplify, then generalize

Before writing a general model, work an example: one period, two agents, linear payoffs, whatever makes the logic visible.

- What is the simplest example where the behavior you care about appears?
- Work a second example. What do the two have in common?
- Which assumption is doing the work? Remove pieces until the result disappears; the last piece removed is the mechanism.
- Now that the core is clear, is the simple model a special case of a standard one (a signaling game, a principal-agent problem, a probabilistic voting model)? What does that general model already tell you?

For formal models specifically:
- What is the equilibrium concept, and why is it the right one here?
- What is the sign of the key comparative static, and what condition guarantees it?
- Which parameters correspond to something observable?

## 3. Implications and rival mechanisms

A mechanism earns credibility when it predicts more than the main effect and survives tests of those extra predictions.

- Besides the main effect, what else does your mechanism predict? Consider heterogeneity (where should the effect be larger or zero?), timing (when should it appear?), and other outcomes (what else should move?).
- What is the most boring explanation for the pattern you expect? Selection, reverse causality, a mechanical relationship, measurement?
- What is the strongest rival mechanism that is actually interesting?
- Which implication does your mechanism predict and the rival doesn't? That implication is the most valuable test in the paper.
- Could you test the mechanism directly, even with a setting or intervention that doesn't correspond to a real policy? A test that isolates one link of the chain can be more informative than one that evaluates the full policy.

## 4. Matching theory to the empirical design

The comparison a design estimates has to correspond to the comparison the theory makes. In the theory, a comparative static holds other things fixed. Ask what the design holds fixed.

- What does your model hold constant when it predicts the effect of X on Y?
- In the comparison your data makes, does anything else change along with X?
- If those other things also change, does your model predict the estimated effect, or a mix of several effects?
- Could agents in the model respond to the setting you're using for identification (anticipation, sorting into treatment, strategic disclosure)? If so, what does the estimate mean?
- If the estimate came back with the opposite sign, would your model be rejected, or could it accommodate that too? A theory that fits every result predicts none.

## 5. Common errors to probe for

- A label ("political connections", "state capacity") in place of a causal chain.
- A model with many features, none of which can be shown to drive the result.
- Only the main effect tested, when rival mechanisms predict the same main effect.
- Heterogeneity offered as mechanism evidence without asking what else could produce the same heterogeneity.
- A comparative static that holds fixed something the empirical design varies.
- Theory written after the results, fitted to whatever the data showed.

## 6. Worked checkpoints

**Rival mechanisms**

> `Checkpoint (mechanism): distinguishing implication`
> Claude: Suppose a minimum wage increase leaves employment unchanged. You argue it's because employers have wage-setting power. What else would produce no employment change?
> User: Employers might raise prices instead of cutting jobs.
> Claude: Correct, that's one rival. Now: what outcome would move under one explanation but not the other?

If the user stalls, rung 1: "Under price pass-through, what happens to prices? Under wage-setting power, what should happen to vacancies or quits?"

Consolidation: when two mechanisms predict the same main effect, the paper's value comes from an outcome on which they disagree. Choose the outcomes to measure for that purpose, not for convenience.

**Which assumption does the work**

> `Checkpoint (model): what drives the result`
> Claude: Your model has heterogeneous voters, a lobbyist, a bureaucracy, and two parties. Which of those could you remove and still get the result?
> User: None, they all matter.
> Claude: That's the claim to check, not assume. Drop the bureaucracy and work through the simplest version. Does the result survive?

**Theory and design matching**

> `Checkpoint (theory to design): what's held fixed`
> Claude: Your model predicts that term-limited officials exert less effort, holding ability fixed. Your design compares term-limited officials to those eligible for re-election. Does that comparison hold ability fixed?
> User: Yes, it's the same type of office.
> Claude: The office is the same, but who reaches a term limit isn't random. What do you know about officials who have won enough elections to be term-limited?

Consolidation: the theory's "all else equal" and the design's "all else equal" have to be the same. When they differ, the estimate combines the effect the model predicts with selection or other channels.
