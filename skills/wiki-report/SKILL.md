---
name: wiki-report
description: Generates a summary report of progress, collaborator updates, and open questions over a given timeframe (defaulting to 8 days) based on the PhD Wiki logs, daily notes, and other documentation.
---

# Wiki Report Skill

This skill handles generating a summary report of progress, collaborator updates, and open questions over a given timeframe.

This is a **READ-ONLY** skill. It must not create or modify any files (including `Wiki/log.md`, project pages, or daily notes). It only reads existing files and prints the generated report to the user.

## Workflow Steps

1. **Determine Timeframe:**
   - Check the user's request for a specified timeframe (e.g., "last 2 weeks", "past 5 days").
   - If no timeframe is specified, default to the last **8 days**.
   - Calculate the start and end dates relative to the current local time (current local time is provided in the environment or metadata).

2. **Read Log and Daily Notes:**
   - Read `Wiki/log.md` and `Daily Notes.md`.
   - Parse and extract all entries, updates, and meetings that fall within the calculated timeframe.

3. **Identify Active Projects & Collaborators:**
   - Based on the progress logs from the timeframe, identify which projects were active.
   - For each active project, read its corresponding project page in `Wiki/Projects/` and reference `Wiki/Project Overview.md` to identify key collaborators.
   - Look up active collaborator details in the profiles under `Wiki/Persons/` (e.g., role, lab affiliation).

4. **Identify Open Questions:**
   - Scan the extracted logs, the `Daily Notes.md` sections within the timeframe, and active project pages for any open questions, discussion points, TODOs, or unresolved issues.

5. **Generate and Present Report:**
   - Present the synthesized report to the user. Do not save it to any file.
   - Structure the report as follows:
     - **Report Period**: Start date to end date.
     - **Progress Summary**: A short, bullet-point list of updates grouped by project. Keep it concise (1-2 sentences per project, highlighting the main technical change/milestone).
     - **Collaborators**: Only include collaborators directly relevant to active projects during the timeframe. For each, list only their name, role, and their specific, direct contribution or relevance to the active projects (do not list generic research areas or general publications).
     - **Open Questions**: A concise bullet-point list of the 3-5 most critical open questions or blockers found in the notes or wiki pages for the active projects.

## Tool Constraints & Reminders
- **Read-Only:** Do NOT write or modify any files. Do not append to `Wiki/log.md`.
- **Obsidian-Style Links:** ALWAYS use Obsidian-style markdown links (e.g., `[[Link]]`) when referencing wiki pages and files.
- **Tone:** Maintain a dry, objective, structural, scientific, and concise tone.
