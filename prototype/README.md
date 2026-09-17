# Streakly Comeback Screen — Prototype

Open `index.html` in a browser. It's a self-contained, clickable mobile-frame prototype — no build step, no dependencies.

**Prototype controls** (dark bar above the phone, not part of the product UI): toggle "days since last app open" to see both comeback-lesson branches, and reset the flow.

## PM Brief

**Target user:** 24-year-old who hit a 12-day streak, missed two days, and has not opened the app since (modeled on the "Tom R." interview profile in [`../02-research/interview-synthesis.md`](../02-research/interview-synthesis.md)).

**Job to be done:** Get back in without feeling they lost everything.

**Feature set:** Personalized Comeback screen, best-streak stat, one 60-second comeback lesson, one-tap streak-freeze offer.

**Constraint:** Use data Streakly already has. No new integrations.

**Grounding:** Builds on the direction Marcus approved in [`../02-research/decision-brief.md`](../02-research/decision-brief.md) — a dedicated Comeback experience (protection + acknowledgment + fast re-entry), not a streak-freeze-only fix.

## Key Decisions Made During the Interview

| Decision | Answer | Status |
|---|---|---|
| Streak-freeze trigger | Offered the first time a user breaks a streak, on their next app open | Proposal — unresolved policy per `project.md`, not yet ratified by the squad |
| Streak-freeze eligibility | Free, one-tap, one use per break event — no monthly allowance, no gem economy | Same status as above |
| Prototype scope | Starts at the Comeback screen; does not cover the streak-break notification (separate open question in `strategy.md`) | Locked for this prototype |
| Comeback-lesson personalization | Under 14 days since last open → continue prior track. 15+ days → generic "welcome back" lesson | Locked, set by Erica |
| 14-day threshold basis | Measured from last app open, not from the day the streak broke | Locked, set by Erica |
| Visual style | Coral Sunrise palette (kuler.ai): `#ff6b6b` primary, `#ffa07a` secondary, `#ffd93d` accent, `#fff9f5` background, `#ffffff` surface, `#2d2020` text | Locked, set by Erica |
| Test user / demo data | Modeled on the Tom R. interview profile; placeholder data only | Locked for this prototype |

## Not in Scope

- The streak-break notification (copy, tone, timing)
- Final streak-freeze eligibility policy — needs squad/Marcus sign-off before this is real product behavior
- Non-goals and success-metric targets for the broader Comeback experience (still undefined per `project.md`)

## Tone Reimagining (2026-09-16 update)

Screens 1 and 4 were reworked for a warmer, no-shame, upbeat tone (Peloton-style "PR" language, a streak-journey milestone strip, light confetti). Screen 3 (the lesson) was intentionally left calm and unchanged. Locked mechanics (freeze eligibility, 14-day threshold, palette) were not touched — this was a tone/visual pass only. Full details in [`../docs/pm-brief.md`](../docs/pm-brief.md).

Full brief: [`../docs/pm-brief.md`](../docs/pm-brief.md)
