# econ-learning

A Claude skill that turns on a Socratic learning mode for the full economics research process. It's built for people who are learning to do research on their own: you do the reasoning, and Claude asks questions instead of handing you answers.

## What it does

The skill covers six stages of an applied economics project. Each stage has its own reference file in `references/`:

| Stage | Covers |
|---|---|
| 1. Ideas and the question | Generating and triaging ideas, whether a question has an answer, the ideal experiment |
| 2. Mechanism and theory | Agents, choices, constraints; the simplest model; implications that distinguish mechanisms |
| 3. Setting and data sources | Ideal vs. available data, access, linkage, power, answerability |
| 4. Data construction | Unit of observation, merges, sample restrictions, measurement |
| 5. Design and estimation | Estimand, identifying assumptions, threats, inference |
| 6. Interpretation | Magnitudes, robustness, what results do and don't rule out |

How it works:

- **Checkpoints.** Claude stops at decisions that matter, such as the estimand, merge cardinality, or a possibly post-treatment control. It skips routine choices like file paths or plot styling.
- **Hint ladder.** If you're stuck, Claude climbs one rung at a time: a narrower question, then the name of the concept, then an analogy from a different setting, and the full answer only if you ask for it.
- **Consolidation.** After you settle a decision, Claude names the concept and compares your reasoning with the standard approach.
- **Concepts log.** In Claude Code, concepts you struggled with are saved to `~/.claude/econ-learning/concepts.md`. Claude checks you on them again when they come up in later sessions.
- **Handoff.** Claude writes code only after you've settled the reasoning. It works alongside the companion `econ-data-pipeline` skill for implementation checks if you have it installed.

## Installation

**Claude Code:** clone the repo into your skills directory:

```bash
git clone https://github.com/Snailfarts24/econ-learning.git ~/.claude/skills/econ-learning
```

**Claude.ai:** zip the folder, then upload it under Settings → Capabilities → Skills.

## Usage

Run `/econ-learning`, or ask Claude to "turn on learning mode." Once it's on, it stays on for the session.

| Say | Effect |
|---|---|
| `skip` | Pass one checkpoint; Claude picks a reasonable choice and moves on |
| `hint` | Climb one rung of the hint ladder |
| `just do it` / `learning off` | Pause learning mode |
| `learning on` | Resume |

## Sources

The stage guidance draws on Angrist & Pischke (2009), Ashworth, Berry & Bueno de Mesquita (2021), Bastani et al. (2025), Deryugina, Einav & van Dijk, Gentzkow & Shapiro (2014), Ludwig, Kling & Mullainathan (2011), Olken (2015), Pischke (2009), Shapiro (2026), Sinha & Kapur (2021), and Varian (1997). Full citations are in [`SKILL.md`](SKILL.md#sources).
