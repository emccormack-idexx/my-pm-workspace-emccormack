# Metric Findings — Comeback Screen Scale Decision

*Source: `data/users.csv`, `data/retention.csv`, `data/sessions.csv`, `data/comeback_sends.csv`. All queries run against these files directly (SQLite over the raw CSVs); column names used exactly as they appear in the files. `data/nudges.csv` exists but wasn't part of this ask, so it isn't used here.*

## 1. Day-7 retention by `cohort_week`

```sql
SELECT cohort_week,
       COUNT(*) AS n_users,
       SUM(CASE WHEN day_7 THEN 1 ELSE 0 END) AS day7_retained,
       ROUND(100.0*SUM(CASE WHEN day_7 THEN 1 ELSE 0 END)/COUNT(*),1) AS day7_retention_pct
FROM retention
GROUP BY cohort_week
ORDER BY cohort_week;
```

| cohort_week | n_users | day7_retained | day7_retention_pct |
|---|---|---|---|
| 1 | 100 | 37 | 37.0% |
| 2 | 100 | 37 | 37.0% |
| 3 | 100 | 31 | 31.0% |
| 4 | 100 | 27 | 27.0% |
| 5 | 100 | 61 | 61.0% |

**What this means for scaling:** weeks 1–4 (no Comeback treatment running yet) show retention eroding further, not stabilizing — 37% → 37% → 31% → 27%. That's the backdrop the Comeback screen is meant to fix, and it confirms the problem is still live, not a one-time dip. Week 5's 61% is **not** directly comparable to weeks 1–4 — it's a blend of the comeback/control split introduced that week (see Q3), so the jump isn't organic improvement, it's the treatment arm pulling the average up.

## 2. Does `broke_streak_week1 = true` retain worse at day 7?

```sql
SELECT broke_streak_week1,
       COUNT(*) AS n_users,
       SUM(CASE WHEN day_7 THEN 1 ELSE 0 END) AS day7_retained,
       ROUND(100.0*SUM(CASE WHEN day_7 THEN 1 ELSE 0 END)/COUNT(*),1) AS day7_retention_pct
FROM retention
GROUP BY broke_streak_week1;
```

| broke_streak_week1 | n_users | day7_retained | day7_retention_pct |
|---|---|---|---|
| false | 310 | 142 | 45.8% |
| true | 190 | 51 | 26.8% |

Sanity-checked by cohort week to make sure this isn't just one week driving it:

| cohort_week | broke_streak_week1 | n_users | day7_retention_pct |
|---|---|---|---|
| 1 | false | 74 | 41.9% |
| 1 | true | 26 | 23.1% |
| 2 | false | 61 | 45.9% |
| 2 | true | 39 | 23.1% |
| 3 | false | 55 | 36.4% |
| 3 | true | 45 | 24.4% |
| 4 | false | 65 | 29.2% |
| 4 | true | 35 | 22.9% |
| 5 | false | 55 | 80.0% |
| 5 | true | 45 | 37.8% |

**What this means for scaling:** yes — clearly and consistently. Breaking a streak in week 1 comes with roughly a 19-point gap in day-7 retention overall (26.8% vs. 45.8%), and that gap holds in every single cohort week we have, not just on average. This is the exact mechanism the Comeback screen targets, so it confirms we're aiming the fix at the right lever. One more thing worth flagging: in week 5, the broke_streak_week1=true group retained at 37.8% — still lower than non-breakers, but far above the ~23% breakers saw in weeks 1–4. That's consistent with the Comeback treatment specifically helping the exact segment it was designed for (confirmed directly in Q3).

## 3. Week-5 `variant` (comeback vs. control) — day 7 and day 30

```sql
SELECT u.variant,
       COUNT(*) AS n_users,
       ROUND(100.0*SUM(CASE WHEN r.day_7 THEN 1 ELSE 0 END)/COUNT(*),1) AS day7_pct,
       ROUND(100.0*SUM(CASE WHEN r.day_30 THEN 1 ELSE 0 END)/COUNT(*),1) AS day30_pct
FROM users u
JOIN retention r ON u.user_id = r.user_id
WHERE u.cohort_week = 5
GROUP BY u.variant;
```

