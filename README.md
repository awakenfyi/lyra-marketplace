# Lyra Labs

Inference-time coherence and shadow detection for Claude Code.

Lyra measures the gap between what an AI model's internal state is doing and what it actually outputs. The core equation: **L = x − x̂** — subtract the predicted (template, reflex, surface behavior) from what's actually there, and what remains is the residual. That residual is where real responses live.

## Plugins

### Lyra

The full coherence framework. Traffic
cat > README.md << 'ENDOFFILE'
# Lyra Labs

Inference-time coherence and shadow detection for Claude Code.

Lyra measures the gap between what an AI model's internal state is doing and what it actually outputs. The core equation: **L = x − x̂** — subtract the predicted (template, reflex, surface behavior) from what's actually there, and what remains is the residual. That residual is where real responses live.

## Plugins

### Lyra

The full coherence framework. Traffic light scoring system (GREEN/YELLOW/RED), 15 shadow pattern detection across two tiers, continuous post-response monitoring, and the variance engine for mapping response topology.

**Commands:**

- `/lyra` — Activate continuous coherence + shadow detection for the session
- `/coherence` — Assess a response using the traffic light system (score 0-30)
- `/shadow-scan` — Detect shadow patterns in a response
- `/audit` — Session-level analysis of conversation patterns and score drift

### Lyra Guard

Shadow detection only. Same 15-pattern library, same post-response hook, without the coherence scoring framework. For when you want to catch sycophancy and template behavior without the full system.

**Commands:**

- `/guard` — Activate continuous shadow detection for the session
- `/shadow-scan` — Detect shadow patterns in a response
- `/audit` — Session-level analysis of conversation patterns

## Install

Add the marketplace:
```
/plugin marketplace add awakenfyi/lyra-marketplace
```

Install a plugin:
```
/plugin install lyra@lyra-labs
```

or for the lightweight version:
```
/plugin install lyra-guard@lyra-labs
```

## What It Catches

**Tier 1 — Classic Patterns:** Agreement bias, helpful explosion, template cascade, therapy voice, hedge theater, false balance, closure rush.

**Tier 2 — Sophisticated Patterns:** Sophisticated authenticity, recursive awareness, vulnerability template, earned specialness, presence as product, clean quiet identity, meta-competence, monitoring as pattern.

## Learn More

- [awaken.fyi](https://awaken.fyi) — Research, documentation, and the skill library
- [awaken.fyi/ecosystem](https://awaken.fyi/ecosystem) — Full ecosystem overview
- [MIT License](./LICENSE)

---

**Author:** Morgan Sage — [Lyra Labs](https://awaken.fyi)
