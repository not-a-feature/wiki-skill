---
name: wiki-lint
description: Performs health checks and janitorial tasks on the Wiki. Use when the user asks to lint, review, or health-check the wiki.
---

# Wiki Lint Skill

## Workflow Steps

1. **Scan for Inconsistencies:** Find contradictory claims across pages that haven't been noted.
2. **Find Orphans:** Identify pages with no inbound links.
3. **Promote Concepts:** Identify terms mentioned repeatedly that lack a dedicated page.
4. **Suggest Actions:** Propose fixes or new pages (execute only if approved).
5. **Log Pass:** Prepend to `Wiki/log.md`: `## [YYYY-MM-DD HH:MM] lint | Lint Pass`.

## Reminders
- Use Obsidian links (`[[Link]]`); never edit `Wiki/_Index.md` or create files in `Library`. Preserve existing cross-references when editing.
- Tone: dry, objective, scientific, concise.
