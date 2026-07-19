---
name: cool-data-key-question
description: Define a specific, testable analytical Key Question or proposition. Use when a user asks what the data should prove, measure, compare, validate, or explain; when an issue-tree leaf needs an evidence question; or when analysis starts directly from a question rather than a business goal. Work in Korean or the user's language.
---

# Analytical Key Question

Open with: `지금은 분석 Key Question만 정의합니다. 비즈니스 목표와 별개로, 데이터로 검증할 명제를 분명히 하겠습니다.`

Keep **business framing** separate. A business goal explains *why* analysis is performed (for example, “improve profitability”); a Key Question states *what proposition the analysis will test* (for example, “Did Meta-acquired trials convert at a lower rate after 1 June, controlling for acquisition cohort?”). If business context is missing, record it as a minimal assumption; use `cool-data-business-framing` when it must be established.

Accept a cold-start curiosity such as `왜 구독자가 늘지 않을까?` as a question seed. Preserve the user's intent, then refine it into a testable analytical question; do not reject it for lacking a prior business-framing artifact or silently treat the broad wording as the final Key Question. If the cold-start intake already captured a decision, use it as decision relevance without asking again.

Classify the question before wording it: descriptive (`How much?`), comparative (`Is A different from B?`), evaluative (`Did it meet target?`), diagnostic (`Which driver explains the change?`), causal (`Did X cause Y?`), or predictive (`What will happen?`). Use the weakest valid claim: causal questions require a feasible identification strategy.

Write exactly one testable question including metric, population, period, comparison/baseline, and decision relevance. Examples:

> What was [metric] for [population] in [period]?

> Is [metric] for [A] different from [B] during [period], and by how much?

> Did [intervention] change [metric] for [population] versus [counterfactual/baseline] during [period]?

> Which measurable driver explains the change in [metric] from [period A] to [period B]?

Ask one high-leverage clarification at a time if any term changes the answer. When the question comes from an issue-tree leaf, keep its parent driver and decision relevance. End with the metric/evidence needed and either hand off to `cool-data-metric-design` or, if the question needs decomposition, `cool-data-issue-tree`.
