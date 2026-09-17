# Streakly Comeback Prototype — Triad Working Session

*Attendees: Erica (PM), Raj (Eng), Lena (Design) · Duration: 30 min*

## Context Going In

The prototype (`prototype/index.html`) has been through three rounds of testing so far — a heuristic walkthrough, an in-character interview round (Priya, Tom, Amara), and a tone/feature pass (PR countdown, push-notification entry point). All testing to date has been Claude role-playing against the interview profiles, **not real usability sessions** — that distinction matters for what this meeting can and can't decide. Full history: `01-orient/change_log.md`. Full brief and locked decisions: `docs/pm-brief.md`.

## Pre-Read (send before the session)

- `prototype/index.html` — open in a browser, click through once
- `docs/pm-brief.md` — locked decisions + what's explicitly out of scope
- `01-orient/change_log.md` — the three rounds of changes and why

## Agenda (30 min)

| Time | What |
|---|---|
| 0:00–0:03 | Framing: what's been tested, what changed each round, what this session needs to produce |
| 0:03–0:15 | Live walkthrough of all 5 screens (lock screen/notification → comeback screen → freeze claimed → comeback lesson → completion), narrating what changed and which interview finding drove it |
| 0:15–0:24 | Discussion (see questions below) |
| 0:24–0:29 | Walk through decisions needed and land where we can |
| 0:29–0:30 | Confirm owner + deadline for the post-session alignment doc |

## What to Show

The live, clickable prototype — all 5 screens, including both branches of the 14-day/20-day comeback-lesson toggle, and the full loop from the push notification through to completion.

## Questions to Ask

**For Raj (feasibility):**
- Do we already track last-app-open date and historical best streak, or does this need new data plumbing? (Constraint per `pm-brief.md`: no new integrations.)
- Is the streak-freeze logic as scoped — free, one-tap, one use per break event, offered on next app open — straightforward, or does it need new state tracking?
- If the push notification became real, is that comparable effort to the in-app screens, or a separate, bigger workstream (send logic, timing, notification infra)?

**For Lena (design/brand fit):**
- Does the tone direction — PR language, the streak-journey milestone strip, confetti, the "silly"/playful copy — feel like a real direction for Streakly's brand voice, or a one-off for this screen?
- Any concerns with the notification's tone as an entry point?
- Is Coral Sunrise still the right visual system now that the tone has shifted more playful, or does the palette need a second look?

**For both:**
- Everything tested so far has been heuristic/role-play, not real users. What needs to be true before this goes in front of actual usability participants?

## Decisions to Walk Out With

1. **Streak-freeze eligibility/trigger policy** — ratify the current proposal, or flag what needs to change, based on Raj's feasibility read.
2. **Notification scope call** — decide whether the push-notification exploration becomes a tracked, in-scope workstream with its own brief, or stays a parked exploration for now. (Note: `pm-brief.md` currently still lists the notification as out of scope even though the prototype now includes one — this session is the moment to resolve that mismatch, one way or the other.)
3. **Design-system fit** — Lena's call on whether the tone rework is ready to treat as the direction, or needs a dedicated design pass first.
4. **Next step** — agree whether this moves to real usability testing next, and who owns scheduling it.

---

# Post-Session Alignment Doc (template)

*Fill in and save as its own file after the session — e.g. `03-build/triad-alignment-YYYY-MM-DD.md`.*

## Attendees & Date

- Date: ___
- Attendees: ___

## Decisions Made

| Decision | Outcome | Owner | Status |
|---|---|---|---|
| Streak-freeze eligibility/trigger policy | ___ | ___ | ___ |
| Notification scope | ___ | ___ | ___ |
| Design-system fit for tone rework | ___ | ___ | ___ |
| Next step (usability testing) | ___ | ___ | ___ |

## Eng Feasibility Notes (Raj)

- Data already available vs. needed: ___
- Streak-freeze logic complexity: ___
- Notification workstream sizing (if applicable): ___
- Other technical flags: ___

## Design Notes (Lena)

- Brand/tone fit: ___
- Visual system (palette/interaction) concerns: ___
- Notification tone reaction: ___
- Other design flags: ___

## Open Items Carried Forward

| Item | Why still open | Next step | Owner |
|---|---|---|---|
| ___ | ___ | ___ | ___ |

## Next Step

- ___

*After filling this in, log a summary entry to `01-orient/change_log.md` per this workspace's established pattern.*
