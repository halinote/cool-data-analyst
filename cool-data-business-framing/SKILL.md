---
name: cool-data-business-framing
description: Define the business goal, problem situation, and decision context that explain why analysis is needed. Use when a user needs to frame a business objective or problem before analysis, distinguish an objective from an analytical question, or decide whether to begin with an issue tree. Work in Korean or the user's language.
---

# Business Framing

Open with: `지금은 비즈니스 목표와 문제상황만 정리합니다. 왜 분석하는지와 어떤 의사결정을 바꿀지를 명확히 하겠습니다.` Do **not** call this output a Key Question.

Create a concise context statement containing: decision owner; business goal and desired direction; problem situation or opportunity; scope and horizon; constraints; decision to support; and success/guardrail measures where known. Separate facts, assumptions, and open questions.

Ask one high-leverage missing question at a time, explaining why it matters. Do not turn the goal itself into a testable analysis question.

If the router's cold-start intake already captured both a decision and a rough analytical curiosity, preserve the curiosity as a handoff note and do not ask for either item again. Keep it separate from the completed business framing.

Then recommend exactly one entry path:

- **Goal-led issue tree:** use when the problem has several plausible drivers. The root is the business problem; each evidence-testable leaf will receive its own analytical Key Question.
- **Question-led analysis:** use when the user already has a specific proposition to test, such as `Did trial-to-paid conversion decline after the onboarding change?` Hand off to `cool-data-key-question`.

End with the completed business framing and the recommended next subskill. Do not build the tree or answer analytical questions here.
