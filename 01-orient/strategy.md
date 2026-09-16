# Strategy — Recovering the Day-7 Retention Drop

## The Drop

Day-7 retention fell 9 points — from 48% to 39% — since the streak redesign (v2) shipped. The decline is concentrated in users who break their streak in week 1; once a user misses two consecutive days, churn nearly doubles.

## Working Hypothesis

Users disengage after a streak break because the break feels like failure, and the app currently offers no graceful way back in — a cold reset to zero, a harsh "you lost your streak" notification, and no path forward once they tap through.

If users had a specific, personal reason to return after a break (rather than a generic "keep going" prompt), we'd expect fewer of them to go passive after breaking a streak — which should show up as improved Day-7 retention among week-1 streak-breakers specifically.

## What's Still Open

- Whether the root cause is the streak-reset mechanic itself, the notification's tone/timing, or both — this hasn't been isolated yet.
- Non-goals and specific success targets haven't been defined.
- No solution direction has been committed to. (One early sketch — a "Comeback" screen with a best-streak stat, a short comeback lesson, and a one-tap streak-freeze — has been floated informally by Lena, but it is not yet an agreed direction and the squad has intentionally not anchored on it while aligning on the problem.)

## Why This Matters Now

This is the current focus for the Product Engagement squad, working toward a problem/scope alignment before bringing a proposal to leadership.
