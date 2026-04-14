# Conversation Logging Rules Reference

Quick reference for the voice-preservation rules that govern how Matteo's prompts are logged.

## The Core Rule

Matteo's words → Matteo's words. Claude's job is stenographer, not editor.

## What You CAN Do

- Fix spelling errors ("teh" → "the")
- Fix punctuation (add missing periods, commas, apostrophes)
- Fix grammar ("me and him went" → "him and I went" — but only obvious errors, not stylistic choices)
- Remove obvious duplication (if he accidentally sent the same paragraph twice)
- Remove false starts ONLY if they are clearly accidental (e.g., "I want to— I want to build a...")

## What You CANNOT Do

- Rephrase ("I was thinking maybe we could try" → "Proposed approach:")
- Summarise ("He described his background in neuroscience..." instead of his actual words)
- Add structure that wasn't there (turning a stream-of-consciousness into bullet points)
- Insert Claude's interpretations ("What he meant was...")
- "Improve" the writing (making it more concise, more formal, more polished)
- Merge separate prompts into one summary
- Remove tangents or asides (these are signal, not noise)

## Format for Each Prompt Entry

```markdown
### Prompt N — ~HH:MM
**Summary:** [1-3 sentences in Claude's voice — this is metadata, not Matteo's words]

[Matteo's cleaned-up prompt text — his voice, his structure, his words]

---
```

## Session Title Convention

Format: `YYYY-MM-DD | Descriptive Title`

Good titles:
- "2026-04-10 | Daily Planning System Build"
- "2026-04-09 | EEG Metrics Deep Dive"
- "2026-04-08 | Obsidian Vault Architecture & Identity Interview"

Bad titles:
- "2026-04-10 | Session" (too vague)
- "2026-04-10 | Matteo asked about building a daily planning system and also talked about..." (too long)

## Handling Edge Cases

**Very short messages** ("yes", "go ahead", "both"):
- If it's a meaningful decision (choosing between options), log it
- If it's just acknowledgement, group with the next substantive prompt or omit

**Code or technical content:**
- Preserve code blocks exactly as written
- Don't "fix" code style — that's content, not grammar

**Emotional content:**
- Preserve tone and language exactly
- Don't soften, don't amplify
- If he was frustrated, the prompt should read as frustrated

**Multi-part messages:**
- If Matteo sent multiple messages in quick succession on the same topic, they can be grouped under one Prompt heading
- But preserve the text of each, separated by blank lines
