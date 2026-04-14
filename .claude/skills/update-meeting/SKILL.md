---
name: update-meeting
description: "Import meeting notes and transcripts from Granola into the Obsidian vault. Use this skill whenever Matteo says 'update meetings', 'import meetings', 'sync Granola', 'log meetings', 'pull meeting notes', or any request to bring meeting transcripts and notes into the vault. Also trigger when Matteo mentions Granola, meeting notes, or asks to review what was discussed in recent meetings."
---

# Update Meeting Notes

This skill pulls meeting transcripts and notes from Granola and imports them into the Obsidian vault as structured markdown files.

## Execution Protocol

### Step 1: Fetch Meetings from Granola

Use the Granola MCP tools to get recent meetings:

1. `list_meetings` — get a list of recent meetings (default: last 7 days)
2. For each meeting that hasn't already been imported, use `get_meeting_transcript` to pull the full transcript
3. Optionally use `query_granola_meetings` to search for specific meetings if Matteo asks for something particular

### Step 2: Check for Existing Notes

Before importing, check if a note already exists for each meeting:
- Look in `01_Daily/Meetings/` (create this folder if it doesn't exist) for files matching the meeting date and title
- Skip meetings that have already been imported unless Matteo asks to re-import

### Step 3: Create Meeting Notes

For each new meeting, create a markdown file at:
`01_Daily/Meetings/YYYY-MM-DD — Meeting Title.md`

Format:

```markdown
# Meeting Title
**Date:** YYYY-MM-DD
**Time:** HH:MM
**Attendees:** [list from Granola metadata]
**Folder:** [Granola folder if available]

---

## Notes
[Granola's structured notes/summary if available]

## Key Takeaways
[Extract 3-5 key points from the transcript — these are Claude's summary, clearly marked]

## Action Items
- [ ] Action item 1 (owner if identifiable)
- [ ] Action item 2

## Transcript
<details>
<summary>Full transcript (click to expand)</summary>

[Full transcript text]

</details>

---
*Imported from Granola on YYYY-MM-DD*
```

### Step 4: Cross-Reference

After importing, check if any meetings involve people who have notes in `02_Domains/People/`:
- If so, add a link to the meeting note from their People page
- If new people appear who don't have notes yet, mention this to Matteo

### Step 5: Update Context

If meeting content reveals new information relevant to:
- Active projects → mention to Matteo, don't auto-update project notes
- Action items for Matteo → flag these clearly
- Decisions that affect current priorities → flag for review

### Step 6: Present Summary

Tell Matteo:
- How many meetings were imported
- A 1-line summary of each
- Any action items identified that are assigned to him
- Any meetings that seem to need follow-up

## Voice Rules

Meeting transcripts are preserved verbatim. The "Key Takeaways" and "Action Items" sections are Claude's extraction and should be marked as such. If Matteo wants to add his own notes to a meeting file, those are his words and should be preserved per Article I.

## Important Notes

- Default import window is 7 days. Matteo can specify a different range.
- Meeting notes go in `01_Daily/Meetings/`, not in project folders. They can be linked to projects via Obsidian links.
- If Granola is unavailable or returns no meetings, report this clearly rather than failing silently.
- The transcript is placed in a collapsed `<details>` block to keep the file scannable.
