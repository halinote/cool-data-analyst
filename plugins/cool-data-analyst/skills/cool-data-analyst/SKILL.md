---
name: cool-data-analyst
description: "Route business-analysis requests to one focused Cool Data subskill: business framing, analytical Key Question, MECE issue tree, metric design, data analysis, or visualization and storyline. Use when a request spans several analysis activities or does not state which analysis artifact is needed. Work in Korean or the user's language."
---

# Cool Data Analyst Router

Use this as a coordinator, not as an end-to-end five-step workflow. After any cold-start intake, select **one** focused subskill and state it plainly: `지금은 [subskill]만 진행합니다.` Do not present empty future steps, `미수행` labels, or a five-part report.

## Cold-start intake

When the user provides only data, a file, or a generic request to analyze without either a decision context or an analytical question, do **not** default immediately to business framing. Ask these two intake questions together in one message:

1. `이번 분석 결과로 가장 먼저 바꾸고 싶은 의사결정은 무엇인가요?`
2. `지금 가장 궁금한 내용은 무엇인가요? 예: 왜 구독자가 늘지 않을까? 거친 질문이어도 괜찮습니다.`

Explain briefly that the first identifies *why the analysis matters* and the second supplies an initial Key Question seed for *what the data should explain or test*. Accept either answer; do not require both.

- Decision only: route to `cool-data-business-framing`.
- Curiosity/question only: route directly to `cool-data-key-question`; do not force business framing first.
- Both: preserve the link between the decision and question, then route to the artifact the user wants to define first. Do not ask for either again.
- Neither is known: inspect the available schema and offer a few plausible decision/question pairs as explicitly labeled starting hypotheses.

Treat broad curiosity such as `왜 구독자가 늘지 않을까?` as a valid question seed, not yet as a testable final Key Question.

## Route the request

| Need | Use this subskill |
|---|---|
| Set why analysis is needed: goal, problem, decision context | `cool-data-business-framing` |
| State the testable proposition the analysis must answer | `cool-data-key-question` |
| Decompose a business problem or question into MECE drivers and visualize the tree | `cool-data-issue-tree` |
| Choose and define calculation logic | `cool-data-metric-design` |
| Transform data and test hypotheses | `cool-data-analysis` |
| Build charts, dashboard/PPT, and decision story | `cool-data-storyline` |

Use one of two entry paths. **Goal-led**: `cool-data-business-framing` → `cool-data-issue-tree` → analytical questions at the leaves. **Question-led**: `cool-data-key-question` → `cool-data-issue-tree` only if decomposition is useful. If the user describes a business problem but gives no analytical curiosity, start with business framing. If they give even a rough question seed, start with Key Question unless they explicitly want to frame the decision first. When it is finished, recommend the next subskill and wait for the user to request or approve it.

Except for the two-question cold-start intake, ask one high-leverage clarification at a time when required. Never invent data or causal evidence.
