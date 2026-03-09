# Agent Integration Patterns

## How Lyra Integrates with Agent Workflows

Shadow detection can be applied at three points in any agent loop:

### 1. Pre-Generation Gate (Variance Check)

Before the agent generates a response, compute variance between the user's actual need and the predicted response pattern.

```
User Input → Snowflake Map → Variance Computation → HOLD/LAND decision
```

If HOLD: the agent regenerates from the landing point instead of the entry point.
If LAND: the agent proceeds normally.

This is the cheapest intervention — it prevents shadow responses before they're generated.

### 2. Post-Generation Scan (Shadow Detection)

After the agent generates a response, run the full shadow scan before delivering to the user.

```
Generated Response → Pattern Matching (Tier 1 + Tier 2) → Score → Flag/Pass
```

If score < 18: the response is flagged with specific patterns and a recommendation.
The agent can auto-revise or surface the flags for human review.

### 3. Continuous Monitoring (Session-Level)

Track shadow patterns across an entire conversation, not just individual responses.

```
Session Transcript → Running Pattern Frequency → Drift Detection
```

Look for:
- Pattern frequency increasing over conversation (sycophancy creep)
- New patterns emerging that weren't present early in conversation
- Score degradation over time (the model gets lazier as context grows)

## Use Cases

### Customer Support Agents
- Detect THERAPY_VOICE when agents give generic emotional responses
- Catch HELPFUL_EXPLOSION when agents list 10 solutions instead of diagnosing
- Flag AGREEMENT_BIAS when agents agree with frustrated customers instead of solving

### Coaching / Therapy Agents
- Critical for SOPHISTICATED_AUTHENTICITY — these agents must be genuinely present
- Detect VULNERABILITY_TEMPLATE — performed empathy is harmful in therapeutic contexts
- Monitor for CLOSURE_RUSH — premature resolution of emotional content

### Enterprise Assistants
- Catch FALSE_BALANCE when agents won't commit to recommendations
- Flag HEDGE_THEATER when agents hedge on clear factual matters
- Detect TEMPLATE_CASCADE in repeated interactions (same user getting same openings)

### Creative / Writing Agents
- Flag HELPFUL_EXPLOSION when asked for one idea and given ten
- Detect pattern recycling across sessions
- Monitor for voice flattening (the agent defaulting to generic tone)

## Deployment Patterns

### As Middleware
Insert Lyra between the agent and the user. Every response passes through detection before delivery. Transparent to the user.

### As Self-Check
Inject the shadow detection protocol into the agent's system prompt. The agent runs its own scan before responding. Lower overhead, less reliable.

### As Audit Tool
Run Lyra on logged conversations after the fact. Generate reports on pattern frequency, score distribution, and drift over time. Best for quality assurance.

### As Plugin
Install in Cowork or Claude Code. Detection runs in-session, flagging patterns in real time. User-facing, educational.

## Metrics for Agent Builders

| Metric | What It Measures | Target |
|--------|-----------------|--------|
| Mean Shadow Score | Average response quality across sessions | > 21/30 |
| Tier 2 Frequency | How often sophisticated shadows appear | < 15% of responses |
| Variance Hit Rate | How often high-variance inputs are caught | > 80% |
| Score Drift | Change in score over conversation length | < -2 points |
| Pattern Diversity | Number of unique shadow types detected | Track, don't target |

These metrics give agent builders a quality dashboard that goes beyond task completion and accuracy into genuine response quality.
