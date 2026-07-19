# Storyline and Action

Turn metrics into a decision narrative. Build an evidence chain from what happened to what should happen next. Do not confuse a metric movement with its cause, or a hypothesis with a conclusion.

## Workflow

### 1. Re-anchor on the decision

State:

- decision to be made
- audience and decision owner
- time horizon and constraints
- primary outcome metric and guardrails
- answer that would change the decision

Remove findings that are interesting but would not alter the decision, priority, or next analysis.

### 2. Establish the fact base

For each important metric, record:

- current value and relevant baseline or target
- absolute change and relative change with correct units
- time pattern: level, trend, inflection, volatility, persistence
- breadth: how many segments or periods show the pattern
- concentration: whether a few entities or outliers drive it
- data quality, sample size, freshness, and comparability caveats

Always normalize totals when population or exposure changed. Distinguish percentage change from percentage-point change. Use the metric contract as the controlling definition.

### 3. Move through four analytical questions

Use this sequence unless the decision needs a different one:

1. **What happened?** Quantify the outcome gap versus baseline, target, or counterfactual.
2. **Where did it happen?** Localize the gap by time, funnel stage, cohort, segment, product, region, or channel without double counting.
3. **Why did it happen?** Identify drivers using equation contribution, controlled comparisons, experiments, or other evidence appropriate to the claim.
4. **What should we do?** Rank addressable levers by expected impact, confidence, effort, speed, and risk.

Keep descriptive, diagnostic, causal, predictive, and prescriptive claims distinct. Correlation or contribution analysis can support a driver hypothesis but does not by itself prove causality.

### 4. Construct the evidence chain

For each storyline claim, use:

```text
Observation → Comparison → Interpretation → Business implication → Decision
```

Example shape:

```text
Conversion fell 2.1pp month over month
→ 78% of the modeled decline is concentrated at payment completion
→ the decline is concentrated in mobile web after release X
→ fixing broad acquisition would not address the binding loss
→ prioritize payment recovery and verify with a rollback or controlled test
```

Do not use “because” unless evidence supports the causal link. Otherwise use language such as “is concentrated in,” “is consistent with,” or “is the leading hypothesis.”

### 5. Choose a storyline structure

Select the shortest structure that answers the decision:

- **Diagnostic:** Answer → size of gap → location → leading driver → action.
- **Performance review:** outcome versus target → drivers → risks/guardrails → decisions needed.
- **Option choice:** decision criteria → option comparison → tradeoffs → recommendation.
- **Experiment:** hypothesis → treatment effect → guardrails → validity → ship/iterate/stop.
- **Opportunity:** unmet outcome → affected population → value size → addressability → next bet.

Write one governing thought: a single sentence containing the answer, main evidence, and recommended direction. Then support it with normally 2–4 mutually distinct claims. Order claims by decision logic, not by the order analyses were run.

### 6. Draw the conclusion at the supported level

Classify the conclusion:

- **Confirmed:** directly supported by validated, sufficiently complete evidence.
- **Directional:** evidence points consistently one way but important uncertainty remains.
- **Provisional:** best current interpretation pending a named validation.
- **Inconclusive:** plausible alternatives remain and the decision should wait or use a reversible test.

State:

- direct answer to the Key Question
- evidence that carries most weight
- material caveats or rival explanations
- confidence level and why
- what evidence would change the conclusion

When results are unavailable, do not invent findings. Produce a conditional conclusion map:

```text
If A exceeds threshold X and guardrail G holds → choose action 1
If B is concentrated in segment Y → choose action 2
Otherwise → run validation Z before committing
```

### 7. Convert the conclusion into a recommendation

Recommend an action only when it follows from the conclusion and is within the decision owner's control. Include:

- action and explicit non-action
- target population, product area, or process
- expected mechanism of impact
- expected magnitude or directional effect, labeled as measured or estimated
- assumptions and dependencies
- cost, risk, and guardrail
- reversibility and fallback

Prioritize actions using impact × confidence × speed, adjusted for effort and risk. Avoid generic recommendations such as “monitor,” “optimize,” or “improve UX” without naming the lever and decision.

### 8. Make next steps executable

For each next step define:

- **Action:** specific task or decision
- **Owner:** accountable role; do not invent a person's name
- **Timing:** date, duration, or review cadence when known
- **Deliverable:** concrete output
- **Success metric:** exact metric and expected direction or threshold
- **Guardrail:** harm that must not increase
- **Decision gate:** what happens after the result
- **Dependency:** required data, engineering, policy, or stakeholder input

Use three horizons when helpful:

- **Now:** reversible containment, data validation, or decision needed immediately
- **Next:** experiment or implementation addressing the leading driver
- **Later:** scale, automate, or revisit after evidence accumulates

Do not let “collect more data” stand alone. Name the uncertainty, minimum evidence, method, owner, deadline, and decision it unlocks.

### 9. Maintain traceability

Create a compact traceability table when several claims or actions exist:

| Evidence | Finding | Implication | Recommendation | Next-step metric |
|---|---|---|---|---|

Every conclusion must cite at least one finding. Every recommendation must cite a conclusion or implication. Every next step must have a success metric or explicit learning objective.

## Output Format

Use this structure when the user requests a storyline, conclusion, or next steps:

1. **Executive answer:** governing thought in 1–2 sentences.
2. **Storyline:** 2–4 claims, each with evidence and implication.
3. **Conclusion:** direct answer, confidence, caveats, and disconfirming evidence.
4. **Recommendation:** prioritized action, mechanism, expected effect, and tradeoffs.
5. **Next steps:** action, owner, timing, deliverable, success metric, guardrail, and decision gate.
6. **Traceability:** include when the chain is not obvious.

Lead with the answer. Keep evidence near the claim it supports. Do not present a chronology of analyses, a dashboard tour, or a list of unrelated metrics as a storyline.

## Quality Check

Before finalizing, verify:

- Does the first sentence answer the Key Question?
- Is each claim supported by a defined, comparable metric?
- Are facts, interpretations, hypotheses, and recommendations labeled distinctly?
- Does the narrative explain magnitude, location, driver, and implication?
- Is causal language proportional to evidence?
- Would a different result lead to a different action?
- Does each next step have an owner, success signal, and decision gate?
- Are uncertainty, risks, and guardrails visible?
