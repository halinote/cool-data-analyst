---
name: cool-data-issue-tree
description: Build, audit, and visualize a MECE issue tree from either a business problem or a defined analytical Key Question. Use when a user asks for an issue tree, driver tree, root-cause decomposition, or a structured visual explanation of a problem. Render every completed tree as responsive interactive HTML. Work in Korean or the user's language.
---

# MECE Issue Tree

Open with: `지금은 MECE 이슈트리만 만듭니다. 문제를 구조화하고 각 리프에 검증 가능한 분석 질문을 붙이겠습니다.` First identify the root type:

- **Goal-led tree:** root = business problem or goal. Use this when the task is to understand the drivers of a broad outcome. Every evidence-testable leaf must receive an analytical Key Question.
- **Question-led tree:** root = an already defined analytical Key Question. Use this when the task is to break the evidence needed to answer one proposition into subquestions.

If neither root is sufficiently specified, ask one clarification rather than silently mixing goal and question.

Choose one primary sibling logic: equation, process, segment, driver, or options. Name it. Keep siblings on the same logical basis and abstraction level; do not mix causes, solutions, metrics, and segments. Use 2–4 branches per level and stop at evidence-testable leaves.

For every tree, create one canonical node model before rendering. Give each node a stable ID, parent ID, concise label, node type (`root`, `driver`, or `leaf`), and sibling logic. Give every leaf its **analytical Key Question**, evidence/metric needed, and decision relevance. Record the MECE boundary, exclusions, overlap risk, and any `practically MECE` caveat. A leaf question must be testable, not a restatement of the business goal.

Use the `visualize` skill to render **every completed tree** as an inline HTML explainer; HTML is the default presentation of the issue-tree artifact, not a separate `MECE viz` analysis skill. Follow the visualization skill's inline-fragment and response contract.

Keep hierarchy dominant and show the complete first meaningful level at initial render. Use restrained visual encoding to distinguish root, drivers, and evidence-testable leaves. Let node selection reveal only the node's analytical question, sibling logic or MECE boundary, evidence/metric, and decision relevance. Add local expand/collapse only when tree depth or width would otherwise make labels unreadable. Make selection keyboard accessible, pair color with text or shape, reflow without horizontal clipping, and include a concise screen-reader tree alternative.

Do not repeat the full tree in prose after rendering. Follow the visual with only the MECE audit: sibling logic used, overlap check, excluded scope, practical caveat, and unresolved gap. If the HTML visualization capability is unavailable, provide a readable indented tree and a Mermaid fallback without claiming that HTML was created.

Show the completed visual tree and audit, then ask whether to revise it or use the leaf questions as input to `cool-data-metric-design`. Do not calculate final metrics, analyze data, or create unrelated visuals here.
