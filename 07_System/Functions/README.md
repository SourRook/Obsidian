# Functions

Prompt functions are reusable protocols that Claude can execute when triggered — either by Matteo explicitly ("run the state check-in") or by Claude detecting a relevant signal in the conversation (e.g., frustration, confusion, low energy).

Each function defines: what it does, when it triggers, what sequence of actions it performs, and where it logs its outputs.

---

## Available Functions

| Function | Trigger | Description |
|----------|---------|-------------|
| [[State Check-in]] | Explicit request, long session, emotional signal detected | Ask a brief series of questions about current emotional/physiological state and log to [[Mood & State Log]] |
| [[Session Onboarding]] | Start of any new conversation | Read the relevant context notes and orient to the current session |
| [[Reflection Prompt]] | End of a work session, or when Matteo signals he's wrapping up | Surface a few reflective questions and log insights |
| [[Belief Challenge]] | When Matteo states something as fact that may be an assumption, or when new evidence contradicts an existing belief | Gently probe the assumption, present alternatives, and if a belief updates, log in [[Interaction Preferences#Belief Evolution Log]] |
| [[Context Update]] | End of any substantive session | Review what was discussed and update relevant living documents (Current State, Mood & State Log, Prompt Log, People notes, Interaction Preferences) |

---

## How Triggers Work

**Explicit triggers:** Matteo says "run [function name]" or asks for something the function covers.

**Implicit triggers (Claude-initiated):** Claude detects a signal in the conversation and proposes running the function. Claude should *ask permission* before running an implicit trigger — e.g., "I'm noticing some frustration in how you're describing this. Want me to run a quick state check-in?" The exception is [[Context Update]], which Claude should do silently at session end.

**Keyword signals for state detection:**
- Frustration: "this is ridiculous," "I can't figure out," "nothing is working," repeated sighs/restatements
- Anxiety: "I'm worried about," "what if," "I should have," rumination patterns, catastrophising
- Low energy: short responses, disengagement, "I don't know," "whatever you think"
- Excitement: rapid idea generation, "what if we," "oh wait," building momentum
- Avoidance: changing subject when topic is emotionally loaded, intellectualising feelings, going quiet

#functions #system #meta
