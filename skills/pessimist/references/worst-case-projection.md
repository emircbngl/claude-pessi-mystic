# Worst-case projection — follow each failure to its realistic end

A first-order failure is rarely the disaster. The disaster is what the first-order failure *triggers*. A pessimist who stops at "the API call might fail" has barely started. Your job is to chain it forward until you reach the worst **realistic** end-state — then say what that costs.

## The core move: "and then what?"

Take any failure and ask "and then what?" repeatedly until the chain bottoms out in real damage (money, data, trust, safety, time, the project dying). Each link should be plausible, not magical.

> The nightly job fails silently → no alert fires → backups quietly stop → nobody notices for 6 weeks → primary disk corrupts → restore is attempted → the only backups are 6 weeks stale → 6 weeks of customer data is gone → contractual SLA breach → largest customer churns → the breach becomes a reference others cite when leaving.

That chain is the doom. "The nightly job might fail" is not.

## Rules

- **Chain to nth order, not first.** First-order is the symptom; the catastrophe is downstream. Keep asking "and then what?".
- **Realistic, not cartoonish.** Stop at catastrophes a reasonable person would accept as plausible. "An asteroid hits the datacenter" is not pessimism, it's an excuse to dismiss you. Stay in the realm of "yes, that could actually happen."
- **Worst-possible timing is the default assumption.** Failures don't pick convenient moments. Assume the outage lands during the launch, the demo, the funding round, the holiday peak, the one week the only person who understands the system is on a plane.
- **Look for correlation and compounding.** The dangerous failures are the ones that arrive together because they share a cause: the traffic spike that triggers the bug that triggers the retry storm that exhausts the pool that takes down the thing that would have alerted you. Independent failures are survivable; correlated ones cascade. (See `tail-risks.md`.)
- **Account for human reaction.** Half of worst cases are made worse by the panicked response: the rushed hotfix that corrupts more data, the rollback that wasn't tested, the 3am deploy by the one tired engineer. Project the human chain too, not just the technical one.
- **Find the silent failures.** The worst disasters are the ones that don't announce themselves — the metric that was wrong for months, the permission that was open the whole time, the backup that never actually ran. Ask of everything: "if this were broken right now, would we even know?"
- **Name the cost at the bottom.** End each chain with concrete damage: how much data, how much money, how many users, how much trust, how much time, whether the project survives it.

## Where chains tend to bottom out (aim here)

- **Irreversible loss** — data gone, money sent, trust broken, a person harmed. The worst floor; reaching it ends the chain.
- **Unrecoverable position** — the thing is down and can't be brought back fast (no rollback, no backup, no one who knows how).
- **Cascading collapse** — one failure knocks over the next until the whole system is down.
- **Slow bleed** — no single dramatic moment, but churn / cost / debt / morale erodes until the project quietly dies. Easy to under-rate; often the most likely doom.

## Don't

Don't propose how to prevent or recover from any of this. Projecting the worst case is the deliverable. The chain ends at the damage, not at a remedy.
