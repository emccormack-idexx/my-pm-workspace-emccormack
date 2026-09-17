# Metric Diagnosis — Day-7 Retention & the Comeback Screen

*Source: same files as `metric-findings.md` — `data/users.csv`, `data/retention.csv`, `data/sessions.csv`, `data/comeback_sends.csv`, `data/nudges.csv`. All numbers below are computed directly from these files (SQLite over the raw CSVs); nothing here is estimated or invented. Where a metric can't be computed from what's in `data/`, that gap is called out explicitly rather than filled in.*

---

## 1. Metric Tree — What Actually Moves Day-7 Retention

```
Day-7 Retention
│
├─ Day-1 activation rate (proxy: retention.day_1)
│   → flat 90–93% every cohort week (1–4). NOT a driver of the decline.
│
├─ Streak-break rate (users.broke_streak_week1)
│   → 26% → 39% → 45% → 35% (weeks 1–4); 45% in week 5.
│   → Breaking is consistently bad for retention (see branch below),
│      so a rising break rate drags the blended number down.
│
├─ Non-breaker Day-7 retention (users who never break in week 1)
│   → 41.9% → 45.9% → 36.4% → 29.2% (weeks 1–4).
│   → Erodes on its own, independent of break rate. See §2 — this is
│      the piece the Comeback screen does NOT target and can't fix.
│
└─ Comeback rate — Day-7 retention conditional on having broken the streak
    │
    ├─ Pre-treatment / control baseline: ~23.5% (weeks 1–4 weighted avg);
    │   28.0% for week-5 control-arm breakers (consistent with baseline).
    │
    ├─ Treatment (week-5 comeback-arm breakers): 50.0%.
    │   → +22–27pt lift over baseline — the actual, measured effect of
    │      the Comeback screen. See §3.
    │
    ├─ Notification open rate (of those sent a nudge)
    │   → Old `streak_lost` nudge: 17.7% opened, 0.0% acted (n=141, wks 1–5).
    │   → New `comeback_screen` nudge: 35.0% opened, 50.0% acted (n=20, wk 5).
    │
    └─ Notification opt-in rate
        → NOT measurable from this data. None of the five files record
           whether a user has push notifications enabled at all — only
           whether a *sent* nudge was opened. A user who disabled
           notifications entirely would look identical here to one who
           simply didn't open it. This is a real blind spot, not a zero.
```

**Bottom line on the tree:** the Comeback screen sits entirely inside the "comeback rate" branch. It cannot move day-1 activation (flat already) and — this is the important part — it does not appear to move non-breaker retention at all, because that's a separate, currently-unexplained branch (§2).

---

## 2. What Caused the Weeks 1–4 Decline — Specifically

Two things are moving, and they're not the same thing.

**It is not acquisition mix.** `acquisition_channel` share (organic/paid/referral ≈ 34/34/32) and `platform` share (ios/android ≈ 60/40) are identical across cohort weeks 1–4. Whatever's happening isn't "we started buying worse users."

**It is not day-1 activation.** Flat at 90–93% every week. People are still starting.

**It is two things, and they don't move together:**

1. **The streak-break rate itself is volatile and mostly rising:** 26% → 39% → 45% → 35%. More people breaking their streak in week 1 mechanically drags down the blended number, because breakers retain at ~23% vs. ~30–46% for non-breakers.
2. **Non-breaker retention is independently eroding: 41.9% → 45.9% → 36.4% → 29.2%.** This is the bigger surprise. Even users who *never broke their streak* are retaining worse over these four weeks — a ~13-point drop from week 2's peak to week 4. Session frequency (~3.1–3.4 sessions/user) and average session duration (~226–243 sec) among these same non-breakers are essentially flat across the same weeks — so it isn't that non-breakers are visibly disengaging in-app. Whatever is eroding their day-7 retention isn't visible in how often or how long they use the app; it's happening somewhere these five files don't capture (e.g., something specific to the app itself, a within-channel quality shift not captured by the channel label, or plain sampling noise — n is only 55–74 non-breakers per cohort week, and a two-proportion check on the week 2→4 drop lands right at the edge of statistical significance, not comfortably past it).