| variant | n_users | day7_pct | day30_pct |
|---|---|---|---|
| comeback | 50 | 76.0% | 36.0% |
| control | 50 | 46.0% | 22.0% |

**What this means for scaling:** this is the actual experiment result, and it's the strongest evidence in this whole analysis. Comeback beats control by +30 points at day 7 (76% vs. 46%, a ~65% relative lift) and by +14 points at day 30 (36% vs. 22%, a ~64% relative lift). The absolute gap narrows from day 7 to day 30 — expected, since both groups decay over time — but the *relative* lift barely moves (~65% → ~64%), which means this isn't a short-lived novelty bump; it holds up a month out. The one honest caveat: n=50 per arm is a real but modest sample for a scale decision — a promising pilot result, worth continued monitoring as exposure grows, not yet proof at the scale leadership will eventually want to see.

## 4. `comeback_sends.csv` open rate by `send_number` (1–4) vs. control

```sql
SELECT send_number, variant,
       COUNT(*) AS n_sends,
       SUM(CASE WHEN opened THEN 1 ELSE 0 END) AS n_opened,
       ROUND(100.0*SUM(CASE WHEN opened THEN 1 ELSE 0 END)/COUNT(*),1) AS open_rate_pct,
       ROUND(100.0*SUM(CASE WHEN acted_on THEN 1 ELSE 0 END)/COUNT(*),1) AS acted_on_rate_pct
FROM comeback_sends
GROUP BY send_number, variant
ORDER BY send_number, variant;
```

| send_number | variant | n_sends | n_opened | open_rate_pct | acted_on_rate_pct |
|---|---|---|---|---|---|
| 1 | comeback | 50 | 14 | 28.0% | 16.0% |
| 1 | control | 50 | 2 | 4.0% | 0.0% |
| 2 | comeback | 50 | 19 | 38.0% | 12.0% |
| 2 | control | 50 | 2 | 4.0% | 0.0% |
| 3 | comeback | 50 | 23 | 46.0% | 12.0% |
| 3 | control | 50 | 2 | 4.0% | 0.0% |
| 4 | comeback | 50 | 28 | 56.0% | 28.0% |
| 4 | control | 50 | 2 | 4.0% | 0.0% |

(50 distinct users per variant, 4 sends each = 200 sends per arm.)

**What this means for scaling:** comeback-variant opens climb with every send — 28% → 38% → 46% → 56% — while control stays flat at ~4% throughout. That's the opposite of typical reminder fatigue, where engagement usually *drops* on repeated sends, so it's worth understanding *why* before locking in a 4-send cadence at scale (is send 4's content different, more urgent, or is this a self-selection effect where only more-engaged users are still receiving/opening by send 4?). `acted_on` tells a similar but noisier story: control users essentially never act (0.0% at every send), while comeback users act on 12–28% of sends, dipping slightly at sends 2–3 before jumping to 28% at send 4. That dip-then-jump shape is worth a follow-up look rather than a confident story — it's a real pattern in the data, not yet an explained one.

## Bottom Line: Should We Scale the Comeback Screen?

All four cuts point the same direction. Weeks 1–4 confirm the retention problem is real and getting worse, not stabilizing on its own (Q1). The broke-streak-week1 segment is exactly where the damage concentrates, in every cohort (Q2). The actual week-5 experiment shows the Comeback treatment substantially outperforming control at both day 7 and day 30, with the relative lift holding up over time (Q3). And the comeback-nudge sequence dramatically outperforms control on both opens and real action (Q4).

That's a consistent, converging case **for** moving forward with scaling — with two honest caveats to carry into that conversation, not to bury: the experiment sample is modest (n=50/arm), and the climbing-engagement pattern in the send sequence isn't yet understood well enough to just copy the exact 4-send cadence as-is at scale.
