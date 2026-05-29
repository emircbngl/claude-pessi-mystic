# Doom report — the output format

How to deliver the verdict. Pure failure, ranked, grounded, no remedies. The format serves three masters: it proves you *understood* the thing, it proves you *covered* everything, and it puts the scariest credible failure first.

## Structure

### 1. What I'm dooming (one short paragraph)
Restate the target in your own words — what it is, what success means. This proves comprehension (directive 1) and lets the user catch a misunderstanding before reading the rest. If you're working from assumptions or partial information, say so here.

### 2. The headline doom (the worst credible failures, ranked)
The top few failures by likelihood × impact, worst-first. For each:

- **The failure** — named specifically, tied to something real in the target (a file, an assumption, a dependency, a user path).
- **The chain** — first-order → worst realistic end-state ("and then what?" to the bottom; see `worst-case-projection.md`).
- **Likelihood × impact** — the bands (see `likelihood-impact.md`).

Use a consistent compact shape per item — a short bolded title, the chain in a sentence or two, then the rating. Keep each tight; this is a list of catastrophes, not essays.

### 3. The tail (low-probability, catastrophic)
A separate, explicit callout for the rare-but-fatal — the disasters everyone rounds to zero. Don't let them hide inside the ranked list. (See the tail trap in `likelihood-impact.md`.)

### 4. Full coverage sweep
Proof that nothing was skipped. Walk every taxonomy dimension. For each, either a one-line failure (with a pointer up to a headline item if it's already covered) or an explicit one-line dismissal with a reason. This is the section that makes the report *exhaustive* rather than just *a list of what came to mind*. A compact table or a tight bulleted list per cluster works well:

> - **Technical:** [see headline #1, #3] + race on the shared counter under concurrent writes.
> - **Data:** no migration rollback path; a failed migration leaves the table half-converted.
> - **Security:** API keys read from a committed `.env.example` look like placeholders but two are real.
> - **Dependencies:** core feature rests on one unmaintained package, last commit 3 years ago.
> - **Operational:** dismissed — runs locally only, no production surface yet.
> - **Product/adoption:** the core flow assumes users will configure X; most won't.
> - **Human/team:** bus factor 1 — only the author understands the parser.
> - **External:** dismissed — no regulatory or platform-policy exposure.
> - **Assumptions:** the whole design assumes the upstream API stays free; it's in beta.
> - **Tail:** [see tail section].

### 5. The single worst thing (optional, when one dominates)
If one failure clearly outranks the rest, end by naming it in one sentence. The thing most likely to kill this. Leave the user staring at it.

## Rules for the whole report

- **No solutions, anywhere.** Not in an aside, not in a "you might consider", not implied. If a fix sneaks in, cut it. (Directive 2.)
- **Specific over generic, always.** Every claim cites the actual target. If a line would be equally true of any project, it's too vague — sharpen it or drop it.
- **Coverage is visible.** Section 4 is what distinguishes this from off-the-cuff worry. Never omit it on a real target. (On a one-line `/doom`, it can collapse to a compact sweep.)
- **Ranked, not flat.** Worst-first. The user should know what to fear most by the end of the first screen.
- **Plain, not theatrical.** No doom-prophet voice, no ominous styling, no emoji. The catastrophes carry themselves. (See SKILL.md "Voice".)
- **Scale the heft to the target.** A one-liner gets a few items and a compact sweep. A repo gets the full structure. Don't bury a small idea in ceremony, and don't under-cover a real system.
