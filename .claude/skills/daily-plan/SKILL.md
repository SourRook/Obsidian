---
name: daily-plan
description: "Generate a daily planning dashboard that aggregates tasks from Slack, Linear, Gmail, daily notes, and the System context files. Creates an interactive HTML dashboard and a companion Markdown summary under 01_Daily/Tasks/ with today's date. Use this skill whenever Matteo asks to 'run daily plan', 'plan my day', 'morning dashboard', 'what's on my plate today', 'daily briefing', or any request to see an overview of today's tasks, emails, and Linear issues. Also trigger when Matteo mentions wanting to see unfinished Linear tasks, emails needing responses, or a combined view of his work streams."
---

# Daily Plan Dashboard

This skill creates a comprehensive daily planning dashboard by pulling data from Matteo's connected services (Slack, Linear, Gmail) and his Obsidian vault, then generating both an interactive HTML dashboard and a companion Markdown summary.

## Context

Matteo is a founding scientist at Constellation, a neuro-AI startup. His vault lives in an Obsidian workspace with a specific folder structure (see below). The dashboard should respect the voice and formatting conventions defined in his Constitution and Laws — particularly that Claude's operational/system outputs use Claude's voice (this is appropriate here since dashboards are system artifacts, not Matteo's self-knowledge).

## Vault Structure

```
01_Daily/
  Tasks/          ← Dashboard output goes here
  Prompt Log.md
  Mood & State Log.md
  Reflections/
07_System/
  Constitution.md
  Laws.md
  Current State.md
  Functions/      ← Function definition lives here
  Identity.md
  Interaction Preferences.md
03_Projects/      ← Project context
05_Goals/         ← Goals context
```

## Execution Protocol

When Matteo triggers this skill, follow these steps in order:

### Step 1: Read System and Daily Context

Read the following files to understand current priorities and state:
- `07_System/CLAUDE.md` — governance and interaction rules (especially Session Protocol and Monitoring sections)
- `01_Daily/Current State.md` — active projects, this week's priorities, what's on his mind
- `01_Daily/YYYY-MM-DD.md` — today's daily note if it exists (Matteo's morning brain dump, AM EMA notes, intentions for the day)
- `01_Daily/YYYY-MM-DD-1.md` — yesterday's daily note for carryover context (if it exists)
- `01_Daily/Reflections/` — most recent reflection file for context on yesterday's wrap-up
- `01_Daily/Tasks/` — check the most recent task file for unfinished items to carry over
- `01_Daily/Mood & State Log.md` — most recent entries to gauge state and TRT cycle position

### Step 2: Gather Data from Connected Services

Run these data pulls in parallel where possible:

**Linear (task management):**
- Use `list_issues` to get all issues assigned to Matteo
- Filter for: In Progress, Todo, Backlog states
- For each issue, capture: title, state, priority, project, due date, any recent comments
- Use `list_cycles` to check current sprint/cycle context
- Use `get_issue_status` for status categories

**Gmail:**
- Use `gmail_search_messages` to find:
  - Unread emails from the last 24 hours: query `is:unread newer_than:1d`
  - Emails needing response (sent to me, unread): query `is:unread to:me newer_than:3d`
  - Starred/important items: query `is:starred is:unread`
- For each relevant email, capture: sender, subject, snippet, date, thread ID
- Use `gmail_read_message` for emails that look particularly important

**Slack:**
- Use `slack_search_public_and_private` to find:
  - Recent messages mentioning Matteo: query `to:me` or search for his name
  - Messages in the last 24 hours that may need responses
- Use `slack_read_channel` for key channels if identifiable
- Capture: channel, sender, message preview, timestamp, whether it seems to need a response

### Step 3: Read Daily Notes Context

- Check `01_Daily/Mood & State Log.md` for today's state entry (if any AM EMA was done)
- Check `07_System/Current State.md` for "This Week's Priorities" section
- Check any existing task files in `01_Daily/Tasks/` for carryover items from yesterday

### Step 4: Generate the HTML Dashboard

Create an interactive HTML dashboard file at:
`01_Daily/Tasks/Dashboard_YYYY-MM-DD.html`

The dashboard should include these sections:

**Header:**
- Today's date, day of week
- A greeting based on time of day
- Quick state summary if morning EMA data exists

**Priority Overview (cards):**
- Top 3-5 items Matteo should focus on today, synthesised from all sources
- Each card shows: source icon (Linear/Gmail/Slack/Vault), title, urgency indicator

**Linear Tasks Panel:**
- Grouped by state: In Progress → Todo → Backlog
- Each task shows: title, project, priority badge (Urgent/High/Medium/Low), assignee
- Visual progress indicators (colour-coded by state)
- Click-through context where possible

**Email Panel:**
- Emails requiring response (sorted by urgency/recency)
- Each shows: sender, subject, preview snippet, time received
- Visual indicator for unread vs starred

**Slack Panel:**
- Messages/threads that need attention
- Grouped by channel
- Shows: sender, preview, channel name, timestamp

**Carryover Tasks:**
- Unfinished items from yesterday's task list (if any)
- Checkbox format for quick review

**This Week's Priorities:**
- Pulled from Current State.md
- Shows completion status where trackable

**Design requirements:**
- Self-contained single HTML file (inline CSS and JS)
- Clean, modern design — dark mode preferred (dark navy/charcoal background, light text)
- Use CSS grid or flexbox for responsive layout
- Colour-coded priority badges: Urgent=red, High=orange, Medium=blue, Low=grey
- Smooth transitions, subtle hover effects
- Collapsible sections for each panel
- Mobile-friendly responsive breakpoints
- No external dependencies (no CDN links) — everything inline

### Step 5: Generate the Markdown Summary

Create a companion markdown file at:
`01_Daily/Tasks/Tasks_YYYY-MM-DD.md`

Format:

```markdown
# Daily Plan — YYYY-MM-DD

## Top Priorities
- [ ] Priority 1 (source)
- [ ] Priority 2 (source)
- [ ] Priority 3 (source)

## Linear Tasks

### In Progress
- [ ] Task title — *Project* | Priority | [link if available]

### Todo
- [ ] Task title — *Project* | Priority

### Backlog (relevant only)
- [ ] Task title — *Project* | Priority

## Emails Needing Response
- [ ] **Sender** — Subject line (received: time)
- [ ] **Sender** — Subject line (received: time)

## Slack Threads
- [ ] **#channel** — Sender: message preview (time)

## Carryover from Yesterday
- [ ] Item from previous day's tasks

## This Week's Priorities
(pulled from Current State.md)

## Notes
(blank space for Matteo to add thoughts during the day)
```

### Step 6: Present to Matteo

After generating both files, present:
1. A brief verbal summary of the day (2-3 sentences, conversational)
2. Link to the HTML dashboard
3. Link to the Markdown task file
4. Any flags: overdue items, high-priority emails, things that look time-sensitive

## Important Notes

- The HTML dashboard is a system artifact (Claude's voice is appropriate here per Constitution Article I — this is an operational tool, not Matteo's self-knowledge)
- The Markdown task file should be minimal and functional — Matteo will edit it throughout the day
- If any service is unavailable or returns no data, note it in the dashboard rather than failing
- Date format for filenames: `YYYY-MM-DD` (e.g., `2026-04-10`)
- Always check for yesterday's task file to pull carryover items
- Be sensitive to Matteo's state — if Mood & State Log shows low energy, note it gently and perhaps suggest a lighter priority list
