# Top Line and Visual Storyline

Turn a supported conclusion into a sequence of visuals that makes the decision logic easy to understand. Treat every visual as evidence for one claim, not as decoration or a dashboard inventory.

## 1. Write the top line first

Write one governing sentence that contains:

```text
Decision answer + magnitude or decisive evidence + primary driver + recommended direction
```

Use a form such as:

> [Outcome] changed by [magnitude] versus [baseline], mainly concentrated in [driver/segment]; therefore [decision owner] should [action], subject to [guardrail or uncertainty].

The top line must:

- answer the Key Question directly
- use the metric contract's exact meaning and unit
- distinguish measured evidence from estimates
- avoid unsupported causal language
- contain a decision implication, not merely describe a trend
- remain short enough to function as an executive headline

If evidence is incomplete, label it as a hypothesis or provisional top line and state the validation needed. Never fill missing values or imply a settled conclusion.

## 2. Decompose the top line into claims

Create normally 3–5 claims that together prove the top line:

1. **Outcome:** What changed and how material is it?
2. **Location:** Where, when, or for whom is the gap concentrated?
3. **Driver:** Which component or mechanism best explains the gap?
4. **Implication:** Why does this matter for the decision?
5. **Action:** What should happen and how will success be judged?

Make claims mutually distinct and collectively sufficient. Remove any claim that does not change belief, priority, or action.

## 3. Assign one analytical job to each visual

Choose the visual from the comparison the reader must make:

| Analytical job | Preferred visual | Use when |
|---|---|---|
| Current status versus target | KPI card, bullet, dot with reference | One value and benchmark matter |
| Trend or inflection | Line or indexed line | At least 8–12 meaningful time points show shape |
| Two or few period changes | Slope, grouped bar, dot comparison | Discrete periods matter more than continuous shape |
| Category or segment comparison | Sorted horizontal bar or dot plot | Magnitudes across categories must be compared |
| Concentration | Pareto or ranked bar with cumulative share | Top contributors explain most of the effect |
| Additive driver bridge | Waterfall | Components reconcile exactly from start to end |
| Funnel or ordered drop-off | Stage bar or funnel | Stages are ordered and share a valid population logic |
| Composition | 100% stacked bar or stacked bar | Part-to-whole with an explicit denominator |
| Distribution | Histogram or box plot | Spread, skew, median, or outliers matter |
| Relationship | Scatter | At least 12–20 comparable observations at one grain exist |
| Cohort or two-dimensional pattern | Heatmap | Matrix shape or retention pattern matters |
| Experiment or uncertainty | Point estimate with confidence interval | Effect and precision drive the decision |
| Exact lookup | Compact table | Exact values matter more than visual pattern |

Do not use a line merely because time exists. Do not use pie by default. Do not average percentages or visualize non-additive metrics as if they were additive. Keep denominators, windows, grains, filters, and units consistent with the claim.

## 3A. Choose the representation for the cognitive task

Choose the lowest-complexity representation that lets the reader make the required comparison accurately. Do not default to a chart merely because a number exists.

| Reader needs to do | Best representation | Use it when | Avoid it when |
|---|---|---|---|
| Read one decisive value against a target | Number with a benchmark/delta | The magnitude and threshold are the only decision | Trend, distribution, or composition matters |
| Look up a few exact values | Compact table | Exact lookup across 2–10 cells matters | A pattern or rank must be seen quickly |
| Compare magnitude/rank across categories | Sorted bar or dot plot | Difference between categories is the question | There is only one value or too many labels |
| See change over time | Line or slope chart | Shape, timing, or inflection matters | There are fewer than three meaningful periods |
| See a part-to-whole relationship | Stacked bar / 100% stacked bar | One shared denominator and composition are central | Categories do not sum to a meaningful whole |
| Explain exact start-to-end reconciliation | Waterfall | Components add exactly to the outcome | Drivers are correlated or do not reconcile |
| Show uncertainty | Point + confidence interval | Precision changes the decision | No defensible uncertainty estimate exists |

Before drawing, write: `Reader comparison: [exact comparison] → chosen form: [number/table/chart] → why: [one sentence].` If a simple number communicates the decision without loss, prefer it. If the reader must compare position, rank, slope, distribution, composition, or uncertainty, use the matching chart.

## 3B. Axis and label discipline

For every axis-based chart, render both axis titles **inside or immediately adjacent to the chart**:

- **X-axis:** field, ordered window/bin/category rule, and unit where relevant.
- **Y-axis:** plotted formula or metric name, unit/scale, and whether the axis starts at zero or uses a stated delta scale.

Do not bury axis identity in a footer, subtitle, or methodology note. The footer may add calculation detail, but it never replaces visible axis titles.

Make every visible text element earn its place:

