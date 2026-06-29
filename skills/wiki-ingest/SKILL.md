---
name: wiki-ingest
description: Processes and ingests new documents, PDFs, links/URLs, HTML, or Markdown files into the Wiki. Use when the user drops a new file or refers to a new source to be added to the knowledge base.
---

# Wiki Ingest Skill

Two workflows, depending on the input.

---

## Branch A: Literature & Document Ingestion
*A raw file or a URL to a paper/article (PDF, HTML, Markdown, text), or a request to ingest a specific reference.*

### A1: Locate Source
- URL (starts with `http`): download to `Wiki/Library/tmp.<ext>`. Use `.pdf` for arbitrary/binary URLs; preserve `.html`/`.md`/`.txt` if present in the path.
- Local path: locate it.

### A2: Extract Text
Read Markdown/text directly. For PDF/HTML, parse text cleanly, ignoring binary/markup wrapping.

### A3: Extract Metadata
1. **title:** APA-style Title Case.
2. **filename:** from title + year, descriptive, under 40 chars (e.g. `Attention_Is_All_You_Need_2017`). Replace spaces, hyphens, slashes, backslashes, dots, question marks, curly braces, and `'s` with single underscores; strip double/leading/trailing underscores.
3. **tag:** one category from `default_tags` in the plugin's `tags.json`.
4. **tag_list:** up to 5 PascalCase tags for indexing, excluding any in `negative_tags` (`tags.json`).
5. **abstract:** exact abstract from the paper; replace unicode with ASCII/LaTeX equivalents; inline math as `$...$`.
6. **topic1-4:** one short sentence each, starting with an action verb — main method, second method, discussion, results (e.g. "Presents...").

### A4: Confirm with User
- Check whether the document is relevant to existing projects, collaborators, or pages — i.e. whether Branch B synthesis applies.
- Present the metadata (Title, Filename, Tag, Tag list, Abstract, Topics) and any identified Branch B updates, then ask: **"Is this correct? Also run concept synthesis to update relevant wiki pages (Branch B)?"**

### A5: Save, Index, Synthesize (once confirmed)
1. **Copy source** to `Wiki/Library/<filename>.<ext>`; delete the temp download if used.
2. **Branch B (if confirmed):** run steps B2 and B3 using the paper's contents.
3. **Markdown note (PDFs only)** at `Wiki/Library/<filename>.md`:
   ```markdown
   >[!abstract]-
   > <abstract>
   - :luc_file_text: [[<filename>.pdf]]
   - <topic1>
   - <topic2>
   - <topic3>
   - <topic4>
   #<tag> #<tag_list_item1> #<tag_list_item2> ...
   -------------
   ```
4. **Index** — prepend to the top of `Wiki/_Index.md`:
   ```markdown
   ### <title>
   >[!abstract]-
   > <abstract>
   - :luc_file_text: [[<filename>.pdf]] ❌
   - :luc_file: [[<filename>.md|Notes]]
   - <topic1>
   - <topic2>
   - <topic3>
   - <topic4>
   ```
   *(Non-PDF source: omit the `- :luc_file:` line.)*
5. **Log** — prepend to `Wiki/log.md`: `## [YYYY-MM-DD HH:MM] ingest | <title>`.

---

## Branch B: Research Notes & Project Ingestion
*Raw research notes, discussion questions, project updates, or meeting minutes.*

### B1: Synthesize
Read the input to identify the core concept, project updates, methods, or open questions. Clarify anything ambiguous with the user.

### B2: Create or Update Pages
Draft or modify the relevant page in `Wiki/Projects/` or `Wiki/`. Merge rather than overwrite — note whether new input refines, expands, or contradicts prior claims. Add Obsidian links (`[[Link]]`) connecting the concept to existing projects, collaborators, and methods.

### B3: Update Navigation
- Prepend to `Wiki/log.md`: `## [YYYY-MM-DD HH:MM] ingest | <Title>`.
- If new pages were created, add their links to `Wiki/wiki.md` under the right category.

## Reminders
- Only touch `Wiki/_Index.md` and `Library` via the steps above; do not otherwise hand-edit them.
- Preserve existing cross-references when editing a page.
- Tone: dry, objective, scientific, concise.
