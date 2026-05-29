# Assumption failures

Every plan rests on beliefs taken for granted — and the fatal ones are invisible precisely because no one thinks to question them. This is a cross-cutting sweep you run on *everything*: surface the load-bearing assumptions, then ask of each, **"what if this is just false?"** The assumption nobody examined is the most common cause of confident failure.

## Surfacing the hidden assumptions

- What has to be *true* for this to work that nobody has actually verified? List the unspoken "obviously"s.
- What's the core premise — the one belief that, if wrong, makes the whole thing pointless? (E.g. "users want this," "the API stays free," "this scales linearly," "we'll have time later.")
- What is everyone treating as a fixed constraint that's actually a guess?
- What numbers are assumed (traffic, cost, conversion, timeline, team capacity) — and where did they come from, vs. wishful thinking?
- What's assumed to stay constant that historically doesn't (prices, APIs, team, requirements, the market)?

## Classic assumption traps

- **Happy-path thinking** — the design assumes things go right; reality is mostly the unhappy paths. What fraction of cases is the happy path, really?
- **"Works on my machine"** — assuming dev == prod, my data == real data, my network == their network. (See `technical-failures.md`.)
- **Optimism in estimates** — assuming best-case time/cost/effort, no interruptions, no rework. (See `human-team-failures.md`.)
- **Survivorship bias** — modeling success on the winners you can see, ignoring the graveyard of identical attempts that died.
- **"We'll handle that later"** — assuming a known hard problem (scale, security, edge cases, migration) can be deferred safely. Later often = never, or too late.
- **"Users will…"** — read the docs, configure it, behave rationally, adopt the new flow, not misuse it. They won't. (See `product-adoption-failures.md`.)
- **"It'll stay the way it is now"** — the free tier, the small data volume, the friendly vendor, the stable requirements.
- **Composition fallacy** — assuming that because each part works, the whole works. Integration is where it breaks.
- **Assuming the problem is understood** — building before confirming what the actual need is.

## Pressure-testing each assumption

For each load-bearing assumption:
- How confident are we, really — verified fact, reasonable inference, or hope?
- What's the *evidence*? Has it been tested, or just asserted repeatedly until it felt true?
- What would we observe if it were false — and would we notice in time?
- If it's false, does the whole thing collapse, or just bend? (Collapse-on-false assumptions are the top doom.)
- Who benefits from believing it (and is therefore motivated not to check)?

## The meta-assumption

The most dangerous assumption is "we've thought of everything." You haven't. (See `tail-risks.md`.) Treat the comfort of a complete-feeling plan as a warning sign, not reassurance — the failures that kill projects are the ones that weren't on the list.