- Give the slide/page title the takeaway; give the chart title only the plotted comparison when a separate chart title is needed.
- State a metric name once at the strongest location: generally the y-axis, a direct label, or a single-value callout. Do not repeat it in the title, legend, every mark label, and footer.
- Use direct labels for the focal mark(s); keep non-focal values unlabeled unless exact comparison is necessary.
- Omit a legend when series are directly labeled. Omit repeated units when an axis title or a column header already establishes the unit.
- Remove decorative subtitles, duplicated captions, and labels that do not change the comparison or decision.
- Preserve the minimum information needed to interpret the number: population, time window, denominator, unit, and caveat must still remain visible in the appropriate chart/subtitle/footer locations.

## 4. Write a chart contract

Before rendering or recommending each chart, specify:

- **Claim:** sentence the visual must support
- **Question:** comparison the reader should make
- **Chart:** family and concrete variant
- **Data:** dimensions, measures, numerator/denominator, grain, window, filters, benchmark, and sample size
- **Encoding:** x, y, order, series, facet, reference line, and label
- **Emphasis:** focal mark and contextual marks
- **Annotation:** exact event, gap, driver, or threshold to call out
- **Title:** descriptive by default; use a takeaway headline only when the requested surface calls for an executive narrative
- **Subtitle:** metric definition, unit, date range, cohort, denominator, and caveat
- **Fallback:** more honest form when data is too sparse
- **Decision link:** belief or action this visual should change

Do not render a visual when the supporting data is absent or insufficient. Provide the chart contract and required dataset instead.

## 5. Sequence the visual argument

Use question-and-answer flow. Each visual should raise or answer the next logical question:

```text
So what happened?
→ Where is the gap?
→ What drives it?
→ Is the driver actionable and worth addressing?
→ What should we do next?
```

A common five-part sequence is:

1. **Top line / executive answer** — conclusion, magnitude, decision.
2. **Outcome evidence** — actual versus baseline/target and trend.
3. **Diagnostic evidence** — concentration, segment, funnel, or driver decomposition.
4. **Decision evidence** — opportunity size, option tradeoff, experiment effect, or risk.
5. **Action plan** — recommendation, owner, timing, success metric, guardrail, decision gate.

Do not order visuals by the chronology of analysis. Order them by the logic required to accept the conclusion.

## 6. Use message-led page or slide titles

For an executive storyline, make each page or slide title a supported claim rather than a topic label.

Weak:

> Conversion trend

Strong when supported:

> Conversion fell 2.1pp, with most of the modeled loss occurring at payment completion

Keep chart titles and page headlines distinct when useful: the page headline states the claim; the chart title describes the plotted evidence. Avoid repeating identical text.

## 7. Design emphasis honestly

- Highlight only the series, segment, period, or driver central to the claim; keep context neutral.
- Prefer direct labels and restrained annotations over legends and decorative callouts.
- Include benchmarks, targets, zero lines, confidence intervals, or denominators when required for honest interpretation.
- Start standard magnitude bars at zero. Use narrowed scales only for appropriate delta-focused views with explicit labels and scale cues.
- Avoid color-only distinctions; also use order, line style, markers, labels, or facets.
- Avoid red/green as the default good/bad encoding.
- Keep a consistent unit, scale, date range, and palette across comparable visuals.
- Show unknown or unclassified populations when they could change the conclusion.

## 8. Close the loop to action

End the visual storyline with:

- decision requested or recommendation
- chosen action and explicit non-action
- accountable role and timing
- primary success metric with exact definition
- guardrail metric
- expected impact, labeled measured or estimated
- test or implementation plan
- decision gate for scale, revise, stop, or investigate

The final action must trace back through the visual evidence to the top line.

## 9. Output format

When asked to design a visual storyline, provide:

1. **Top line:** one governing conclusion.
2. **Story arc:** 3–5 claim headlines in order.
3. **Chart map:** claim, visual, required data, emphasis, annotation, and decision link.
4. **Page/slide outline:** headline plus role of each visual.
5. **Final conclusion and action:** recommendation, owner, success metric, guardrail, and decision gate.
6. **Evidence gaps:** data needed before a claim or chart can be finalized.

When actual data is supplied and a visual artifact is requested, render on the selected surface and inspect the final charts for accurate signs, scales, labels, denominators, date ranges, legibility, and consistency. When only a plan is requested, do not create synthetic charts that look like real evidence.

## Quality check

- Does the top line answer the Key Question and state the decision implication?
- Do all claim headlines collectively prove the top line?
- Does every visual have exactly one primary analytical job?
- Is the chart family appropriate for the comparison and data density?
- Are metric definition, grain, period, denominator, and filters consistent?
- Does each chart advance the story rather than repeat another chart?
- Are causal claims proportional to the evidence?
- Can the reader trace the final action back to specific visual evidence?
