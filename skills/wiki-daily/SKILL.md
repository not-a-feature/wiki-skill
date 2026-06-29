---
name: wiki-daily
description: Generates a daily brief summarizing active projects, open tasks, todos, open questions, and reminders. Useful for starting the day.
---

# Wiki Daily Brief Skill

**READ-ONLY.** Read existing files and print the brief. Never create or modify files.

## Workflow Steps

1. **Open Todos and Tasks:** Read `Projects and Todos.md` and the most recent `Daily Notes.md` entries for incomplete items (`- [ ]` or `Todo` headers).
2. **Active Projects:** Extract WIP/high-priority projects from `Projects and Todos.md` and the most recent updates in `Wiki/log.md`.
3. **Open Questions & Blockers:** Scan active project pages and recent daily notes.
4. **Reminders and Deadlines:** Find upcoming dates, meetings, or milestones in `Daily Notes.md` or `Projects and Todos.md`. **Ignore anything before the current local time** — only active or future items.
5. **Present Brief** (do not save): short bullets only, no paragraphs. Sections: **Open Todos**, **Active Projects**, **Open Questions**, **Reminders / Deadlines**.

## Reminders
- Reference wiki pages with Obsidian links (`[[Link]]`).
- Tone: dry, objective, scientific, concise.
