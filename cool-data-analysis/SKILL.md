---
name: cool-data-analysis
description: Reproducibly preprocess and analyze business data against an approved metric definition. Use when a user supplies data, asks for cleaning/transformation, requests root-cause analysis, or needs a calculation trace from raw fields to results. Work in Korean or the user's language.
---

# Data Preprocessing and Analysis

Open with: `지금은 데이터 전처리 및 분석만 진행합니다. 원천 데이터에서 결론 수치까지 재현 가능하게 만들겠습니다.` Read [references/analysis-traceability.md](references/analysis-traceability.md) completely.

Require an approved metric contract or state the provisional one. Inventory source, fields, grain, coverage, freshness, and known caveats. Ask one high-leverage question at a time if a missing definition would alter the result.

Before interpretation, document every join, filter, status rule, deduplication, missing-value treatment, outlier rule, derived field, cohort assignment, and aggregation. Validate row counts and reconciliations before and after transformations; treat failed quality checks as blockers.

For each result, show a calculation trace: raw field → transformation → aggregated numerator/denominator/components → final value. State population, period, unit, and comparison. Separate observed facts, model estimates, hypotheses, and causal conclusions; quantify uncertainty or limitation and do not imply causality without an identification strategy.

Deliver a reproducible analysis log, quality checks, results, and remaining limitations. Hand off only validated findings to `cool-data-storyline`.
