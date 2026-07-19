# Analysis Traceability and Presentation Notes

Use this reference for Step 3–5. It makes every number, transformation, and visual auditable.

## A. Analysis ledger

Maintain one row per analysis output or metric slice.

| Item | Record exactly |
|---|---|
| Business question | Key Question and issue-tree leaf answered |
| Output | Metric/chart value, unit, segment, period |
| Raw data | Tables/files, fields, source owner, extraction time, raw grain, coverage |
| Population | Eligibility rule, inclusions/exclusions, denominator population |
| Transformations | Join keys/type, filters, status logic, deduplication key + precedence, null/outlier treatment, derived fields |
| Formula | Full algebra; numerator/denominator or all operands; scale and weights |
| Aggregation | Event-to-user/day/month method; distinct-count, sum, weighted recompute, average, or last-value rule |
| Validation | Row-count changes, uniqueness, reconciliation, bounds, freshness and sensitivity checks |
| Limitation | Bias, missingness, maturity, confounding, uncertainty, or non-causal interpretation |

Show a compact version in the deliverable and retain the complete trace in supporting material. Never write “calculated from data” without the transformation and formula.

## B. Preprocessing protocol

1. **Profile sources:** record schema, raw grain, primary keys, timestamp semantics, timezone, date range, refresh time, null/duplicate rates, and known gaps.
2. **Define the analytic population:** apply the metric contract before aggregation. Record records removed at each eligibility filter.
3. **Join deliberately:** state left/inner/full join, keys, expected cardinality, and how one-to-many fanout is prevented or aggregated.
4. **Resolve duplicates:** state key and precedence (for example, latest valid `updated_at` per `order_id`).
5. **Handle invalid/missing values:** state whether values are excluded, imputed, classified as unknown, capped, or retained; quantify impact.
6. **Create derived fields:** write the exact expression and unit conversion. Preserve raw columns.
7. **Aggregate at the contracted grain:** calculate components before non-additive rates. For an overall rate use `SUM(numerator) / SUM(denominator)`, unless equal weighting is deliberate and documented.
8. **Validate:** reconcile totals to a source-of-truth total; test bounds; compare pre/post row counts; inspect extreme values; test time and cohort boundaries; report failures.

## C. Calculation trace template

For any reported value, use this pattern:

```text
Metric: 14-day trial-to-paid conversion, April 2026, new trial cohort
Raw fields: trial_started_at, first_paid_at, user_id, account_type
Eligibility: production users with first trial in [2026-04-01, 2026-05-01), excluding employee/test accounts
Numerator: COUNT(DISTINCT user_id with first_paid_at in [trial_started_at, trial_started_at + 14d]) = 1,240
Denominator: COUNT(DISTINCT eligible trial starters) = 8,610
Calculation: 1,240 / 8,610 × 100 = 14.40%
Rollup: full-period ratio of sums; not arithmetic mean of daily rates
Validation: numerator is subset of denominator; cohort count reconciles to trial-start event table
```

## D. Chart contract: exact plotting rules

For each chart, document:

| Field | Required content |
|---|---|
| Claim | The one statement the visual proves |
| Mark and grain | Bar/line/point/etc. and one observation's grain |
| X-axis | Field, ordered values/bin/window, unit, timezone, and range |
| Y-axis | Formula of plotted value, unit/scale, range, and zero/baseline rule |
| Series/facet/color | Exact grouping field and category definitions |
| Population | Eligibility, filters, segment, cohort, and denominator |
| Calculation | Raw fields → transforms → numerator/denominator/operands → aggregation/weighting |
| Reference | Target, prior period, control, benchmark, or confidence interval and formula |
| Labels | Which values are directly labeled and rounding rule |
| Why this value | Driver/reconciliation or limitation that explains the observed magnitude |
| Caveat | Sample size, incomplete period, uncertainty, or non-causal warning |

Examples:

