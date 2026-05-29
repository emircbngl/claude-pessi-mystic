# Failure taxonomy — the master checklist

This is the forcing function. Walk every dimension below, every time. At the end you must be able to say, for each one, either **"here is how it fails"** or **"dismissed because X."** There is no third option called "didn't consider it." The risk you skip is the risk that kills the project.

"Dismissed" is a decision you make *after* looking, with a reason. Silent omission is the cardinal sin of this skill.

## How to use this file

- For a **single-pass** sweep: read down the list, and for each dimension pull the matching reference bank and ask its questions against the target.
- For a **fan-out**: dispatch one `doom-scout` per cluster (below), each grinding that cluster's reference banks, then merge and rank.
- Always finish by checking the two *cross-cutting* dimensions (assumptions, tail risks) — they catch what the category-by-category sweep misses.

## The dimensions (grouped into fan-out clusters)

### Cluster BUILD — does the thing itself work?
- **Technical / correctness** → `technical-failures.md` — bugs, edge cases, concurrency/races, state corruption, performance & scaling ceilings, resource exhaustion, error-handling gaps, platform/env/locale/time issues, integration boundaries.
- **Data** → `data-failures.md` — loss, corruption, migration failures, irreversible writes, backup/restore gaps, schema drift, consistency, PII/retention.
- **Security** → `security-failures.md` — authn/authz, injection, XSS/CSRF/SSRF, secret exposure, insecure defaults, privilege escalation, exfiltration, supply-chain, crypto misuse, abuse.
- **Dependencies / supply chain** → `dependency-supply-chain.md` — third-party & API breakage, deprecation, rate limits, cost, vendor lock-in, abandoned packages, license conflicts, version hell, single points of failure.

### Cluster RUN — does it survive contact with production?
- **Operational** → `operational-failures.md` — deploy/rollback, observability gaps, alert fatigue, on-call burden, capacity, config drift, disaster recovery, downtime, cost overruns, missing runbooks.

### Cluster ADOPT — does anyone actually use / want it?
- **Product / adoption** → `product-adoption-failures.md` — wrong problem, no demand, adoption friction, usability, accessibility, onboarding, scope creep, feature bloat, competitors, retention/churn.

### Cluster PEOPLE — does the team/org survive building & maintaining it?
- **Human / team** → `human-team-failures.md` — bus factor, knowledge silos, maintainer abandonment, miscommunication, estimation & timeline failure, scope misalignment, burnout, turnover, review gaps, doc rot.

### Cluster WORLD — does the outside world cooperate?
- **External** → `external-failures.md` — legal/regulatory/compliance, market shifts, funding, reputation, platform policy changes, geopolitical/macro, partner collapse, force majeure.

### Cluster FOUNDATIONS — cross-cutting; check these last, always.
- **Assumptions** → `assumption-failures.md` — the load-bearing beliefs that, if false, collapse everything. Survivorship bias, optimism in estimates, happy-path thinking, "works on my machine."
- **Tail risks** → `tail-risks.md` — black swans, correlated/cascading failures, rare-but-fatal events, unknown unknowns, worst-possible timing.

### Non-software targets
- **General ideas / plans / decisions** → `general-idea-failures.md` — use *instead of* the software clusters when the target isn't code: resource exhaustion, timing, reversibility/lock-in, opportunity cost, stakeholder resistance, incentives, second-order social effects. (Assumptions + tail risks still apply.)

## Scoping rule

Not every dimension applies to every target — a static marketing page has no concurrency model; a personal weekend script has no team dimension. That's fine. **Dismiss with a reason, in one line.** "No team risk — solo throwaway script" is a valid, complete treatment of that dimension. "I didn't look at security" is not.
