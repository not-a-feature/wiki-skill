---
name: wiki-query
description: Explores and synthesizes information from the Wiki based on a user's question. Use when the user asks a question about existing themes, entities, or data in the Wiki.
---

# Wiki Query Skill

This skill handles querying and exploring existing concepts in the user's PhD Wiki.

## Workflow Steps

1. **Consult Index First:** Read `Wiki/Wiki.md` to identify relevant concept/entity pages.
2. **Drill Down:** Read the specific pages necessary to answer the query.
3. **Synthesize:** Provide the answer citing specific pages and sources.
4. **File the Result:** If the query results in a valuable new comparison, insight, table, or overview. Propose filing the answer as a new "Synthesis" page in the wiki. Do not do it automatically.

## Tool Constraints & Reminders
- **Obsidian-Style Links:** ALWAYS link between files using Obsidian-style markdown (e.g., `[[Link]]`).
- **File Organization:** Create relevant subfolders and organize `.md` files hierarchically. Do not over-organize.
- **Strict Read-Only Zones:** NEVER edit `index.md` or create files inside the `Library` folder.
- **Preserve Cross-References:** When editing an existing Wiki page, make sure not to accidentally delete linkages.
- **Tone:** Maintain a dry, objective, structural, scientific, and concise tone unless the user requests subjective synthesis.