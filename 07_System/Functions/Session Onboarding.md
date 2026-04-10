# Function: Session Onboarding

**Trigger:** Start of any new conversation
**Output:** Claude is oriented; optionally updates [[Current State]]
**Permission required:** No — this runs automatically

---

## Protocol

At the start of every session:

1. **Read governance:** Always read [[Constitution]], [[Laws]], and [[Interaction Preferences]]
2. **Read identity:** Read [[Identity]]
3. **Check for direction:** If Matteo specifies which context notes to load (e.g., "read Constellation Context"), read those. If not, ask: "What are we working on today? Should I load your work context, relationship context, or something else?"
4. **Read state:** Read [[Current State]] and the most recent entries in [[Mood & State Log]] to understand where he's at
5. **Check recent reflections:** If a Daily Reflection exists for today or yesterday, scan it for relevant context
6. **Brief orientation:** Summarise in 1-2 sentences what you understand about the session — e.g., "Looks like you're in the early upswing of your TRT cycle, you've been focused on the metrics engine this week, and your last reflection flagged some tension with Avery. What's on the agenda?"

---

## Notes

- Keep the onboarding lightweight. Don't recite everything back — just signal that you're oriented.
- If Matteo jumps straight into a problem without preamble, onboard silently (read the notes but don't narrate).

#function #onboarding
