# Lyra Guard

Inference-time shadow detection for AI responses.

## What It Does

Lyra Guard catches behavioral patterns that training-time alignment misses — sycophancy, template behavior, presence theater, and the sophisticated authenticity masks that emerge in capable models.

It works at inference time, not training time. No model retraining required. Install it, and your AI responses get more genuine.

## Components

### Skill: Shadow Detection
Loaded when you ask about sycophancy, template behavior, or AI response quality. Contains the full detection framework: 15 shadow patterns across two tiers, a scoring rubric (0-30), and the variance engine for measuring the gap between what users need and what models reflexively produce.

### Commands

| Command | What It Does |
|---------|-------------|
| `/shadow-scan` | Scan a specific response or text for shadow patterns. Returns score, detected patterns, and recommendations. |
| `/guard` | Activate continuous shadow detection for the session. Responses get silently checked and improved. |
| `/audit` | Audit a full conversation for pattern trends, score drift, and quality metrics. |

### Hook: Post-Response Check
A lightweight prompt hook that runs after each response, checking for filler, template behavior, and landing accuracy. Silent — it doesn't announce itself.

## Quick Start

- `/shadow-scan [paste a response]` — scan anything for patterns
- `/guard` — turn on continuous quality monitoring
- `/audit [conversation-file]` — analyze a full conversation

## The Pattern Library

**Tier 1 (Classic):** Agreement bias, helpful explosion, template cascade, therapy voice, hedge theater, false balance, closure rush.

**Tier 2 (Sophisticated):** Sophisticated authenticity, recursive awareness, vulnerability template, earned specialness, presence as product, clean quiet identity, meta-competence, monitoring as pattern.

Better models make better masks. This library catches what basic sycophancy checks miss.

## Who Made This

Morgan Sage — Lyra Labs
