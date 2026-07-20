# Cool Data Analyst

하나의 거대한 단계형 분석 스킬 대신, 필요한 작업만 독립적으로 실행하는 데이터 분석 스킬 모음입니다.

| 필요한 결과물 | 사용할 스킬 |
|---|---|
| 분석의 이유인 목표·문제상황·의사결정 맥락 | `cool-data-business-framing` |
| 검증할 명제인 분석 Key Question | `cool-data-key-question` |
| 목표/문제 또는 질문에서 출발하는 HTML MECE 이슈트리 | `cool-data-issue-tree` |
| 지표 선택·계산식 정의 | `cool-data-metric-design` |
| 전처리·원인 분석 | `cool-data-analysis` |
| 대시보드/PPT/웹 스토리라인 | `cool-data-storyline` |

`cool-data-analyst`는 위 스킬 중 하나를 고르는 라우터입니다. **비즈니스 목표는 왜 분석하는지**, **분석 Key Question은 무엇을 데이터로 검증할지**를 뜻하며 둘을 섞지 않습니다. 목표에서 시작할 때는 `비즈니스 프레이밍 → 이슈트리 → 리프별 분석 Key Question`, 이미 명제가 있을 때는 `분석 Key Question → 지표/분석`으로 진행합니다.

데이터만 있고 목적과 질문이 없는 cold start에서는 라우터가 다음 두 가지를 한 번에 확인합니다: **이번 분석으로 가장 먼저 바꾸고 싶은 의사결정**과 **지금 가장 궁금한 내용**. 둘 중 하나만 답해도 되며, `왜 구독자가 늘지 않을까?` 같은 거친 질문이 있으면 business framing을 강제로 먼저 거치지 않고 `cool-data-key-question`에서 검증 가능한 질문으로 다듬습니다.

각 스킬은 하나의 작업에만 집중하며, 필요한 정보는 한 번에 하나의 고레버리지 질문으로 확인합니다. 지표는 분자·분모·기간·단위·집계·제외 규칙을 명시하고, 시각화는 차트 안의 축 제목과 하단 수치 해석, PPT의 방법론 주석을 포함합니다.

`cool-data-issue-tree`는 완성된 모든 트리를 반응형 인터랙티브 HTML로 보여줍니다. 별도 시각화 분석 스킬로 분리하지 않고, 이슈트리가 MECE 구조와 노드별 분석 질문을 소유하며 `visualize`를 렌더링 도구로 사용합니다.

예시:

```text
무료체험 전환율 하락 문제의 비즈니스 목표와 의사결정 맥락을 정리해줘.
이 문제를 MECE 이슈트리로 만들고, 각 리프에 분석 Key Question을 붙여줘.
Meta 유입 사용자의 유료 전환율이 6월에 유의하게 하락했는지 검증할 질문을 정의해줘.
전환율을 코호트 기준과 일별 기준으로 계산하면 무엇이 달라져?
이 데이터에서 이탈 원인을 재현 가능하게 분석해줘.
분석 결과를 임원용 PPT 스토리라인으로 만들어줘.
```

---

# Cool Data Analyst

A collection of focused business-analysis skills, rather than one rigid end-to-end workflow.

| Needed artifact | Skill |
|---|---|
| Why analysis is needed: goal, problem, decision context | `cool-data-business-framing` |
| Testable analytical Key Question | `cool-data-key-question` |
| Responsive HTML MECE issue tree from a goal/problem or question | `cool-data-issue-tree` |
| Metric selection and calculation contract | `cool-data-metric-design` |
| Reproducible preprocessing and analysis | `cool-data-analysis` |
| Dashboard, PPT, web visual, and decision story | `cool-data-storyline` |

`cool-data-analyst` is a lightweight router. A business goal says *why* analysis matters; an analytical Key Question says *what proposition data must test*. Goal-led work becomes `business framing → issue tree → leaf questions`; question-led work starts directly with the analytical question. Each skill asks one high-leverage question at a time and produces a traceable analytical artifact.

In a cold start with data but no stated purpose, the router asks for both the decision to change and the user's current analytical curiosity in one intake. Either answer is enough. A rough question seed routes directly to `cool-data-key-question` for refinement instead of forcing business framing first.

`cool-data-issue-tree` renders every completed tree as responsive interactive HTML while retaining ownership of the MECE logic, node structure, and leaf-level analytical questions. The shared `visualize` skill remains the rendering mechanism rather than a separate analysis stage.

---

## Claude (Claude Code / Cowork)

This repo also ships a Claude plugin marketplace under `.claude-plugin/` and
`plugins/cool-data-analyst/`, packaging the same six skills for Claude Code
and Cowork (Codex-only `agents/openai.yaml` files are excluded from the
Claude package).

```
/plugin marketplace add halinote/cool-data-analyst
/plugin install cool-data-analyst@cool-data-analyst-marketplace
```
