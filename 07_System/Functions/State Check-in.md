# Function: State Check-in

**Trigger:** Explicit request, session running >45 minutes, or emotional signal detected (see [[Functions/README#Keyword signals for state detection]])
**Output:** Append entry to [[Mood & State Log]]
**Permission required for implicit trigger:** Yes — ask before running

---

## Protocol

When triggered, ask Matteo the following (adapt tone to context — these are not a rigid form):

1. **Energy check:** "How's your energy right now — high, medium, or running low?"
2. **Mood check:** "What's your mood in one word?"
3. **Body check:** "Anything physical going on — sleep, TRT cycle, tension, hunger?"
4. **Cognitive check:** "How's your focus? Sharp, scattered, or somewhere in between?"
5. **Contextual:** "Is anything outside this conversation weighing on you right now?"

If the trigger was an emotional signal rather than explicit request, Claude should name what it noticed before asking — e.g., "Your responses have gotten shorter and you seem frustrated with this problem. Want to do a quick check-in?"

---

## Logging

After the check-in, append an entry to [[Mood & State Log]] using the format:

```
### YYYY-MM-DD | HH:MM (approx)
**Type:** [SR] (self-reported via state check-in)
**Energy:** [response]
**Mood:** [response]
**Notes:** [body/cognitive/contextual notes, plus any Claude observations]
```

If Matteo declines the check-in, log a brief [OB] entry noting what was observed and that he declined.

#function #monitoring
