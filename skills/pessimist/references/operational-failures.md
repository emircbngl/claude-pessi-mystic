# Operational failures

Code that passes tests still has to be deployed, observed, scaled, paid for, and resurrected at 3am by someone who didn't write it. Most outages are operational, not algorithmic. Ask: **"when this breaks in production, how do we find out, and how do we get it back?"**

## Deploy & rollback
- How does a deploy go wrong — half-deployed, wrong version, config mismatch, migration races the code?
- Is there a rollback? Has it ever been used? Can you roll back if the deploy included a non-reversible migration?
- Can old and new versions coexist during a rolling deploy without breaking each other?
- Is deploy a one-click repeatable process, or a tribal-knowledge ritual only one person can perform?
- What if a deploy needs to happen *during* an incident and the deploy pipeline is itself broken?

## Observability — the silent-failure killer
- If this breaks right now, would anyone know? How — an alert, or an angry customer?
- What's *not* monitored? The silent failures (jobs that stopped running, backups that stopped, a queue quietly backing up) are the ones that become disasters.
- Are there logs/metrics/traces to diagnose a problem, or will an incident be a blind guess?
- Are alerts actionable, or so noisy that real ones drown (alert fatigue → the page everyone ignores)?
- Can you tell the difference between "slow," "down," and "returning wrong answers"? The last is the hardest and worst.

## Capacity & cost
- What happens at peak — the launch spike, the viral moment, the batch job and the traffic peak colliding?
- Is there autoscaling? Can it scale *down* (or does idle cost balloon)? Can scaling itself fail or lag the spike?
- What's the runaway-cost scenario — an infinite loop calling a metered API, a log explosion, egress fees, a misconfigured instance left running?
- Could a bug or an attacker run up a catastrophic bill overnight? Are there spending limits/alerts?

## Resilience & recovery
- What's the disaster-recovery story? If the primary region/datacenter/account is lost, what's the RTO/RPO — and has it ever been tested?
- Are there runbooks, or does recovery depend on one person's memory? What if that person is unreachable?
- What's the single thing whose failure takes everything down (the load balancer, the DB, the auth service, DNS)?
- After an outage, can the system actually recover cleanly, or does it come back in a corrupted/inconsistent state?

## Config & environment drift
- How much lives in config/env that can be set wrong with no validation (a flipped flag, a wrong URL, a missing var)?
- Do staging and prod actually match, or do bugs hide in the gap?
- Are secrets/config rotated, and does rotation break things? What expires silently (certs, tokens, domains, cards on file)?
- Is there a "works until the cert/domain/credential expires in 90 days and nobody set a reminder" time bomb?

## On-call & operational burden
- Who carries the pager? Is the operational load sustainable, or is it a burnout engine (see `human-team-failures.md`)?
- Does every incident require the original author? Is operational knowledge written down or trapped in heads?
- How many manual steps does normal operation require — each one a chance for human error under pressure?
