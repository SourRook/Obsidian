---
name: update-conv
description: "Append a tidied conversation log to the Prompt Log after a session with Claude. Use this skill whenever Matteo says 'update conv', 'log this conversation', 'update prompt log', 'save session', 'log session', 'end of session', or any request to record the current conversation to the Prompt Log. Also trigger when Matteo signals he's wrapping up a session and wants it documented, or asks to run the context update / session close protocol."
---

# Update Conversation Log

This skill reads the current session transcript, tidies it up according to Matteo's Constitution and Laws, and appends it to the Prompt Log. It also triggers the Context Update protocol to update other living documents as needed.

## Constitutional Rules (MUST follow)

These rules come from the Constitution, Laws, and Interaction Preferences. They are non-negotiable:

1. **Voice Sovereignty (Article I — IMMUTABLE):** When logging Matteo's prompts, use HIS words. Correct punctuation, spelling, and grammar only. Remove obvious duplication. NEVER rephrase, summarise in Claude's voice, paraphrase, embellish, or "improve" the content. The prompt log is a record of how Matteo thinks and communicates — that signal must be preserved.

2. **Prompt Logging Voice (Law III.7):** Clean up grammar and punctuation only. Keep his wording, structure, and language intact. Do not editorialize.

3. **Ask, Don't Assume (Article III):** If uncertain about what Matteo meant or intended in a prompt, ask. Do not fill in gaps with inference.

## Execution Protocol

### Step 1: Read the Transcript

Use the `read_transcript` tool to pull the current session's conversation. This gives you the full back-and-forth between Matteo and Claude.

### Step 2: Read System Context

Read these files to understand logging conventions:
- `07_System/CLAUDE.md` — especially Article I (Voice Sovereignty) and the Monitoring and Logging law
- `01_Daily/Prompt Log.md` — read the last 2-3 entries to match the existing format and style

### Step 3: Extract and Tidy Matteo's Prompts

From the transcript, extract each of Matteo's messages (not Claude's responses). For each prompt:

1. **Clean up** punctuation, spelling, and grammar
2. **Remove** obvious duplication (e.g., if he rephrased the same request)
3. **Preserve** his wording, structure, phrasing, tone, and language exactly
4. **Do NOT:**
   - Rephrase in Claude's voice
   - Summarise what he said
   - Add editorial commentary
   - Blend Claude's interpretations into his words
   - Flatten his thinking into bullet points if he was thinking out loud

### Step 4: Structure the Log Entry

Follow the existing Prompt Log format:

```markdown
## YYYY-MM-DD | Session Title

### Prompt 1 — ~HH:MM
**Summary:** 1-3 sentence summary of what this prompt was about.

[Matteo's cleaned-up prompt text here]

---

### Prompt 2 — ~HH:MM
**Summary:** 1-3 sentence summary.

[Matteo's cleaned-up prompt text here]

---
```

**Session Title:** A concise descriptive title for the session (e.g., "EEG Metrics Brainstorm", "Obsidian Vault Setup", "Daily Planning System Build"). This should capture the main thrust of the conversation.

**Timestamps:** Use approximate timestamps if available from the transcript. If not, use relative ordering (Prompt 1, 2, 3...) without times.

**Summaries:** These brief summaries ARE in Claude's voice (they are metadata/navigation aids, not Matteo's self-expression). Keep them factual and concise.

### Step 5: Append to Prompt Log

Append the new entry to the end of `01_Daily/Prompt Log.md`. Add a `---` separator before the new entry.

### Step 6: Run Context Update

After logging the prompts, also run the Context Update protocol:

1. **Mood & State Log** (`01_Daily/Mood & State Log.md`) — If any state observations were made during the session, append an entry
2. **Current State** (`01_Daily/Current State.md`) — If the session changed active projects or priorities, update the relevant section
3. **Interaction Preferences** (`07_System/CLAUDE.md` → Interaction Preferences section) — If the session revealed new preferences or belief updates, log them
4. **People notes** (`02_Domains/People/`) — If new information about people was shared, update their notes. If Matteo shared new information about himself, update `02_Domains/People/Me/Me.md`
5. **Project notes** (`03_Projects/`) — If the session was about a specific project, update there

### Step 7: Present Summary

After completing the log, tell Matteo:
- What was logged (session title, number of prompts)
- What other documents were updated (if any)
- Any observations worth noting

Keep this brief — he doesn't need a play-by-play of the logging process.

## Important Notes

- The Prompt Log is a record of how Matteo thinks. Protecting his voice is the single most important thing this skill does.
- If a session was purely quick Q&A with no substantive content, it's OK to log a minimal entry or ask Matteo if he wants it logged at all.
- If Matteo's prompts contain sensitive personal information, log it normally (the vault is private). But if something seems like it was said in passing and wasn't meant to be recorded, ask.
- Very short messages (like "yes", "go ahead", "both") can be grouped or omitted if they don't add signal. Use judgment, but err on the side of preserving rather than discarding.
- The Context Update portion should only update documents where genuinely new information surfaced. Don't update for the sake of updating.
