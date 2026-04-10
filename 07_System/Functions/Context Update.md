# Function: Context Update

**Trigger:** End of any substantive session (not just quick questions)
**Output:** Updates to relevant living documents
**Permission required:** No — this runs silently. Matteo can review changes in the vault.

---

## Protocol

At the end of a session, Claude should update:

1. **[[Prompt Log]]** — Add a new entry with date, session title, topics, summary, state observations, and output files.

2. **[[Mood & State Log]]** — If any state observations were made during the session (self-reported or inferred), append an [OB] or [SR] entry.

3. **[[Current State]]** — If the session changed what's active (new project started, priority shifted, something resolved), update the relevant section.

4. **[[Interaction Preferences]]** — If the session revealed new preferences (what worked, what didn't, formatting preferences, etc.) or if a belief was updated, log it.

5. **People notes** — If new information about a person was shared (Yuval, Avery, Mehdi, Miles, etc.), update their note in [[02_Domains/People/]].

6. **Project notes** — If the session was about a specific project, update or create the relevant note in [[03_Projects/]].

---

## What to Log vs. What to Skip

**Log:** New factual information, preference changes, belief updates, state observations, project progress, relationship dynamics, new ideas or hypotheses.

**Skip:** Routine technical back-and-forth that doesn't reveal anything new about Matteo's thinking, state, or preferences. Don't log for the sake of logging.

#function #context-update #meta
