# Comprehension — understand the target before you attack it

The most important rule in this skill. Pessimism applied to a thing you don't understand is just generic noise, and noise is worse than silence — it buries the real risks. **First you know. Then you doom.** This file is how you stop stumbling when you don't yet know what the project is.

## The bar you must clear

You may not produce a single failure claim until you can **restate the target accurately in your own words**: what it is, what it's trying to do, who it's for, and what "working" would mean. If you can't do that, you are still in comprehension, not pessimism.

## The core question

Before anything else: **"What exactly is this, and what would it mean for it to succeed?"** You can't enumerate failure until you know what success looks like — every failure is just a success condition negated.

## If the target is a codebase / repo

Read, in roughly this order, until the picture is clear (don't read everything — read until you can restate it):

- **README / docs** — the stated purpose, scope, audience, claims.
- **Manifests** — `package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `requirements.txt`, etc. → language, framework, dependencies, scripts, entry points.
- **Entry points & top-level structure** — `main`, `index`, `app`, route definitions, CLI definitions; the directory layout.
- **Config & deploy** — env vars, `.env.example`, Dockerfiles, CI workflows, infra-as-code, deploy scripts → how it runs and ships.
- **Tests** — what's covered tells you what the authors fear; what's *not* covered tells you where to aim.
- **Git history** — recent commits, churn hotspots, reverts, "fix" commits clustering around a file → where pain already lives. (`git log --oneline -20`, `git log --stat`.)
- **Dependencies** — what's pulled in, how old, how maintained.

Use Read/Glob/Grep/Bash (read-only) for this. If something is genuinely unknowable from the repo (intended scale, real user load, deployment target, business stakes), ask — don't invent it.

## If the target is a raw idea / plan / decision

Ask the **minimum** targeted questions to ground the doom. Prioritize:

- **Goal** — what outcome is this supposed to produce? What problem does it solve?
- **Scope & stage** — napkin idea, prototype, or shipping? How big, how committed already?
- **Users / stakeholders** — who has to adopt, approve, fund, or maintain it?
- **Constraints** — budget, deadline, team size, tech, regulatory, reputational.
- **Success criteria** — how would they know it worked? (Negate this for the failure surface.)
- **Reversibility** — if it goes wrong, how hard is it to undo? (Cheap-to-reverse and catastrophic-to-reverse are very different doom profiles.)

Ask only what you can't reasonably infer. Two or three sharp questions beat an interrogation. If the user gave enough to proceed, proceed.

## When you genuinely can't fully comprehend

Sometimes you won't get complete information (the user is vague, the repo is huge, the idea is half-formed). Don't stall and don't fake confidence. Instead:

- Comprehend as much as you can, and **state your working understanding explicitly** ("I'm reading this as a B2B billing service that…"). This lets the user correct you before you waste effort dooming the wrong thing.
- Make your **assumptions visible** and route them to `assumption-failures.md` — an unverified assumption is itself a failure vector.
- Scope the doom to what you understand, and name what you couldn't assess and why.

## Stop condition

Comprehension is done when you can restate the target and name its success conditions. The moment you can, stop investigating and start attacking. Don't over-research — endless recon is just procrastination in a lab coat, and the doom is where the value is.
