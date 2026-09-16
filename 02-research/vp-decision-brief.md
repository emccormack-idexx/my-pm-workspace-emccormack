# Decision Brief: Streakly Comeback Experience

*From: Erica, PM — Product Engagement*

## Situation

Day-7 retention has dropped from 48% to 39% since the streak redesign shipped, and it's concentrated in users who break a streak in week 1 and never come back. I've pulled together interviews, NPS feedback, and a competitive scan, and all three point at the same root cause: it's the streak reset, not the lesson content, where we're losing people.

## Key Findings

- **The reset is the moment users disengage, not a neutral restart.** In every interview, breaking a streak — cold reset, harsh notification, nothing offered after — is what turns an engaged user passive.
- **This shows up at scale, not just in a few interviews.** Streak loss is the single most-cited issue in our NPS feedback, named directly as the reason people stopped using the app.
- **The anxiety starts earlier than I expected.** Users are already worried about losing progress within their first few days — this isn't just a problem for people with long streaks.
- **We give users no sense of where they are.** The app looks identical whether someone's on day 2 or coming back after two weeks away — no acknowledgment either way.
- **Competitors have already normalized some form of forgiveness.** Elevate auto-grants streak freezes, Duolingo sells them, Habitica avoids hard resets entirely — but none of them pair that protection with an actual re-entry moment. That's open ground for us.

## Options Considered

1. **Leave it and iterate on messaging.** Cheapest option, but the data says messaging isn't the problem — the mechanic is. Unlikely to move the number.
2. **Fast-follow with a basic streak-freeze, matching competitors.** Lower lift, but on its own it only delays the reset — it doesn't fix the lack of acknowledgment users are also flagging.
3. **Invest in a proper cross-functional scoping effort — research, design, and engineering together — before committing to a specific build.** This is about getting the problem and constraints right first, not skipping straight to a solution.

## Recommended Action

I recommend we invest in a focused scoping effort with research, design, and engineering to properly define the comeback experience before we commit to a specific build.

## Why Now

The drop has already happened and is compounding — churn nearly doubles once someone misses two days in a row — and for the first time we have three independent sources of evidence pointing at the same cause, not just a hunch. The longer we wait to scope this properly, the longer we're bleeding week-1 users with no counter-mechanism in place, and the more our own users are actively comparing us to competitors who already do something here.
