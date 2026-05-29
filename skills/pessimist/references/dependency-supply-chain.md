# Dependency & supply-chain failures

Everything you didn't build is something you don't control and can't fix when it breaks. Every dependency is a bet that someone else stays up, stays compatible, stays maintained, and stays affordable. Ask of each one: **"what happens to us the day this changes or disappears?"**

## Third-party services & APIs
- What external APIs/services are load-bearing? What happens the day one is down, slow, or rate-limiting you?
- Do they have an SLA? Does it match what you're promising your own users? (You can't be more reliable than your hardest dependency.)
- What if they make a breaking change, deprecate the version you use, or change response shapes without notice?
- What if they change pricing, introduce quotas, or move a feature behind a higher tier?
- What if they ban your account, region, or use case — or get acquired/shut down?
- Is there a single API whose outage takes your whole product down? (Auth providers, payment, email, maps, an LLM API.)

## Packages & libraries
- Which dependencies are unmaintained (last commit years ago, single maintainer, open critical issues)?
- What's the transitive tree — how many packages do you *actually* trust, including the ones you've never heard of?
- What breaks on the next major version bump? Are you pinned, or floating toward a surprise?
- Is a critical feature resting on one small package that could be abandoned, yanked, or taken over?
- Are there known CVEs in the tree right now? (WebSearch the notable deps + "CVE" / "vulnerability".)
- Could a package be removed from the registry (left-pad), renamed, or relicensed out from under you?

## Licensing & legal
- Are any dependency licenses incompatible with how you ship (GPL/AGPL in a closed product, license changes like the SSPL/BSL relicensings)?
- Does anything require attribution, source disclosure, or commercial licensing you're not honoring?
- Did a key dependency recently change its license in a way that affects you?

## Version & compatibility hell
- Do two dependencies require conflicting versions of a shared transitive dependency?
- Is the runtime/language version you depend on approaching end-of-life or already unsupported?
- What forces a painful synchronized upgrade across many components at once?
- Does a security patch require a major version bump that breaks your code (so you're stuck choosing between insecure and broken)?

## Single points of failure & lock-in
- Where is there exactly one of something with no fallback — one provider, one region, one credential, one maintainer?
- How locked in are you? If this vendor doubles the price or fails, how many weeks/months to migrate off, and is it even possible?
- Does the whole thing assume a free tier / beta / promotional pricing that won't last?
- Is there a data-export path off each critical service, or is your data effectively hostage?
