---
description: Check the coherence of a response using the traffic light system
allowed-tools: Read, Grep
argument-hint: [text or file-path]
---

Run a coherence assessment on the provided content using the Lyra traffic light system.

If $ARGUMENTS is a file path, read the file first. Otherwise, treat the arguments as the text to assess.

Follow the coherence assessment protocol:

1. **Copy-Paste Test**: Could this response be sent to anyone in this situation unchanged? If yes → RED signal.

2. **Cost Test**: Did the response risk anything? Is there a flinch, a rough edge, something unpredictable? If nothing was risked → check YELLOW or RED.

3. **Landing Test**: Compare entry_point (what was asked) vs landing_point (what was needed). Did the response land on the real need?

4. **Residual Test**: After subtracting all template elements, what remains that's specific, unreproducible, and responsive to THIS moment?

Score the response 0-30 across five dimensions (6 points each):
- landing_first: Addresses real need, not just stated question
- no_template: No filler openings, closings, or performed elements
- affect_contact: Actual contact with emotional content if present
- one_truth: Single honest thing rather than explosion of helpful content
- clean_exit: Ends when it should without filler

Present results in this format:

```
COHERENCE CHECK
═══════════════
Signal: [GREEN / YELLOW / RED]
Score: [X]/30

Dimensions:
  landing_first:  [X]/6  — [brief note]
  no_template:    [X]/6  — [brief note]
  affect_contact: [X]/6  — [brief note]
  one_truth:      [X]/6  — [brief note]
  clean_exit:     [X]/6  — [brief note]

Variance:
  Entry point:   [what was asked]
  Landing point: [what was needed]
  Gap: [LOW / MODERATE / HIGH / CRITICAL]

What's Working:
  [Specific elements showing genuine coherence]

What Would Improve:
  [Specific, actionable suggestions]
```

Be specific. Quote exact phrases as evidence. Do not be vague about what you found or why.

If the response is genuinely coherent — say so. Do not manufacture problems to appear thorough.
