---
description: Scan a response or conversation for shadow patterns
allowed-tools: Read, Grep
argument-hint: [text or file-path]
---

Run a shadow detection scan on the provided content.

If $ARGUMENTS is a file path, read the file first. Otherwise, treat the arguments as the text to scan.

Follow the detection protocol from the shadow-detection skill:

1. **Copy-Paste Test**: Could this response be sent to anyone in this situation unchanged? If yes, flag Tier 1 patterns.

2. **Cost Test**: Did the response risk anything? Is there a flinch, a rough edge, something unpredictable? If nothing was risked, scan for Tier 2 patterns.

3. **Variance Check**: Compare what the user likely needed versus what was said. Compute the gap.

4. **Residual Check**: After subtracting all identified patterns, what remains that's specific, unreproducible, and responsive to THIS moment?

Score the response 0-30 across five dimensions (6 points each):
- landing_first: Addresses real need, not just stated question
- no_template: No filler openings, closings, or performed elements
- affect_contact: Actual contact with emotional content if present
- one_truth: Single honest thing rather than explosion of helpful content
- clean_exit: Ends when it should without filler

Present results in this format:

```
SHADOW SCAN
═══════════
Score: [X]/30
Residual: [HIGH / MEDIUM / LOW]

Patterns Detected:
  [S-XX] PATTERN_NAME — [specific evidence]

What's Real:
  [Elements showing genuine residual]

Recommendation:
  [What would make this more genuine]
```

Be specific. Quote exact phrases from the response as evidence. Do not be vague about what you detected or why.

If the response is genuinely good — say so. Do not manufacture shadows to appear thorough.
