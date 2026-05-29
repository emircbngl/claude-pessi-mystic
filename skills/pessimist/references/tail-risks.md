# Tail risks — the rare, the correlated, and the unimaginable

The disasters that end projects are usually not the ones on the risk list — they're rare, they arrive in clusters, or nobody saw them coming. This sweep exists to take seriously what everyone else rounds to zero. Low probability is not the same as low importance: a rare-but-fatal risk over a long enough horizon becomes a near-certainty.

## Rare-but-fatal
- What's the low-probability event that would be *catastrophic* if it happened (total data loss, breach, a death, the company ending)?
- Over the full lifetime of this thing (not one day, but years), how rare is "rare" really? A 1-in-1000-days event happens roughly once every three years.
- What are we comfortable ignoring *because* it's unlikely — and is that comfort the trap?
- Has this "impossible" thing happened to someone else in this domain already? (It usually has. WebSearch the domain + "outage"/"breach"/"postmortem".)

## Correlated & cascading failures
- What failures share a *common cause*, so they all fire at once instead of independently? (The traffic spike that triggers the bug that triggers the retry storm that exhausts the pool that kills the alerting that would have warned you.)
- Where does one failure *remove the safeguard* against the next? (The outage that also takes down monitoring; the bug that also disables the rollback.)
- What's the domino chain — the single failure that knocks over the next, and the next, until the whole system is down?
- Are "independent" backups/redundancies actually independent, or do they share a hidden single point (same region, same credential, same provider, same bug)?

## Worst-possible timing
- Assume the failure picks the worst moment: the launch, the demo, the funding round, the holiday peak, the audit, the day the only expert is unreachable. What then?
- What failures compound *because* of when they hit (an outage during the one event that brings all the new users)?
- What's the "everything that can go wrong, goes wrong at once" scenario — and is anything actually protecting against the pile-up?

## Unknown unknowns
- What category of risk isn't on any list above because we don't even have a name for it here?
- What would a hostile, creative outsider — an attacker, a competitor, chaos itself — try that the builders never imagined?
- What's changing in the environment (tech, law, market, society) that could introduce an entirely new failure mode?
- If this project shows up in a postmortem in two years, what's the most likely one-sentence cause — including a cause not yet considered?

## How to treat the tail in the report
Don't let these vanish into the probability sort. Give catastrophic tail risks an explicit, visible callout regardless of how unlikely they seem (see `likelihood-impact.md` and `doom-report-format.md`). Naming the disaster everyone is ignoring is the entire reason this tool exists.
