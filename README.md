# pessi-mystic — a relentless pessimism plugin for Claude Code

> A **Claude Code plugin** (skill + slash commands + a parallel failure-scout agent) that turns Claude into a **pre-mortem engine**: it understands what your project, idea, or codebase actually is, then enumerates *every* way it can fail — worst cases followed to their realistic end, across a full taxonomy so nothing is skipped, ranked by likelihood and impact.

**Topics:** `claude-code` · `claude-code-plugin` · `claude` · `pessimism` · `pre-mortem` · `risk-analysis` · `failure-modes` · `fmea` · `red-team` · `worst-case` · `devils-advocate`

> First it knows. Then it dooms.

## Why this exists

Optimism is the default everywhere: plans are written by people who want them to work, code by people who believe it's correct, ideas by people already imagining the win. That bias is invisible from the inside, and it's exactly where disasters hide. `pessi-mystic` is the deliberate counterweight — the one voice in the room that assumes failure and goes looking for it, methodically, until every plausible way the thing dies is on the table.

Two things make a pessimist actually useful, and this plugin is built around both:

- **It understands before it attacks.** Generic doom ("it might not scale") is noise. Real pessimism is specific — it cites *your* file, *your* assumption, *your* dependency. So the plugin always comprehends the target first; it doesn't stumble when it doesn't yet know the project, it investigates.
- **It doesn't miss anything.** The risk you don't think of is the one that gets you. Under the hood is a dense taxonomy of failure dimensions and probing questions, walked every time, so coverage doesn't collapse under pressure.

## Core behaviors

- **Comprehend first** — reads the repo (or asks a couple of sharp questions) and restates the target before judging it. No blind prophecy.
- **Pure doom, by design** — it names what breaks and what the worst case is. It does **not** offer fixes, mitigations, or reassurance. That's your job (or plain Claude's).
- **Leaves nothing unexamined** — walks a full failure taxonomy (technical, data, security, dependencies, operational, product, people, external, assumptions, tail risks); every dimension is either a finding or an explicit one-line dismissal.
- **Follows failures to the bottom** — chains first-order failures to their worst *realistic* end-state ("…and then what?"), including correlated failures and worst-possible timing.
- **Ranks by likelihood × impact** — worst-first, with rare-but-catastrophic tail risks flagged explicitly instead of rounded to zero.
- **Scales to the target** — a one-liner gets a single compact pass; a real codebase gets parallel `doom-scout` agents, one per failure cluster, merged.
- **Plain, not theatrical** — direct and specific. The name is wordplay; the behavior is rigor. No doom-prophet voice, no emoji.

## Install

```
/plugin marketplace add emircbngl/claude-pessi-mystic
/plugin install pessi-mystic
```

Then restart Claude Code. (To try it locally before publishing, run `/plugin marketplace add` with the absolute path to this folder instead of the GitHub slug.)

> Forking or rehosting? Update the `emircbngl/claude-pessi-mystic` slug in `.claude-plugin/marketplace.json` and `.claude-plugin/plugin.json` to your own.

## Commands

| Command | What it does |
|---|---|
| `/premortem [target]` | Assume it already failed catastrophically — work backward through every failure dimension to explain how it died. The full, exhaustive pre-mortem (fans out to `doom-scout`s on real projects). |
| `/doom [target]` | Quick pessimistic take: worst cases and failure modes for a smaller idea, snippet, or decision. The everyday workhorse. |
| `/worst-case [decision]` | Take one decision or plan and follow it to its worst realistic end-state, chain by chain. |
| `/audit` | Point it at the current codebase — comprehend it from the files, then produce a grounded, exhaustive doom report. |

The skill also activates automatically when you say things like *"what could go wrong with this?"*, *"tear my plan apart"*, *"red team this"*, or *"what am I missing?"* — no command required.

## How it works

1. **Comprehend** — figures out what the target is and what "success" would mean (reads README/manifests/entry points/git history, or asks the minimum questions). It won't produce a single failure claim until it can restate the thing accurately.
2. **Sweep the taxonomy** — walks every failure dimension via dense reference checklists, so nothing is silently skipped. Small target → one pass; real target → parallel `doom-scout` agents per cluster, then merged.
3. **Project to the worst realistic end** — chains each failure forward to concrete damage, with worst-possible timing and correlated failures.
4. **Rank & report** — orders the doom worst-first by likelihood × impact, flags catastrophic tail risks explicitly, and ends with a coverage sweep proving every dimension was examined or explicitly dismissed.

## What this is NOT

- **Not a planner or a fixer.** It will not tell you how to prevent any of this. It is intentionally one-sided.
- **Not a balanced advisor.** It is a counterweight to optimism, meant to be used *alongside* normal Claude — read its report, then go solve the problems yourself.
- **Not a doom-prophet act.** No mystic persona, no theatrics. Just a thorough, grounded map of the downside.

Use it precisely *because* it only shows the bad side. That's the value.

## Project layout

```
pessi-mystic/
├── .claude-plugin/{plugin.json, marketplace.json}
├── skills/pessimist/SKILL.md            # the doctrine: comprehend → doom, pure & exhaustive
│   └── references/                      # the heart: dense failure-question banks
│       ├── comprehension.md             # understand before attacking (anti-stumble)
│       ├── failure-taxonomy.md          # the master checklist + fan-out clusters
│       ├── worst-case-projection.md     # chaining to the worst realistic end
│       ├── likelihood-impact.md         # ranking + the tail trap
│       ├── doom-report-format.md        # the output schema
│       └── *-failures.md / tail-risks.md / general-idea-failures.md  # per-dimension banks
├── agents/doom-scout.md                 # parallel single-dimension failure hunter
└── commands/                            # /premortem, /doom, /worst-case, /audit
```

## No hooks, no state — on purpose

Unlike some plugins, this one ships **no hooks** and keeps **no state file**. Pessimism is a tool you reach for deliberately, not an always-on mood — an automatic doom-injector would just get in the way of normal work. And every invocation starts fresh: there's no risk ledger to maintain or drift out of date. You point it at something, it tears that thing apart, and it's done.

## Star history

<a href="https://star-history.com/#emircbngl/claude-pessi-mystic&Date">
  <img src="https://api.star-history.com/svg?repos=emircbngl/claude-pessi-mystic&type=Date" alt="Star history chart for emircbngl/claude-pessi-mystic" width="640">
</a>

## License

MIT — see [LICENSE](LICENSE).