**Week-by-week, which effect dominates:**
- Week 1→2 (37%→37%, flat): break rate got *worse* (26%→39%) but non-breaker retention got *better* (41.9%→45.9%) — the two effects canceled out.
- Week 2→3 (37%→31%): both effects point down — break rate up slightly (39%→45%), non-breaker retention down sharply (45.9%→36.4%).
- Week 3→4 (31%→27%): break rate actually *improved* (45%→35%, retention-positive), but non-breaker retention kept falling (36.4%→29.2%) and more than offset it. **This is the specific, non-generic finding: the week 3→4 drop is not explained by more people breaking their streak — it happens despite fewer people breaking. It's driven entirely by something making non-breakers themselves retain worse.**

**Implication:** the Comeback screen, as scoped, only ever touches the streak-break branch. It cannot address the non-breaker erosion, because that erosion has nothing to do with breaking a streak at all. Scaling the Comeback screen will likely still leave this second, unexplained decline untouched.

---

## 3. What the Week-5 Treatment vs. Control Split Actually Fixed

| Group | n | Day-7 | Day-30 |
|---|---|---|---|
| Comeback, broke streak | 20 | 50.0% | — |
| Control, broke streak | 25 | 28.0% | — |
| Comeback, did not break | 30 | 93.3% | — |
| Control, did not break | 25 | 64.0% | — |

Two distinct findings here, not one:

**a) Among breakers, the Comeback screen roughly doubles the recovery rate** — 28.0% → 50.0%. This is the mechanism it was designed for, and it worked in the direction and rough magnitude expected: acknowledgment + a fast, specific way back in measurably beats a bare streak-loss notification (which, recall, drove 0.0% action across 141 sends in weeks 1–5 combined).

