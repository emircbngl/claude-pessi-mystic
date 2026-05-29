# Technical / correctness failures

Does the thing itself actually work — on real input, under real load, at the edges? Ask every question that fits; for each "yes, this could happen," chain it to its worst end (`worst-case-projection.md`).

## Correctness & edge cases
- What inputs break it? Empty, null, zero, negative, huge, unicode, emoji, malformed, deeply nested, duplicated?
- What's the off-by-one, the boundary at exactly the limit, the empty-collection case, the single-element case?
- What happens at the min/max of every numeric field? Overflow, underflow, precision loss, float rounding, division by zero?
- Where are values assumed non-null / present / well-formed that aren't guaranteed to be?
- What untested code path runs only in a rare branch — and is therefore wrong and nobody knows?
- Are there silent wrong answers (returns a plausible-but-incorrect result instead of erroring)? Those are worse than crashes.

## Concurrency, ordering & state
- What breaks if two requests/threads/jobs hit this at the same time? Race conditions, lost updates, double-processing?
- Is there shared mutable state without locking? A check-then-act that isn't atomic? A read-modify-write that can interleave?
- What if events arrive out of order, duplicated, or replayed? Is anything assumed to happen exactly once?
- Are there deadlocks, livelocks, or thundering-herd patterns under contention?
- Can the system end up in an inconsistent intermediate state if interrupted mid-operation (crash, kill, timeout) between two writes?
- Is idempotency assumed but not guaranteed (retries cause duplicate side effects: double charges, double emails)?

## Performance & scaling ceilings
- What's the hidden O(n²) (or worse) — the nested loop, the N+1 query, the per-item network call?
- What happens at 10×, 100×, 1000× the data/traffic the author tested with? Where's the first wall?
- What's unbounded — a queue, a cache, a list, a log, a retry, a recursion — that grows until it exhausts memory/disk?
- Is there a single bottleneck everything funnels through? A lock, a single worker, one DB, one node?
- Do latencies compound across a call chain? Does a slow dependency cascade into timeouts upstream?

## Resource exhaustion & failure handling
- File handles, sockets, DB connections, threads, memory — what leaks, and what happens when the pool is empty?
- What happens when the disk fills, memory runs out, or a quota is hit mid-operation?
- Are errors swallowed, logged-and-ignored, or caught too broadly (hiding the real failure)?
- On failure, does it fail safe or fail open? Does a crash leave locks held, files half-written, transactions open?
- Are retries bounded with backoff, or can they storm? Do timeouts exist at all, and are they sane?

## Environment, platform & time
- "Works on my machine" — what differs in prod: OS, arch, runtime version, env vars, file system, case sensitivity, line endings?
- Timezones, DST, leap seconds/years, clock skew, clock going backwards, dates before 1970 or after 2038?
- Locale, encoding, collation, number/date formatting, RTL text, character set assumptions?
- Network: what if it's slow, flaky, partitioned, behind a proxy, rate-limited, or the DNS/cert expires?
- What's hardcoded that shouldn't be (paths, URLs, limits, credentials, assumptions about the host)?

## Integration boundaries
- At every boundary (API, queue, DB, file, third party): what if it's down, slow, returns garbage, returns a different shape than expected, or changes without warning?
- Are response schemas validated, or trusted? What if a field is missing, renamed, or newly nullable?
- Is partial failure handled (call A succeeds, call B fails — now what state are you in)?
- Version skew: what if the client and server, or two services, are on different versions during a deploy?
