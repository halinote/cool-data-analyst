# Metric Definition

Define a metric as an executable contract, not a label. Produce enough detail that independent analysts using the same source data obtain the same result.

## Definition-choice gate: explain, then choose

Before defining a metric, identify calculation choices that materially alter what the metric means. Present a compact comparison before locking the contract:

| Choice | Formula or rule | What it reveals | What it can hide or distort | Decision impact | Recommendation / user choice |
|---|---|---|---|---|---|

For each material choice, explain the number using the actual or illustrative components when available. State how a different choice could change the conclusion, not merely the calculation. Recommend one option based on the Key Question, then ask the user to select **one high-leverage unresolved choice at a time**. Do not ask when the semantic owner has already specified the rule; record it as confirmed.

Common choices to surface when relevant:

- **Entity:** user versus account versus session versus order. User shows people; account shows commercial relationships; session shows visit-level efficiency.
- **Population/denominator:** all users, eligible users, exposed users, sessions, trials, or opportunities. A broader denominator lowers a rate and measures reach; an eligible denominator measures execution within the addressable population.
- **Time:** calendar-period activity versus entry cohort; event time versus payment/settlement time; rolling versus fixed window. Cohorts reveal lifecycle behavior; calendar periods reveal current business throughput.
- **Aggregation:** ratio of sums versus average of daily/entity rates; user-weighted versus equal-weighted average; total versus per-person. Ratio of sums represents the aggregate experience; equal weighting prevents large groups from dominating but can overstate small groups.
- **Value basis:** gross versus net; booked versus recognized versus collected; nominal versus constant currency. Choose the basis aligned to the financial decision.
- **Attribution/maturity:** first-touch, last-touch, multi-touch; 7/14/30-day conversion window; mature-only versus provisional cohorts. Short windows are timely but miss delayed effects; mature cohorts are comparable but lag.
- **Outlier/missingness policy:** retain, exclude, cap, winsorize, impute, or show unknown. Robust treatment can reveal typical performance but must not hide economically real extremes.

Never silently substitute a convenient denominator, average, time window, or attribution rule. Label the selected option as confirmed, proposed, or open in the metric contract.

## Workflow

### 1. Start from the decision

State:

- decision the metric supports
- behavior or business outcome it represents
- decision owner and review cadence
- whether it is an outcome, driver, diagnostic, or guardrail metric

Reject vanity metrics whose movement would not change a decision. If the metric is a proxy, state what it proxies and how it can mislead.

### 2. Write the semantic definition

Specify:

- **Metric name:** unambiguous business name and optional technical name
- **Meaning:** one-sentence interpretation
- **Entity:** user, account, order, session, item, subscription, merchant, or another unit
- **Qualifying event or state:** exact business event that causes inclusion
- **Unit:** count, KRW, USD, percentage point, percent, seconds, items/user, or another unit
- **Directionality:** whether higher, lower, or a bounded range is better
- **Owner and source of truth:** when known

Never use undefined words such as active, valid, retained, churned, new, completed, revenue, or customer. Define their event/state conditions.

### 3. Write the mathematical definition

Show the complete equation and explicitly label every term.

For ratios and rates:

```text
Metric = Numerator / Denominator × Scale
```

Define:

- numerator population and qualifying condition
- denominator eligible population and qualifying condition
- whether numerator must be a subset of denominator
- deduplication key for each side
- scale: 1, 100, 1,000, etc.
- zero-denominator result: NULL, 0, suppressed, or not applicable

For sums, differences, and products, show all operands and signs:

```text
Net revenue = Gross recognized revenue - Refunds - Discounts - Taxes
Revenue = Paid orders × Items per paid order × Net price per item
```

Define whether monetary values are gross/net, booked/recognized/collected, tax-inclusive/exclusive, nominal/constant currency, and which FX date/rate applies.

For averages, name the weighting explicitly:

```text
Unweighted daily average = SUM(daily metric) / number of eligible days
User-weighted rate = SUM(user successes) / SUM(user opportunities)
Average of user rates = SUM(each user's rate) / number of eligible users
```

Do not treat these as interchangeable. Prefer ratio-of-sums for an overall rate unless the decision calls for equal weight per entity or period.

### 4. Fix the grain and time semantics

Specify both the calculation grain and reporting grain:

