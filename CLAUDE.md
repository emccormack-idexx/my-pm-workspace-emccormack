# CLAUDE.md — Persistent Memory

> The file Claude Code reads at the start of every session. Short, true, current — the difference between Claude building blind and building with context.

## The Product

*What it does, for whom, current focus.*

Working scenario: the **Streakly Comeback experience** — recovering Day-7 retention for Streakly, a consumer habit + micro-learning app whose Day-7 retention slipped from 48% to 39% after a v2 redesign.

**Core metric:** Day-7 retention.

**Key tension:** breaking a streak feels like punishment with no way back in — cold reset to zero, harsh "you lost your streak" notification, nothing offered afterward. Open question: is the root cause the reset mechanic, the notification tone/timing, or both.

**Open decision:** aligning the Product Engagement squad on problem/scope for the Comeback experience before bringing a proposal to leadership. Solution direction (e.g., the Comeback screen concept) is intentionally not yet decided.

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
  - Never pick the solution direction — the Comeback screen concept is intentionally undecided; don't push toward a specific fix.
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
| **Comeback experience** | The overall initiative/workstream to give users a graceful path back in after a streak break, instead of a cold reset. Solution direction not yet decided. |
| **Comeback screen** | An early, informally-floated (Lena) concept — not an agreed direction — shown when a user breaks a streak. Would include a best-streak stat, a comeback lesson, and streak-freeze. |
| **Best-streak stat** | Concept: showing a user's historical best streak instead of just resetting the visible counter to zero. |
| **Comeback lesson** | Concept: a one-time, 60-second lesson offered after a break to rebuild momentum. |
| **Streak-freeze** | Concept: a one-tap option to protect a rebuilt streak from breaking again; also a named competitor feature (Duolingo) that a churned user cited by name. |
| **Comeback Coach** | Name used in the README for the eventual agent stack this workspace builds toward (Module 6) — not yet built. |
