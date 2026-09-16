# Streakly Comeback Experience — PRD Skeleton

*Source: Planning meeting notes, Monday 9:14am*

## Project Overview

**What Streakly is:** A consumer habit + micro-learning app. Users pick a track and complete a short (five-minute) daily lesson; the streak is the core habit loop. Launched 4 years ago, Series B funded ($42M), 2.1M registered users, 340K monthly active users, growing 28% YoY on MAU.

**Squad:** Product Engagement
- Erica — Product Manager
- Marcus — Head of Product
- Raj — Engineer
- Lena — Designer

**Current phase:** Discovery / problem-scoping. The squad is aligning internally on the problem and scope of the Comeback experience before bringing a proposal to leadership. No solution direction has been committed to yet.

**Key stakeholders:** Marcus (Head of Product, sponsor of the initiative), leadership (audience for the eventual proposal).

## Problem Statement

Day-7 retention has dropped from 48% to 39% since the streak redesign shipped. The decline is sharpest among users who break their streak in week 1 — once a user misses two days in a row, churn nearly doubles.

User research suggests why: people build a good streak, miss a day for normal life reasons, and return to a counter reset to zero with no acknowledgment of their prior progress. The "you lost your streak" push notification has a harsh tone, and tapping through drops users back at day zero with nothing else offered. There's no graceful way back in.

Working hypothesis: users go passive after a streak break because it feels like failure, and the app offers no comeback path — no acknowledgment, no specific reason to re-engage, just a generic reset.

Open question the team flagged: is the root cause the streak reset mechanic itself, the timing/tone of the notification, or both.

## Goals

- Recover Day-7 retention back toward pre-redesign levels.
- Replace the generic "keep going!" re-engagement with something specific to the user's own progress.
- Design and ship a "Comeback" screen shown when a user breaks a streak, including:
  - Display of the user's best-streak stat (instead of just resetting to zero)
  - A one-time, 60-second "comeback lesson" to rebuild momentum
  - A one-tap streak-freeze option to protect a rebuilt streak

## Non-Goals

- Not yet defined in the notes — to be clarified with the team.

## Success Metrics

- Day-7 retention (primary metric currently tracked; no target figure set yet in notes).
- Churn rate among users who miss two consecutive days (called out as a leading indicator, currently ~2x baseline).

*No specific target thresholds were set in the notes — to be defined.*

## Open Questions

- Is the retention drop driven by the streak-reset mechanic, the notification tone/timing, or both?
- What is the targeting logic for who sees the Comeback screen?
- What are the rules for the one-tap streak-freeze (e.g., frequency, eligibility)?
- Raj noted the Comeback screen is technically doable with existing systems and requires no new data sources — confirm this holds once logic/rules are scoped.
