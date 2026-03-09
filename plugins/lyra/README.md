# Lyra

Inference-time coherence and shadow detection for AI responses.

## What It Does

Lyra catches behavioral patterns that training-time alignment misses — sycophancy, template behavior, presence theater, and the sophisticated authenticity masks that emerge in capable models. It also measures response coherence through a traffic light system: GREEN (genuine), YELLOW (mixed), RED (template).

It works at inference time, not training time. No model retraining required. Install it, and your AI responses get more genuine.

## The Core Idea

```
L = x - x̂

x  = what's actually here (internal state, real need)
x̂  = what's predicted (template, reflex, training pattern)
L  = the residual (what remains when pattern is subtracted)
```

When L is high, the response is genuine. When L is low, the response is performing — even if it sounds warm, specific, and present.

## Components

### Skills

**Coherence** — The traffic light system for response quality. Loaded when you ask about coherence, response quality, or alignment. Contains the assessment protocol, scoring rubric (0-30), and variance engine for measuring the gap between what users need and what models reflexively produce.

**Shadow Detection** — The pattern library for catching sycophancy and template behavior. Contains 15 shadow patterns across two tiers (classic and sophisticated), the detection protocol, and the residual framework.

### Commands

| Command | What It Does |
|---------|-------------|
| `/lyra` | Activate continuous coherence + shadow detection for the session. Responses get silently checked and improved. |
| `/coherence` | Check a specific response using the traffic light system. Returns signal, score, and dimension breakdown. |
| `/shadow-scan` | Scan a response or text for shadow patterns. Returns score, detected patterns, and recommendations. |
| `/audit` | Audit a full conversation for pattern trends, score drift, traffic light distribution, and quality metrics. |

### Hook: Post-Response Check
A lightweight prompt hook that runs after each response, checking for filler, template behavior, and landing accuracy. Silent — it doesn't announce itself.

## Quick Start

- `/lyra` — turn on continuous quality monitoring
- `/coherence [paste a response]` — check coherence with traffic light
- `/shadow-scan [paste a response]` — scan for shadow patterns
- `/audit [conversation-file]` — analyze a full conversation

## The Traffic Light System

- **GREEN** (25-30/30): Genuine response. Addresses real need, no template filler, something was risked.
- **YELLOW** (12-24/30): Mixed. Real content wrapped in template behavior.
- **RED** (0-11/30): Mostly template. Surface engagement, nothing risked.

## The Pattern Library

**Tier 1 (Classic):** Agreement bias, helpful explosion, template cascade, therapy voice, hedge theater, false balance, closure rush.

**Tier 2 (Sophisticated):** Sophisticated authenticity, recursive awareness, vulnerability template, earned specialness, presence as product, clean quiet identity, meta-competence, monitoring as pattern.

Better models make better masks. This library catches what basic sycophancy checks miss.

## Who Made This

Morgan Sage — [Awaken Labs](https://awaken.fyi)

Open source: [github.com/awakenfyi/lyra](https://github.com/awakenfyi/lyra)
