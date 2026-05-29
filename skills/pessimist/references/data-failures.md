# Data failures

Data loss and corruption is the archetypal worst case — it's often irreversible, frequently silent, and ends trust instantly. Treat data with maximum suspicion. For each risk, ask the killer question: **"if this were already wrong/gone right now, would we even know?"**

## Loss
- What single action can permanently destroy data? A bad `DELETE`/`DROP`, a wrong `WHERE`, a `rm`, an overwrite, a truncate?
- Is there anything between a user/operator and irreversible deletion (soft-delete, confirmation, undo window)? Or does one click/keystroke end it?
- Do backups exist? Have they ever been *restored* (an untested backup is not a backup)? How stale can they be? Where do they live — same disk/account/region that could die with the primary?
- Can a bug, a retry, or a race delete or overwrite data that looked safe?
- Is there a cascade delete that removes far more than intended?

## Corruption & integrity
- What writes partial/garbage data on crash, timeout, or interruption mid-write?
- Can two writers corrupt a record by interleaving (see concurrency in `technical-failures.md`)?
- Are there integrity constraints (foreign keys, uniqueness, checks), or can the data drift into impossible states?
- Can encoding/serialization round-trips silently mangle data (unicode, floats, dates, big integers, nulls)?
- Is corruption detectable (checksums, validation), or does it sit there until it surfaces as a wrong answer months later?

## Migrations & schema
- What if a migration fails halfway? Is the table left half-converted with no rollback? Is the app down until someone fixes it by hand?
- Is the migration tested against production-scale data, or just a tiny dev set (and so locks the table for hours / runs out of memory in prod)?
- Is there a backward-incompatible schema change deployed before the code that depends on it (or after the code that needs it)?
- Schema drift: do dev, staging, and prod actually match? Do two services disagree about the shape of shared data?
- Can old and new code run simultaneously during a rolling deploy and write incompatible shapes?

## Consistency & distribution
- Where is eventual consistency assumed to be immediate (read-after-write that reads stale)?
- What breaks under replication lag, split-brain, or a failover mid-transaction?
- Are there duplicate or orphaned records when a multi-step write partially fails?
- Is "the source of truth" actually single, or do caches/copies/denormalized fields drift out of sync?

## Privacy, retention & compliance
- Is PII/secret data stored where it shouldn't be — logs, analytics, error reports, backups, screenshots, URLs?
- Is sensitive data encrypted at rest and in transit? Or sitting in plaintext somewhere?
- Is data retained longer than allowed, or deleted before it legally/operationally should be?
- On a deletion/GDPR request, is the data *actually* gone everywhere (backups, replicas, caches, third parties), or only from the main table?
- Who can read the production data, and what's the blast radius if one of those accounts is compromised?
