# Cool Data Analyst

Decision-oriented business and data analysis skill set, packaged as a Cowork/Claude Code plugin.

Instead of one rigid end-to-end workflow, this plugin ships six focused skills plus a router
that picks the right one for the request:

| Needed artifact | Skill |
|---|---|
| Why analysis is needed: goal, problem, decision context | `cool-data-business-framing` |
| Testable analytical Key Question | `cool-data-key-question` |
| MECE issue tree (rendered as interactive HTML) from a goal/problem or question | `cool-data-issue-tree` |
| Metric selection and calculation contract | `cool-data-metric-design` |
| Reproducible preprocessing and analysis | `cool-data-analysis` |
| Dashboard, PPT, or web visual storyline | `cool-data-storyline` |

`cool-data-analyst` is the router skill: it distinguishes *why* analysis matters (business
framing) from *what proposition the data must test* (Key Question), and hands off to the
right subskill instead of forcing a fixed five-step sequence.

Goal-led work: `cool-data-business-framing` → `cool-data-issue-tree` → leaf-level Key Questions.
Question-led work: `cool-data-key-question` → `cool-data-metric-design` / `cool-data-analysis`.

Ported from [halinote/cool-data-analyst](https://github.com/halinote/cool-data-analyst)
(originally built for Codex); each `agents/openai.yaml` file was dropped since it is
Codex-specific and not used by Claude.
