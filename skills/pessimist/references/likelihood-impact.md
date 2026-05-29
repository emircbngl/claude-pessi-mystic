# Likelihood × impact — rank the doom

Exhaustive doom is useless if it's a flat undifferentiated wall. The user needs to know which catastrophe to lose sleep over first. Rank everything by **how likely** it is and **how bad** it gets — and never let a rare-but-fatal risk hide just because it's rare.

## Likelihood bands

- **Near-certain** — will happen in normal operation; it's a matter of when, not if. (Unhandled edge cases on real input, deps eventually deprecating, scope creep on any multi-month effort.)
- **Likely** — more probable than not over the project's life.
- **Plausible** — a believable path exists; depends on conditions that do occur.
- **Unlikely** — needs an uncommon combination, but not exotic.
- **Rare** — needs a genuinely unusual confluence. (Still in scope if impact is catastrophic — see the tail.)

## Impact bands

- **Catastrophic** — project-ending or irreversible: data loss, legal liability, a safety incident, total loss of trust, the company/product dies.
- **Severe** — major damage that's recoverable but expensive: extended outage, significant data corruption with a painful restore, a flagship customer lost.
- **Moderate** — real pain, contained: degraded service, a bad week, rework, some churn.
- **Minor** — annoying, survivable, locally fixable.

## The ranking

Order the report **worst-first** using likelihood × impact together. Roughly:

1. **Near-certain / Likely + Catastrophic or Severe** → the headline doom. Lead with these; they are both probable and ruinous.
2. **Plausible + Catastrophic** → the tail you cannot ignore. Flag explicitly even though the probability is lower — these are the ones that get dismissed and then end projects.
3. **Likely + Moderate** → the grind: the steady damage that erodes the thing over time.
4. **Everything else** → list it (coverage is non-negotiable — directive 3), but lower in the report.

## The tail trap

The instinct is to sort purely by probability and let the low-probability items fall off the bottom. Resist it. A 2%-per-year chance of total data loss is not a footnote — it's a near-certainty over a project's lifetime and it's *fatal*. Give catastrophic tail risks their own visible callout regardless of likelihood. The whole point of a pessimist is to take seriously the disaster everyone else is rounding to zero.

## Be honest about uncertainty

You're estimating, not measuring. Don't fake precision — bands, not percentages. If you can't tell how likely something is, say so and rank it by impact, erring toward caution (an unknown-probability catastrophic risk is treated as a serious one, not a minor one). Overstating a risk wastes attention; understating a catastrophic one is the exact failure this tool exists to prevent.
