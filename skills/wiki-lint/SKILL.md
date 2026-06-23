---
name: wiki-lint
description: Performs health checks and janitorial tasks on the Wiki. Use when the user asks to lint, review, or health-check the wiki.
---

# Wiki Lint Skill

This skill handles maintenance and health-check operations for the user's PhD Wiki.

## Workflow Steps

1. **Scan for Inconsistencies:** Look for contradictory claims across pages that haven't been properly noted.
2. **Find Orphans:** Identify pages that exist but have no inbound connections (links from other pages).
3. **Promote Concepts:** Identify important concepts or terms that are mentioned repeatedly but lack their own dedicated page.
4. **Suggest Actions:** Propose to the user (or execute directly if approved) changes or new pages that fill out these knowledge gaps. 
5. **Log Pass:** Prepend a "Lint Pass" entry to `Wiki/log.md` (Format: `## [YYYY-MM-DD HH:MM] lint | Lint Pass`).

## Tool Constraints & Reminders
- **Obsidian-Style Links:** ALWAYS link between files using Obsidian-style markdown (e.g., `[[Link]]`).
- **File Organization:** Create relevant subfolders and organize `.md` files hierarchically. Do not over-organize.
- **Strict Read-Only Zones:** NEVER edit `index.md` or create files inside the `Library` folder.
- **Preserve Cross-References:** When editing an existing Wiki page, make sure not to accidentally delete linkages.
- **Tone:** Maintain a dry, objective, structural, scientific, and concise tone.