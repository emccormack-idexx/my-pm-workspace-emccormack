# CLAUDE.md — Persistent Memory

> The file Claude Code reads at the start of every session. Short, true, current — the difference between Claude building blind and building with context.

## The Product

*What it does, for whom, current focus.*

Working scenario: the **Streakly Comeback experience** — recovering Day-7 retention for Streakly, a consumer habit + micro-learning app whose Day-7 retention slipped from 48% to 39% after a v2 redesign.

**Core metric:** Day-7 retention.

**Key tension:** breaking a streak feels like punishment with no way back in — cold reset to zero, harsh "you lost your streak" notification, nothing offered afterward. Open question: is the root cause the reset mechanic, the notification tone/timing, or both.

**Solution direction:** decided. Marcus approved investing in a dedicated Comeback experience — protection + acknowledgment + fast re-entry — over a narrower streak-freeze-only fix (see `02-research/decision-brief.md`). The Comeback screen concept is the agreed direction and now has a working prototype (`prototype/index.html`, brief in `docs/pm-brief.md`).

**Still open:** specific implementation policy — streak-freeze trigger/eligibility rules are still a proposal, not yet ratified by the squad or signed off by Marcus (see `docs/pm-brief.md`, "Not in Scope"). Non-goals and success-metric targets for the broader Comeback experience also remain undefined (see `01-orient/project.md`).

_(Replace this section with your own product if you're bringing a real situation from your day job.)_

## My Role & Squad

- **Erica** — Product Manager
- **Squad:** Product Engagement
- **Also on the squad:** Marcus (Head of Product), Raj (Engineer), Lena (Designer)

## How I Want Claude to Work With Me

- **Interview first:** ask clarifying questions before building.
- **Tone:** Direct & concise. Short, to-the-point answers — skip preamble and hedging.
- **Defaults:**
  - Ask before building — interview/clarify scope before writing or generating an artifact.
  - Cite sources — tag claims with where they came from (interview, doc, dataset) rather than stating them as fact.
  - Flag assumptions — call out explicitly when inferring something not stated, rather than folding it silently into the answer.
- **Never:**
  - Never treat streak-freeze trigger/eligibility policy as final — it's still a proposal pending squad/Marcus sign-off (see `docs/pm-brief.md`), even though the Comeback screen concept itself is decided.
  - Never invent data/metrics — no fabricated NPS scores, retention numbers, or quotes; only use what's in the workspace or explicitly given.
  - Never speak for the squad — don't write copy as if it's Marcus's, Raj's, or Lena's stated opinion unless it's documented.
  - Never skip the interview step — never generate an artifact for a new module without first asking clarifying questions.

## Glossary (my product's words)

| Term | Meaning |
|------|---------|
| **Streakly** | Consumer habit + micro-learning app; users complete a 5-min daily lesson on a chosen track. The streak is the core habit loop. |
| **Streak** | Consecutive days of daily-lesson completion; the core engagement mechanic. |
| **v2 redesign** | The streak-system redesign after which Day-7 retention fell from 48% → 39%. |
| **Day-7 retention** | Primary success metric for this initiative; % of users still active 7 days after signup/start. |
| **Streak reset** | The mechanic where missing a day resets the streak counter to zero with no acknowledgment of prior progress — suspected root cause of disengagement. |
| **Week-1 streak-breaker** | A user who breaks their streak within their first week; this segment shows the sharpest Day-7 retention decline. |
| **Comeback experience** | The overall initiative/workstream to give users a graceful path back in after a streak break, instead of a cold reset. Solution direction decided: a dedicated Comeback screen (protection + acknowledgment + fast re-entry), approved by Marcus per `02-research/decision-brief.md`. |
| **Comeback screen** | The agreed-direction screen shown when a user breaks a streak, originally sketched by Lena. Includes a best-streak stat, a comeback lesson, and a streak-freeze offer. Prototyped in `prototype/index.html` (brief: `docs/pm-brief.md`); freeze trigger/eligibility policy is still a proposal pending squad sign-off. |
| **Best-streak stat** | Concept: showing a user's historical best streak instead of just resetting the visible counter to zero. |
| **Comeback lesson** | Concept: a one-time, 60-second lesson offered after a break to rebuild momentum. |
| **Streak-freeze** | Concept: a one-tap option to protect a rebuilt streak from breaking again; also a named competitor feature (Duolingo) that a churned user cited by name. |
| **Comeback Coach** | Name used in the README for the eventual agent stack this workspace builds toward (Module 6) — not yet built. |
