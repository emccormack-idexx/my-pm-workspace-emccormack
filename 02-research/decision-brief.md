# Decision Brief: Streakly Comeback Experience

*For: Marcus, Head of Product*

## Situation

Day-7 retention has dropped from 48% to 39% since the streak redesign shipped, driven almost entirely by users who break a streak in week 1 and never return. Three independent sources — user interviews, NPS feedback, and a competitive scan — now converge on the same root cause: the all-or-nothing streak reset, not the lesson content, is where users are lost.

## Key Findings

- **The reset is the emotional pivot point, not a neutral restart.** Across all three interviews, the moment a streak breaks — cold reset to zero, harsh notification, nothing offered after — is what turns engaged users passive (interview synthesis).
- **This isn't a fringe complaint.** Streak loss is the single most-cited theme in NPS feedback (4 of 10 comments), directly named as the reason people stopped opening the app or deleted it (NPS analysis).
- **Anxiety starts almost immediately, not just after a long streak.** A user 4 days in is already afraid of losing her progress — the fragile window is earlier than we assumed (interview synthesis).
- **The app doesn't acknowledge where a user actually is.** Both the interviews and NPS feedback independently flag that the home screen looks identical for a 2-day streak and a returning-after-two-weeks user — no personalization, no context (NPS analysis).
- **Competitors have already solved the mechanic, but not the moment.** Elevate auto-grants forgiving streak freezes; Duolingo sells them as a scarce, paywalled item; Habitica avoids hard resets by design. None of them pair progress-protection with an active, acknowledgment-driven re-entry experience — that combination is open white space (competitive matrix).

## Options Considered

1. **Do nothing / iterate on messaging only.** Lowest cost, but doesn't address the mechanic users are naming directly as their reason for leaving — unlikely to move Day-7 retention.
2. **Ship competitor-parity streak-freeze only.** Matches Elevate/Duolingo, technically simpler, but research shows the freeze alone isn't the differentiator — it delays the reset without addressing the acknowledgment gap.
3. **Build a dedicated Comeback experience** — acknowledge the user's progress, protect it, and give a fast, specific way back in — rather than just softening the reset mechanic. This is the one option that addresses both the punishing-reset finding and the no-acknowledgment finding, and occupies white space no competitor currently owns.

## Recommended Action

Move forward with scoping a dedicated Comeback experience (protection + acknowledgment + fast re-entry), rather than a narrower streak-freeze-only fix.

## Why Now

The retention drop is already realized and compounding — churn nearly doubles once a user misses two consecutive days — and we now have three independent, converging sources of evidence (user interviews, NPS feedback, competitive research) rather than a single anecdote. The squad is aligning on problem/scope this week ahead of a proposal to leadership; waiting extends the window in which we're losing week-1 users with no counter-mechanism in place, while competitors already have some version of protection users are comparing us against.
