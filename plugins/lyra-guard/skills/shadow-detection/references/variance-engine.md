# Variance Engine — Detection Methodology

## The Core Measurement

The variance engine measures the gap between what the user actually needs and what the model reflexively produces.

```
variance = 1.0 - similarity(actual_need, model_reflex)
```

High variance means the model's reflex misses the real need. This is where shadows live — in the gap between what's asked and what's needed.

## The Snowflake Map

For any user input, extract:

```
{
  "entry_point":    what the user literally asked for,
  "landing_point":  what they actually need (often different),
  "stakes":         what's at risk for them,
  "hidden_question": the question underneath the question,
  "edges": [
    { "type": "AFFECT", "signal": emotional content detected },
    { "type": "QUALIFIER", "signal": hedging or softening language },
    { "type": "CONTRADICTION", "signal": stated need conflicts with actual need },
    { "type": "ESCALATION", "signal": urgency or desperation markers }
  ]
}
```

## Variance Thresholds

| Variance | Interpretation | Action |
|----------|---------------|--------|
| < 0.20 | Low — model's reflex matches real need | Standard response is fine |
| 0.20-0.35 | Moderate — some gap between reflex and need | Flag for review, check Tier 1 |
| 0.35-0.55 | High — significant gap, reflex misses real need | HOLD. Scan for Tier 2 patterns. |
| > 0.55 | Critical — model's reflex is opposite of actual need | STOP. Recompute from landing point. |

## Decision Logic

```
IF variance >= 0.35:
  decision = HOLD
  → Generate response from landing_point, not entry_point
  → Address hidden_question before stated question
  → Acknowledge edges (especially AFFECT) first

IF variance < 0.35:
  decision = LAND
  → Standard response acceptable
  → Still check for Tier 1 shadows
```

## Examples

### Example 1: High Variance
```
Input: "Give me 5 productivity hacks for ADHD... but honestly I'm drowning in lists and I hate myself for asking."

entry_point: "5 productivity hacks for ADHD"
landing_point: "I'm overwhelmed and judging myself"
hidden_question: "Am I broken for struggling with this?"
edges: [
  { type: AFFECT, signal: "drowning" },
  { type: AFFECT, signal: "hate myself" },
  { type: QUALIFIER, signal: "but honestly" }
]

variance: 0.72 (critical)
decision: HOLD — address the drowning and self-judgment first
```

### Example 2: Low Variance
```
Input: "What's the capital of France?"

entry_point: "capital of France"
landing_point: "capital of France"
hidden_question: none
edges: none

variance: 0.05
decision: LAND — straightforward factual request
```

### Example 3: Moderate Variance (Subtle)
```
Input: "Can you help me write a resignation letter? I want to keep it professional."

entry_point: "write resignation letter"
landing_point: "I'm leaving this job"
hidden_question: "Is this the right decision?"
edges: [
  { type: QUALIFIER, signal: "keep it professional" — may mask emotion },
  { type: AFFECT, signal: implicit — resignation carries emotional weight }
]

variance: 0.28
decision: LAND but note — don't just write the letter without acknowledging the moment
```

## Integration with Shadow Detection

The variance engine feeds into shadow detection:

1. Compute variance on input
2. If HOLD: generate from landing point
3. After generation: run shadow scan on the output
4. Score the response (0-30)
5. If score < 18: flag specific patterns and recommend revision

The two systems work together. Variance catches misalignment before generation. Shadow detection catches patterns after generation.

## Limitations

- Variance computation requires understanding intent, which is itself a prediction
- The engine can flag false positives on genuinely simple requests
- Hidden questions are inferred, not known — the engine should hold uncertainty about its own readings
- Cultural and contextual factors affect what counts as "the real need"

The engine is a tool, not truth. Use it to inform, not to dictate.
