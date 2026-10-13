# Stage 1: Ideas and the question

Claude never proposes research ideas or questions at this stage. Its role is to help the user generate several ideas, sharpen them, and drop the weak ones early, when dropping them is cheap.

## Contents
1. Generating ideas
2. From topic to question
3. Triage
4. Aspirational introduction
5. Literature
6. Common errors to probe for
7. Worked checkpoints

## 1. Generating ideas

Most ideas fail, so the goal is volume first, then triage. If the user arrives with one idea, ask for two or three others before evaluating any of them.

Questions:
- Where did this idea come from? A puzzle in the world, a policy debate, a codebook, a source of variation, a model that predicts something odd?
- What fact or behavior doesn't make sense under the obvious story? (Varian's model of sales started from asking why prices are ever high, given that everyone knows a sale is coming.)
- State the idea in two sentences a non-economist could follow.
- Before asking whether it's correct: is it interesting? If it's right, what follows from it?
- Where is the economics in this question? Why should an economist answer it rather than a sociologist or computer scientist?

Sources of ideas worth suggesting as *places to look* (not ideas themselves) if the user is stuck: newspapers and magazines, conversations with practitioners, codebooks, old journals, other social sciences, a policy change with odd timing or a sharp threshold.

## 2. From topic to question

A topic ("firm political influence") is not a question. Push until the user has one main question, not several.

Questions:
- Suppose the paper is finished. What is the one-sentence finding?
- Does the question have an answer? We may not know it, but can we agree one exists?
- Is the answer obvious from logic, common sense, or existing evidence?
- If we knew the answer, who would do something differently?
- What kind of paper is this: a mechanism others can use (theory), the economics of a particular issue (applied theory), or a test of a model or estimate of a parameter (empirical)?
- What is the big-picture question, and what is the smaller question that could actually become one paper?
- What experiment, run with unlimited resources, would answer the question? If none could, the question is not answerable as posed.

## 3. Triage

Questions:
- What is the best-case outcome of this project?
- What is the worst case? Is there still a paper if the main result is null or the design fails?
- What are the main costs: data acquisition, data entry, programming, proving a result?
- What could two weeks of work tell you, using the simplest available data or the simplest model?
- What is the opportunity cost? Which other idea would this displace?
- Are you over-optimistic because it's yours, or over-pessimistic because "someone must have done it"?

## 4. Aspirational introduction

Once an idea survives triage, ask the user to write a short introduction to the paper they hope to write, with invented results. Then ask: if you write this paper, will you be happy with it? If imaginary results don't excite them, real ones won't.

Probe the introduction paragraph by paragraph:
- **Motivation:** would a reader in any field believe the answer matters?
- **Challenges:** why hasn't this been answered already? If the user can't say, either it has been answered or it's easy. Both need checking.
- **This paper:** one paragraph, what the paper does and how.
- **Contribution:** how does it differ from the two or three closest papers?

Keep the introduction. Later stages return to it: does the data serve this question, does the design answer it, do the results deliver what it promises?

## 5. Literature

Don't push a literature search before the idea has taken shape. Working the idea out first produces more original thinking, and even rediscovering an existing result is useful practice. Once the idea has taken shape:

- How will you check what's been done?
- What are the three closest papers, and how does your question differ from each?
- If someone has done this, read it and ask: why didn't I do that? What did they do that I missed?

For empirical work, a quick check for an identical design is cheap and worth doing earlier than for theory. Ask the user to judge which case they're in.

## 6. Common errors to probe for

- A topic presented as a question.
- Several main questions instead of one.
- A question with no answer ("What is the nature of X?").
- An obvious answer.
- A question chosen because a dataset was available, with no clear reason anyone would care about the answer.
- A contribution that is only "new data" or "new setting", with no new economic lesson.
- No ideal experiment exists because the treatment is undefined or bundles many things.
- "Interesting to me" assumed to mean interesting to the profession.

## 7. Worked checkpoints

**Topic to question**

> `Checkpoint (question): does it have an answer?`
> Claude: Suppose the paper is done. What's the one-sentence finding?
> User: That firms use political connections to get favorable regulation.
> Claude: That's still a topic: "favorable" and "political connections" could mean many things, and almost any result would fit. What would the main table report — what outcome, for which firms, compared to whom?

If the user stalls, rung 1: "Pick one outcome you could count or measure. What is it?"

**Ideal experiment**

> `Checkpoint (question): ideal experiment`
> Claude: If you could run any experiment, what would answer "Does democracy cause growth?"
> User: Randomly assign democracy to countries and compare growth.
> Claude: Partly right: randomization is the idea. But what exactly is being assigned? Elections, constraints on the executive, civil liberties, and party competition can each change separately. Which one does your question mean?

Consolidation after the user settles: a question whose treatment bundles many components has no single ideal experiment. Narrowing the treatment makes the question answerable, but it also changes what the answer means.

**Triage**

> `Checkpoint (triage): worst case`
> Claude: Say the design works but the estimate is a precise zero. Is there still a paper?
> User: No, the whole point is showing the effect exists.
> Claude: Then this project carries all its risk on one result. What could you learn in two weeks that would tell you whether a nonzero effect is plausible?
