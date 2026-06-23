---
name: wiki-daily
description: Generates a daily brief summarizing active projects, open tasks, todos, open questions, and reminders. Useful for starting the day.
---

# Wiki Daily Brief Skill

This skill handles generating a highly condensed daily overview of active work, tasks, questions, and deadlines.

This is a **READ-ONLY** skill. It must not create or modify any files (including `Wiki/log.md`, project pages, or daily notes). It only reads existing files and prints the generated brief to the user.

## Workflow Steps

1. **Identify Open Todos and Tasks:**
   - Read `Projects and Todos.md`.
   - Parse `Daily Notes.md` (specifically the most recent entries) for incomplete checklist items (e.g., `- [ ]` or `Todo` headers).

2. **Identify Active Projects:**
   - Extract the current work-in-progress (WIP) or high-priority projects from `Projects and Todos.md` and the most recent updates in `Wiki/log.md`.

3. **Identify Open Questions & Blockers:**
   - Scan active project pages and recent daily notes for current open questions or design blockers.

4. **Identify Reminders and Deadlines:**
   - Find upcoming dates, meetings, or milestones listed in `Daily Notes.md` or `Projects and Todos.md`.
   - **Ignore stale/past deadlines** (any dates that are before the current local time). Only include active or future reminders and deadlines.

5. **Generate and Present Brief:**
   - Present the synthesized brief to the user. Do not save it to any file.
   - Use only short bullet points. Do not write paragraphs.
   - Structure:
     - **Open Todos**
     - **Active Projects**
     - **Open Questions**
     - **Reminders / Deadlines**

## Tool Constraints & Reminders
- **Read-Only:** Do NOT write or modify any files. Do not append to `Wiki/log.md`.
- **Obsidian-Style Links:** ALWAYS use Obsidian-style markdown links (e.g., `[[Link]]`) when referencing wiki pages and files.
- **Short Format:** Keep the brief extremely concise with brief bullet points.
- **Tone:** Maintain a dry, objective, structural, scientific, and concise tone.
