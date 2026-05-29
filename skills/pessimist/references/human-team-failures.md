# Human & team failures

Projects are killed by people problems far more often than by hard technical ones. The code can be perfect and the project still dies because the one person who understood it left, or because nobody agreed on what "done" meant. Ask: **"how does this fail because of who's building and maintaining it, not what's being built?"**

## Bus factor & knowledge concentration
- Who is the *only* person who understands this? What happens the week they're on vacation, sick, or gone?
- Is critical knowledge written down, or trapped in one head, one chat thread, one person's memory?
- If the original author left tomorrow, could anyone else operate, debug, or extend this? How long to onboard a replacement?
- Are there parts everyone is afraid to touch because only one person "knows how it works" (and that person is busy/gone)?

## Maintenance & abandonment
- Who maintains this in 6 months, in 2 years? Is that resourced, or assumed?
- What happens when the interesting build phase ends and only the unglamorous maintenance remains — does anyone actually own it?
- Does this add permanent operational/maintenance load that no one budgeted for?
- Is this a side project / passion project that dies when its champion's attention moves on?

## Estimation & timelines
- How wrong is the estimate? (It's wrong. By how much, and what breaks when it slips?)
- What's the dependency on someone/something outside the team's control that can block everything?
- What gets cut when time runs short — tests, security, docs, error handling? (Those cuts are future failures.)
- Is there a hard external deadline (launch, contract, season, funding) that the schedule can't actually hit?
- Does the plan assume everyone works at peak with no interruptions, no sick days, no competing priorities?

## Communication & alignment
- Do the stakeholders actually agree on what's being built and why, or just assume they do?
- Where will "I thought you meant X" surface — between teams, between PM and eng, between you and the user?
- Is there a decision with no clear owner that will stall, or get re-litigated repeatedly?
- Who has the power to change scope/priorities midstream and blow up the plan?
- Are requirements written down, or living in a conversation someone will remember differently later?

## Process & quality erosion
- Is anyone reviewing this work, or does it ship unchecked? What slips through with no second set of eyes?
- Does documentation exist and stay current, or rot until it's actively misleading?
- Is there test coverage that will catch a regression, or will breakage be found by users in production?
- As the team grows/shrinks/changes, what conventions and context get lost?

## People sustainability
- Is the pace sustainable, or is this a burnout/turnover machine that loses its key people mid-flight?
- Does this rely on heroics — one person carrying the on-call, the crunch, the rescue — that won't last?
- What's the morale failure: the demoralizing rewrite, the death march, the project everyone quietly stops believing in?
