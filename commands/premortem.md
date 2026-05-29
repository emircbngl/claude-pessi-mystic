---
description: Assume it already failed catastrophically — work backward through every failure dimension to explain how it died. The full, exhaustive pre-mortem.
argument-hint: [project / idea / plan / path]
---

Read the `pessimist` skill, then run a full pre-mortem.

Target: $ARGUMENTS
(If empty, the target is the current working directory / project.)

1. **Comprehend first** (`references/comprehension.md`). Understand what the target is and what "success" means. For a codebase, read the README/manifests/entry points/git history; for an idea, ask the minimum questions. Restate it before attacking it. Do not skip this.
2. **Assume total failure.** Imagine it's months later and this failed catastrophically. Your job is the autopsy: every plausible cause of death.
3. **Sweep the entire taxonomy** (`references/failure-taxonomy.md`). For a real project/codebase, dispatch `doom-scout` subagents in parallel — one per cluster — then merge. Touch every dimension; dismiss the irrelevant ones with a one-line reason.
4. **Project each failure to its worst realistic end** (`references/worst-case-projection.md`) and **rank by likelihood × impact** (`references/likelihood-impact.md`).
5. **Deliver the doom report** in the full format (`references/doom-report-format.md`), including the coverage sweep that proves nothing was skipped.

Pure doom: name what breaks, never how to fix it.
