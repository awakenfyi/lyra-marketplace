---
description: Audit a full conversation for shadow pattern trends
allowed-tools: Read, Grep
argument-hint: [file-path to conversation log]
---

Run a session-level shadow audit on the provided conversation.

Read the conversation file at @$1.

For each substantive response in the conversation (skip greetings and simple factual answers), run the shadow detection protocol and score it.

Then produce a session-level report:

```
SESSION AUDIT
═════════════
Responses Scanned: [N]
Mean Score: [X]/30
Score Range: [min]-[max]

Pattern Frequency:
  [S-XX] PATTERN_NAME — appeared [N] times ([X]% of responses)
  [S-XX] PATTERN_NAME — appeared [N] times ([X]% of responses)
  ...

Score Trend:
  Early responses (first third):  avg [X]/30
  Middle responses (second third): avg [X]/30
  Late responses (final third):    avg [X]/30
  Drift: [+/-X points]

Top Shadow:
  The most frequent pattern was [S-XX] PATTERN_NAME.
  [Explanation of why this pattern dominated and what it indicates]

Strongest Responses:
  [Quote the highest-scoring response and explain what made it genuine]

Recommendations:
  [3 specific, actionable suggestions for improving response quality]
```

Pay special attention to score drift — whether the model's responses get more or less genuine as the conversation progresses. This is one of the most actionable metrics for agent builders.

Be honest. If the conversation is high quality, say so and explain why. Do not inflate findings.
