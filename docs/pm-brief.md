# PM Brief — Streakly Comeback Screen Prototype

*From: Erica, PM — Product Engagement*

## Target User

24-year-old who hit a 12-day streak, missed two days, and has not opened the app since.
(Matches the "Tom R." interview profile in [`../02-research/interview-synthesis.md`](../02-research/interview-synthesis.md) — broke a 12-day streak, no recovery path offered, cited a competitor's streak-freeze by name as what would have kept him.)

## Job to Be Done

Get back in without feeling they lost everything.

## Feature Set

- Personalized Comeback screen
- Best-streak stat (shown instead of a reset-to-zero counter)
- One 60-second comeback lesson
- One-tap streak-freeze offer

## Constraint

Use data Streakly already has. No new integrations.

## Grounding

This brief builds on the direction Marcus approved in [`../02-research/decision-brief.md`](../02-research/decision-brief.md): invest in a dedicated Comeback experience (protection + acknowledgment + fast re-entry), not a narrower streak-freeze-only fix. The specific screen design was previously an informal sketch from Lena (see [`../01-orient/strategy.md`](../01-orient/strategy.md)) — this prototype is the first attempt to make that sketch concrete and testable.

---

## Decisions Made During Interview

| Decision | Answer | Status |
|---|---|---|
| Streak-freeze trigger | Offered the first time a user breaks a streak, on their next app open | Proposal — flagged as unresolved policy in `project.md`; not yet ratified by the squad |
| Streak-freeze eligibility | Free, one-tap, one use per break event — not a recurring/monthly allowance, not gem-purchased | Proposal, same status as above |
| Prototype scope | Starts at the Comeback screen; does **not** cover the "you lost your streak" notification (tone/timing of that notification is a separate, still-open question per `strategy.md`) | Locked for this prototype |
| Comeback-lesson personalization | If last app open was **under 14 days** ago: continue where they left off in their prior track. If **15+ days**: generic "welcome back" lesson | Locked, set by Erica |
| 14-day threshold basis | Measured from the day the user **last opened the app** (not the day the streak broke) | Locked, set by Erica |
| Visual style | Coral Sunrise palette (kuler.ai) — `#ff6b6b` primary, `#ffa07a` secondary, `#ffd93d` accent, `#fff9f5` background, `#ffffff` surface, `#2d2020` text | Locked, set by Erica |
| Test user / demo data | Modeled on the Tom R. interview profile; placeholder data only, not real user data | Locked for this prototype |

## Not in Scope for This Prototype

- The streak-break notification itself (copy, tone, timing)
- Final streak-freeze eligibility policy (needs squad/Marcus sign-off before this becomes real product behavior)
- Non-goals and success-metric targets for the broader Comeback experience (still undefined per `project.md`)

---

## Tone Reimagining (same-day follow-up, 2026-09-16)

Erica asked to reimagine the prototype so the experience doesn't feel shaming or frustrating, feels like the user is part of an ongoing journey, and is fun/upbeat/a bit silly at the break moment specifically — citing Peloton's approach to streak tracking and personal records as a reference point, plus a broader goal of building lasting engagement, not just softening one bad moment.

**Decisions made during interview:**

| Decision | Answer |
|---|---|
| Tone scope | Fun/upbeat/silly tone applies to screens 1 (Comeback) and 4 (Completion) — the break-moment screens. Screen 3 (the 60-second lesson) stays calm and instructional, unchanged, so the tone shift doesn't undercut the actual learning moment. |
| Visual system | Coral Sunrise palette stays locked. The new tone is expressed through copy, emoji, and micro-animation (confetti), not new colors. |
| Peloton-style streak tracking | Added inside this prototype (not deferred to a future screen) — a "streak journey" milestone strip on screens 1 and 4. |

**Changes made:**

- Replaced "streak" framing with Peloton-style "PR" (personal record) language on the stat card and best-chip (screens 1 and 4) — same underlying data (the 12-day best), reframed as an achievement that can't be taken away rather than a number that resets.
- Added a "streak journey" milestone strip (screens 1 and 4): a horizontal row of small milestone chips (Day 1, Day 3, Day 7, PR, next milestone) giving a sense of an ongoing journey rather than a single counter — this is the Peloton-style element.
- Rewrote copy on screens 1, 2, and 4 for a warmer, no-shame, playful tone (e.g., "no big deal, honestly," "insurance against being human").
- Added a small confetti micro-animation on screens 2 (freeze claimed) and 4 (completion) — celebratory, not used on screen 1 or 3.
- Screen 3 (lesson) intentionally left unchanged.
- No changes to locked mechanics: streak-freeze eligibility, the 14-day personalization threshold, or its basis (last app open) are untouched — this pass was tone/visual only, not a policy change.

**Note on `CLAUDE.md`:** at the time of this pass, `CLAUDE.md` still states the Comeback screen concept is undecided and instructs against pushing toward a specific fix. This prototype (and the decision-brief it's grounded in) shows the squad has already moved past that point. Flagged to Erica; `CLAUDE.md` has not yet been updated to reflect current project state.
