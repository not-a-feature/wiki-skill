---
name: wiki-report
description: Generates a summary report of progress, collaborator updates, and open questions over a given timeframe (defaulting to 8 days) based on the PhD Wiki logs, daily notes, and other documentation.
---

# Wiki Report Skill

**READ-ONLY.** Read existing files and print the report. Never create or modify files.

## Workflow Steps

1. **Determine Timeframe:** Use the timeframe in the user's request (e.g. "last 2 weeks"); default to the last **8 days**. Calculate start/end dates from the current local time.
2. **Read Log and Daily Notes:** Read `Wiki/log.md` and `Daily Notes.md`. Extract entries, updates, and meetings within the timeframe.
3. **Identify Active Projects:** From those entries, determine which projects were active. For each, read its page in `Wiki/Projects/` and check `Wiki/Project Overview.md` for key collaborators, then their profiles in `Wiki/Persons/`.
4. **Identify Open Questions:** Scan the timeframe's logs, `Daily Notes.md`, and active project pages for open questions, TODOs, or unresolved issues.
5. **Present Report** (do not save) with this structure:
   - **Report Period:** start to end date.
   - **Progress Summary:** bullets grouped by project, 1-2 sentences each, main technical change/milestone only.
   - **Collaborators:** only those with directly relevant info; name + the relevant point.
   - **Open Questions:** the 3-5 most critical open questions or blockers.

## Reminders
- Tone: dry, objective, scientific, concise.