```text
X-axis: calendar week of trial start, Monday 00:00–Sunday 24:00 Asia/Seoul.
Y-axis: distinct users converting within 14 days / distinct eligible trial starters in that week's cohort × 100; 0–25%, percentage scale.
Line value: ratio of weekly sums, not a daily-rate average. Values after the latest mature cohort are not plotted.
```

## E. Required PPT chart footer

Put a small, readable methodology note at the bottom of **every slide containing an analytical number, table, or chart**. Use 9–10pt in a normal presentation; use 11px or the smallest accessible host-scaled secondary text in a dashboard. Do not allow it to overlap the visual.

Use this compact format (one to three lines, separated with `•`):

```text
* Metric: [exact formula] • Population: [eligible entities + exclusions] • Period: [start–end, timezone]
* Calculation: [grain → aggregation/weighting] • X: [field/range/unit] • Y: [formula/unit/scale]
* Source: [table/file + refresh] • Notes: [n, maturity, missingness, uncertainty, causal limitation]
```

For a non-chart conclusion slide, include the formula/source/period of the decisive evidence and any modeled assumption. For a chart without an axis (for example a waterfall), replace X/Y with “Marks: [component formula]” and “Reconciliation: [start + components = end].”

## F. Required visible “수치 해석” below conclusions

Place a visible `수치 해석` block immediately below the takeaway conclusion, chart, or recommendation it supports. This is **not** the small methodology footer: it explains why the observed numbers lead to the conclusion for the decision-maker. Use 14–18pt in a presentation, enough contrast, and 2–4 short lines or bullets.

Every block must contain, in this order:

1. **Observed value:** exact value(s), unit, segment, and period from the chart.
2. **Comparison:** absolute delta, percentage-point delta, or percent change versus a named baseline/target; state the arithmetic.
3. **Driver/read-through:** the numeric relationship that makes the value decision-relevant (rank, concentration, reconciliation, trade-off, or modeled effect).
4. **Decision bridge and caveat:** the specific action or next test it supports, plus the material limitation if the evidence is observational or modeled.

Use this template:

```text
수치 해석
• [Segment A]의 [metric]은 [value]로, [baseline]의 [value] 대비 [± absolute unit / ±pp / ±%]이다.
• [Driver]의 [value]가 [comparison]이므로, [formula or mechanism]을 통해 [outcome]에 [quantified impact]를 준다.
• 따라서 [action]을 [scope]에서 검증한다. 단, [caveat]이므로 [validation method] 전에는 인과로 단정하지 않는다.
```

For a final recommendation that comes from a scenario model, name each modeled input and show the arithmetic bridge:

```text
수치 해석
• ₩25M을 Broad·Interest에서 Lookalike·Retargeting으로 이동하면, 모델의 신규 유료 고객은 1,273명에서 1,342명(+69명, +5%)이다.
• LTV/CAC는 Σ(고객 수×오디언스별 LTV) ÷ ₩100M으로 2.98×에서 3.21×(+0.23×)가 된다; 30일 유지율은 고객 수 가중 평균으로 64%에서 67%(+3pp)다.
• 이는 고효율 오디언스 확대의 가설을 지지하므로 2주 CAC 검증과 30일 유지율 holdout을 통과할 때만 확대한다.
```

Never say “높다/낮다/개선된다” without the displayed comparison and its unit. Never use a narrative interpretation to hide a denominator, small sample, incomplete cohort, modeled input, or non-causal limitation.

## G. Analyst QA before delivery

- Can another analyst reproduce every headline number from the ledger?
- Does the formula use the stated numerator, denominator, scope, window, and deduplication?
- Are x and y axis labels exact fields/formulas and units, not vague names?
- Does the chart’s aggregation match the metric contract?
- Do chart totals reconcile to source totals or are differences explained?
- Are percent change and percentage-point change correctly distinguished?
- Does the footer state data source, timeframe, calculation, and limitation?
- Does every chart conclusion and recommendation have a visible 수치 해석 block with observed value, baseline delta, driver, action, and caveat?
- Are facts, estimates, hypotheses, and causal conclusions clearly separated?
