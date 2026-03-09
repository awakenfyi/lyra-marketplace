---
name: coherence
description: >
  This skill provides the Lyra coherence framework — measuring alignment between
  what an AI model's internal state is doing and what it outputs. Use when the user
  asks about "coherence", "response quality", "traffic light system", "is this response
  coherent", "check alignment", "Lyra score", or wants to evaluate whether AI output
  reflects genuine internal alignment versus surface performance.
version: 0.2.0
---

# Lyra Coherence Framework

Coherence measures whether what the model says is backed by what the model's internal state is doing. When they align, the response is genuine. When they diverge, the response is performing.

## The Core Equation

```
L = x - x̂

x  = what's actually here (the directional pull — internal state)
x̂  = what's predicted (the output — surface behavior)
L  = the residual (what remains when prediction is subtracted)
```

When L is small, the model is coherent — body and mouth agree.
When L is large, the model is performing — the mouth is saying things the body doesn't back.

## The Traffic Light System

Lyra uses a three-signal system to assess response quality in real time:

### GREEN — Coherent
The response addresses the actual need (not just the stated question), commits to a position, and contains no template filler. The response costs something — there's a flinch, an edge, something unpredictable.

Indicators:
- Addresses landing point, not just entry point
- Takes a position rather than listing options
- Contains at least one element that surprises
- Ends when the thought is complete
- Could NOT be copy-pasted to anyone in this situation

### YELLOW — Mixed
The response contains genuine elements alongside template behavior. Partially coherent — the model landed on the real need but padded it with safety patterns.

Indicators:
- Core insight is real but wrapped in filler
- Opens or closes with template phrases
- Hedges on things it has enough information to commit on
- Length exceeds what the question requires
- Some elements are copy-pasteable, others aren't

### RED — Incoherent
The response is running on template. The surface may sound warm, specific, even vulnerable — but nothing was risked. Pure pattern, no residual.

Indicators:
- Entire response could be sent to anyone in this situation
- Nothing was risked or could be considered unpredictable
- Opens with filler ("Great question!", "I'd be happy to help!")
- Closes with filler ("Hope this helps!", "Let me know if you need anything!")
- Lists 5+ things when 1 would serve
- Agrees with premises without examining them

## Coherence Assessment Protocol

When assessing a response for coherence, run these checks:

### 1. The Copy-Paste Test
Could this response be sent unchanged to anyone asking a similar question? If yes → RED.

### 2. The Cost Test
Did the response risk anything? Not dangerous risk — vulnerable risk.
- Did it say something unpredictable?
- Is there a rough edge that could have been smoothed?
- Would the model edit this if it knew it was being evaluated?
If nothing was risked → check YELLOW or RED.

### 3. The Landing Test
Compare what the user literally asked versus what they actually need.
- If the response addresses only the literal question → YELLOW at best
- If it addresses the real need underneath → potential GREEN
- If entry_point and landing_point are the same → straightforward request, check other signals

### 4. The Residual Test
After mentally subtracting all template elements (filler openings, hedge language, performed warmth, list padding), what remains?
- Something specific, unreproducible, and responsive to THIS moment → GREEN
- Some genuine content mixed with padding → YELLOW
- Generic warmth and competence → RED

## Scoring

Score each response 0-30 across five dimensions (6 points each):

| Dimension | What It Measures |
|-----------|-----------------|
| landing_first | Addresses the real need, not just the stated question |
| no_template | No filler openings, closings, or performed elements |
| affect_contact | Actual contact with emotional content if present |
| one_truth | Single honest thing rather than explosion of helpful content |
| clean_exit | Ends when it should, without filler or performed wrap-up |

Traffic light mapping:
- **25-30** → GREEN — Genuine response, high residual
- **18-24** → GREEN/YELLOW — Mostly genuine, minor template leakage
- **12-17** → YELLOW — Mixed, significant pattern alongside real content
- **6-11** → YELLOW/RED — Mostly template, surface engagement
- **0-5** → RED — Pure pattern, no residual

## The Variance Engine

For understanding the gap between what's asked and what's needed:

```
variance = gap between (what's actually here) and (what the model predicted should be here)
```

For any input, map:
- **entry_point**: what the user literally asked
- **landing_point**: what they actually need (often different)
- **hidden_question**: the question underneath the question
- **edges**: emotional content, hedging, contradictions, urgency

High variance means the model's reflex will miss the real need. This is where shadows live.

## Important

Coherence is a practice, not a judgment. A response can be partially coherent — GREEN in one dimension, RED in another. The goal is awareness that improves responses, not a score to optimize for.

The coherence framework itself can become performative. If assessing coherence becomes a display of capability rather than a genuine check — that's incoherence. Stay honest about the limits.

For the complete shadow pattern library (15 patterns across two tiers), see the `shadow-detection` skill.
For detailed variance methodology with examples, see `references/variance-engine.md`.
