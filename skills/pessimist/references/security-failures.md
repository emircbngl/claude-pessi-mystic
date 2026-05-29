# Security failures

Assume an adversary who is patient, automated, and smarter than the happy-path design. Security failures are catastrophic (breach, exfiltration, legal liability, total trust loss) and often invisible until exploited. Ask: **"how would someone abuse this on purpose?"** and **"if this were already compromised, would we know?"**

## Authentication & authorization
- Can a request act without proving who it is? Are there unauthenticated endpoints that shouldn't be?
- Authorization: can user A read/modify user B's data by changing an ID (IDOR)? Is access checked on every path, or only in the UI?
- Are there privilege escalation paths — a normal user reaching admin actions, a tenant reaching another tenant's data?
- Session/token handling: predictable tokens, no expiry, no revocation, tokens in URLs/logs, missing CSRF protection?
- Default/weak/shared credentials? A backdoor "admin/admin" left in? Password reset that leaks or can be hijacked?

## Injection & input handling
- SQL/NoSQL injection — is any query built by string concatenation with user input?
- Command injection — does user input reach a shell, `eval`, a template, a deserializer, a file path?
- XSS — is user content rendered without escaping? Stored XSS that persists and hits every viewer?
- SSRF — can a user make the server fetch an arbitrary URL (cloud metadata endpoint, internal services)?
- Path traversal, XXE, prototype pollution, regex DoS — does untrusted input reach somewhere it can subvert?
- Is input validated/escaped at the boundary, or trusted because "it comes from our frontend"?

## Secrets & exposure
- Are credentials/keys committed to the repo, in `.env` files, in history, in client-side bundles, in CI logs?
- Do "placeholder" secrets in examples turn out to be real? Are any secrets shared across environments?
- Is anything sensitive leaking through error messages, stack traces, debug endpoints, verbose logs, or response headers?
- Are internal/admin endpoints reachable from the internet? Is there a debug mode that's on in prod?

## Supply chain & dependencies
- Could a compromised or typosquatted dependency run arbitrary code at install or runtime? (See `dependency-supply-chain.md`.)
- Are dependencies pinned and verified, or pulling "latest" from wherever? Is the lockfile trusted?
- Does CI/CD have credentials that, if the pipeline is compromised, hand over production?
- Are there known CVEs in the current dependency versions? (Use WebSearch to check notable ones.)

## Crypto, transport & config
- Is anything rolling its own crypto, using weak/old algorithms, hardcoded IVs/keys, or `Math.random()` for tokens?
- Is TLS enforced everywhere, or is there a plaintext path? Are certs validated, or is verification disabled "to make it work"?
- Are security headers, CORS, and cookie flags (HttpOnly, Secure, SameSite) set, or wide open?
- Are cloud resources (buckets, DBs, dashboards) public by default or misconfigured open?

## Abuse & operational security
- Is there rate limiting? What stops credential stuffing, scraping, spam, or resource-exhaustion abuse?
- Can the feature be weaponized to attack others (open redirect, email/SMS relay, amplification)?
- Is there an audit trail? If breached, can you even tell what was accessed and when?
- What's the blast radius of one compromised employee laptop, API key, or CI token — does it reach everything?