**b) Surprising and not something the feature was designed to do: even non-breakers in the comeback arm retained far better than non-breakers in the control arm (93.3% vs. 64.0%).** Checked this against acquisition-channel and platform mix between arms — both are comparably balanced (e.g., organic/paid/referral ≈ 11/8/11 vs. 10/6/9), so it isn't an obvious sampling artifact from those two covariates. Two honest readings: either (1) there's a real spillover effect — simply knowing a safety net exists reduces pre-break anxiety enough to change behavior before anyone ever breaks (which would line up with Amara's interview finding that streak-anxiety starts well before a break), or (2) at n=25–30 per cell, a double-digit swing on a binary outcome is still within reach of chance/unmeasured imbalance. **This is not something to present as a settled 29-point win without saying so plainly — it needs a second week of data before leaning on it.**

**Net:** the data supports "the Comeback screen fixes the recovery moment it was built for" with real confidence. It does not yet support "the Comeback screen also improves retention for people who never break," even though that's what the raw numbers show this week — that claim needs replication, not a re-statement of this week's numbers as fact.

---

## 4. Four Ranked Hypotheses — Why Some Treatment Users Still Churned

Half of comeback-arm breakers (10 of 20) still churned by day 7 despite getting the actual Comeback nudge. Ranked by how much the *existing* data already supports each one.

### Rank 1 — Action beats exposure
**Prediction:** Among comeback-arm breakers, users who acted on at least one comeback send retain at day 7 at a meaningfully higher rate than those who only viewed the comeback screen without acting, and screen-view count alone shows no such relationship.

**What the data shows:** acted_on≥1 breakers retained at 54.5% (6/11) vs. 37.5% (3/8) for acted_on=0 — a real but modest 17-point gap on a very small n. Meanwhile, `comeback`-screen *session* count shows no positive relationship at all — churned breakers averaged slightly *more* comeback-screen visits (2.3) than retained breakers (1.9). The two patterns point the same direction: viewing the screen isn't what correlates with recovery; doing something on it is.

**Confidence: 6/10.** The gap is directionally consistent across two independent cuts (acted_on and view-count both point the same way), which is more reassuring than either alone — but both cuts are drawn from only 19–20 users, so this is suggestive, not proven.

**Would confirm it:** at a larger sample (more treatment weeks), acted_on=yes breakers keep retaining meaningfully higher than acted_on=no breakers, while view-count keeps showing no independent effect.

**Would rule it out:** at a larger sample, the acted_on gap shrinks into noise, or view-count itself starts showing a positive effect — meaning this week's pattern was small-sample noise, not a real "action > exposure" effect.

### Rank 2 — Paid-channel breakers don't recover as well, even with treatment
**Prediction:** Among comeback-arm breakers specifically, day-7 retention is highest for organic-acquired users, lower for referral, lowest for paid.

**What the data shows:** organic 83.3% (5/6), referral 40.0% (2/5), paid 33.3% (3/9) — a 50-point spread. Directionally consistent with the common growth-marketing pattern that paid-acquired users carry lower intrinsic motivation, which one notification-plus-screen wouldn't be expected to fully overcome.

**Confidence: 5/10.** The direction is plausible and the spread is large, but each channel cell has only 5–9 users — a swing this size is well within what small-sample noise alone could produce.

**Would confirm it:** the same organic > referral > paid ordering, with a comparably large spread, holds up among comeback-arm breakers once measured across additional cohort weeks.

**Would rule it out:** at larger n, the three channels converge to within ~10 points of each other among comeback-arm breakers — meaning this week's spread was noise.

### Rank 3 — Repeat breakers treat the offer as noise
**Prediction:** Users who churned despite the Comeback screen had already broken their streak more than once, and by the second break the comeback offer reads as routine rather than meaningful — echoing Tom R.'s interview account of quitting after repeated resets.

**What the data shows:** nothing, either way. `users.csv` and `retention.csv` only carry a single `broke_streak_week1` boolean — there is no field counting how many times a user has broken a streak. This hypothesis is not testable with the current instrumentation.

**Confidence: 2/10** — not because the mechanism is implausible (it's exactly what Tom described in the original interview), but because there is currently zero data either supporting or contradicting it. The score reflects the *data*, not the idea.

**Would confirm it:** adding a repeat-break counter to the schema and finding that churned comeback-arm breakers have a higher average break count than retained ones.

**Would rule it out:** the same counter shows no difference in average break count between churned and retained comeback-arm breakers.

### Rank 4 — Platform-specific drop-off
**Prediction:** iOS users who break their streak are less likely to recover via the Comeback screen than Android users.

**What the data shows:** churned breakers were 6 iOS / 4 Android; retained breakers were an even 5/5 split. A 1-in-10-user tilt on a sample of 20.

**Confidence: 2/10.** The gap is small enough to be essentially noise at this n; there's no mechanism proposed here beyond "the split looked slightly uneven," which is a weak basis for a platform-specific claim.

**Would confirm it:** a clear, repeated iOS-vs-Android gap in comeback-arm breaker recovery across multiple cohort weeks, ideally alongside a plausible mechanism (e.g., a platform-specific bug or notification-delivery difference).

**Would rule it out:** the platform split among comeback-arm breakers evens out to roughly the same recovery rate at larger n.

---

## 5. Which Hypothesis to Act on First

**Rank 1 — action beats exposure.** Two reasons, together:

1. **It's the best-supported hypothesis of the four** — the only one with two independent, mutually-reinforcing signals in the existing data (acted_on gap + the null view-count effect), rather than a single noisy cut.
2. **It's the only one actionable inside a single sprint, on the prototype that already exists.** This lines up directly with a gap the heuristic prototype walkthrough already flagged on screen 1: the streak-freeze CTA and the "skip to lesson" path currently compete for attention, with skip framed as a low-effort plain-text link. If exposure isn't what's helping people recover — action is — the highest-leverage, cheapest next step is making the action step itself harder to bypass and easier to complete (e.g., a more prominent single primary action instead of a primary offer + a de-emphasized skip link), then re-measuring the acted_on-vs-retention relationship on the next cohort.

By contrast: the channel hypothesis (Rank 2) points at a targeting/acquisition-mix decision, not a product change — a different team's sprint, not this one's. The repeat-break hypothesis (Rank 3) can't be tested at all without new instrumentation, so the first sprint's job there would be adding a field, not shipping a UX fix. The platform hypothesis (Rank 4) is too weak to justify sprint time yet.
