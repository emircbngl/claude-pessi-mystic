---
description: Point the pessimist at the current codebase/working directory — comprehend it from the files, then produce a grounded, exhaustive doom report.
argument-hint: [optional path or subsystem to focus on]
---

Read the `pessimist` skill, then audit the current project for everything that can go wrong.

Focus: $ARGUMENTS
(If empty, audit the whole working directory. If a path/subsystem is given, scope to it.)

1. **Comprehend from the files** (`references/comprehension.md`): read the README, manifests, entry points, config, tests, dependencies, and recent git history (`git log`). Restate what this project is and what "working" means before judging it.
2. **Sweep the full taxonomy** (`references/failure-taxonomy.md`), dispatching `doom-scout` subagents in parallel per cluster for anything more than trivial — each grinding its dimension's reference bank against the actual code.
3. **Ground every finding in real artifacts** — cite specific files, functions, dependencies, and config. No generic warnings; if a line would be true of any repo, sharpen or cut it.
4. **Project to worst realistic outcomes** (`references/worst-case-projection.md`) and **rank by likelihood × impact** (`references/likelihood-impact.md`).
5. **Deliver the full doom report** (`references/doom-report-format.md`) with the coverage sweep proving every dimension was examined or explicitly dismissed.

Pure doom: name what breaks, never how to fix it.
