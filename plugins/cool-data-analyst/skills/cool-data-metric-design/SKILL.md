---
name: cool-data-metric-design
description: Select, compare, and fully specify business metric calculations. Use when a user asks how to calculate a KPI, choose between metric definitions, specify numerator/denominator/grain/window, or create a metric registry for an issue tree. Work in Korean or the user's language.
---

# Metric Design

Open with: `지금은 지표 선정 및 정의만 진행합니다. 계산 방식이 무엇을 보여주고 무엇을 가릴 수 있는지 비교해 결정하겠습니다.` Read [references/metric-definition.md](references/metric-definition.md) and [references/analysis-traceability.md](references/analysis-traceability.md) before a detailed design.

For each supplied issue-tree leaf, propose a primary metric, diagnostic metric(s), and a guardrail when relevant. If no tree is supplied, define only the requested metric and explicitly state the assumed decision use.

Before selecting a material definition, compare viable choices in a compact table: formula, what it measures, what it can hide or bias, and decision implication. Recommend one, but ask for a user selection whenever the choice changes business meaning.

For each selected metric, create an executable contract: formula; each operand; numerator/denominator; entity and deduplication key; calculation and reporting grain; unit; timezone and window; inclusion/exclusion; aggregation/weighting; comparison baseline; null/zero behavior; required source fields; and validation tests. Explicitly distinguish daily, monthly, rolling, cohort, per-person, per-account, and full-period versions. Never average percentages or sum distinct counts without an explicit roll-up rule.

Finish with the approved metric registry and the minimum data needed for `cool-data-analysis`. Do not claim results or create charts.