- event, user-day, account-month, order, cohort, or other base grain
- daily, weekly, monthly, quarter-to-date, rolling N-day, lifetime, or full-period output
- calendar versus rolling window
- timezone and day boundary
- event time versus processing/ingestion time
- window boundaries, preferably half-open: `[start, end)`
- partial-day/month handling
- late-arriving data and restatement policy
- cohort entry date and observation/maturity window when relevant

Distinguish these common calculations:

- **Daily total:** events occurring within each calendar day
- **Monthly total:** events occurring within the calendar month
- **Average daily value in a month:** sum of daily values divided by eligible days
- **Monthly distinct users:** distinct users across the whole month, not the sum of daily distinct users
- **Per-person metric:** total qualifying value divided by distinct eligible people in the same scope and window
- **Full-period rate:** total numerator across the period divided by total denominator across the period
- **Average of daily rates:** arithmetic or weighted average of daily rates; state weights

### 5. Fix scope and set logic

List inclusion and exclusion rules:

- product, platform, geography, channel, segment, plan, or experiment scope
- test/internal/bot/fraud accounts
- cancellations, refunds, reversals, duplicates, retries, and deleted records
- missing IDs, missing timestamps, unknown categories, and null values
- reactivated users, account merges, cross-device identity, and anonymous-to-known stitching
- valid status transitions and event precedence

State the deduplication rule as key plus precedence, for example: keep the latest valid record by `order_id` using `updated_at`.

### 6. Define aggregation behavior

Classify the metric:

- **Additive:** safely summed across all relevant dimensions, such as eligible transaction value when currencies and definitions match.
- **Semi-additive:** summed across some dimensions but not time, such as end-of-day inventory.
- **Non-additive:** ratios, distinct counts, medians, percentiles, and retention rates; recompute from components instead of summing.

For every rollup, say whether to sum, recompute, weight, take the last value, average, or prohibit aggregation. Never sum daily distinct users to obtain monthly distinct users or average percentages without specifying weights.

### 7. Define comparison semantics

When change is reported, distinguish:

```text
Absolute change = Current - Previous
Percent change = (Current - Previous) / Previous × 100
Percentage-point change = Current rate - Previous rate
Index = Current / Baseline × 100
```

Specify the baseline, comparable window, seasonality treatment, and behavior when the baseline is zero or negative.

### 8. Define implementation and validation

When schemas are available, map every component to source tables, fields, join keys, filters, and timestamps. Provide SQL or pseudocode only when requested or when it removes material ambiguity; do not invent unavailable schema names.

Include validation checks:

- numerator does not exceed denominator when subset logic applies
- component reconciliation to known totals
- uniqueness at the declared grain
- null, duplicate, and late-event rates
- daily-to-monthly reconciliation appropriate to the metric type
- boundary tests at start/end times and timezone changes
- backfill stability and expected freshness

### 9. Mark unresolved choices

Separate:

- **Confirmed definition** — supported by the user's requirements or source of truth
- **Proposed definition** — recommended default requiring approval
- **Open decision** — alternatives that materially change the number

Do not silently choose among material alternatives such as users versus accounts, created versus paid orders, event time versus settlement time, or daily average versus full-period ratio.

## Metric Contract Output

Use this structure for each metric:

1. **Name and purpose**
2. **Business definition**
3. **Formula**
4. **Numerator / denominator / operands**
5. **Entity, grain, and unit**
6. **Time window and timezone**
7. **Inclusions, exclusions, and deduplication**
8. **Aggregation and rollup rules**
9. **Comparison rule**
10. **Source mapping and freshness**, if known
11. **Edge cases and zero/null behavior**
12. **Validation tests**
13. **Confirmed / proposed / open decisions**

If several metrics are requested, first show a compact registry table, then give full contracts only for primary metrics or those with material ambiguity.

## Mini example: monthly purchase conversion rate

```text
Monthly purchase conversion rate
= distinct eligible users with ≥1 paid order during month
  / distinct eligible users with ≥1 qualifying visit during the same month
  × 100
```

- Entity and grain: user-month; report monthly
- Window: calendar month `[month_start, next_month_start)` in the declared business timezone
- Numerator: distinct eligible `user_id` with at least one order reaching `paid` state in the window
- Denominator: distinct eligible `user_id` with at least one qualifying visit in the window
- Set rule: numerator must be restricted to users in the denominator
- Exclusions: test, bot, fraud, fully reversed orders; define anonymous users separately
- Rollup: non-additive; recompute distinct numerator and denominator for quarters or segments
- Zero denominator: NULL and flag as insufficient population
- Important alternative: a session-based or funnel-cohort conversion rate answers a different question and must use a different name
