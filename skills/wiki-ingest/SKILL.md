---
name: wiki-ingest
description: Processes and ingests new documents, PDFs, links/URLs, HTML, or Markdown files into the Wiki. Use when the user drops a new file or refers to a new source to be added to the knowledge base.
---

# Wiki Ingest Skill

This skill handles processing new sources, notes, and documents into the user's PhD Wiki. It supports two distinct workflows depending on the input type:

---

## Branch A: Literature & Document Ingestion
*Use this workflow when the user provides a raw file, a URL to a paper/article (PDF, HTML, Markdown, or text), or asks to ingest a specific reference.*

### Step A1: Download & Locate Source
- If the input is a URL (starts with `http`), download the file contents:
  - Default to `.pdf` extension for arbitrary/binary URLs, or preserve `.html`, `.md`, `.txt` if present in the URL path.
  - Save temporarily in `Wiki/Library/tmp.<ext>`.
- If the input is a local file path, locate it.

### Step A2: Extract Text
- Read Markdown/text files directly.
- Extract text from PDFs or HTML documents (convert/parse text cleanly, ignoring binary/markup wrapping).

### Step A3: Extract Metadata Schema
Analyze the document text and extract the following metadata:
1. **title:** The title of the paper following APA Style Title Case Capitalization.
2. **filename:** Proposed file name based on the title and publication year. Compact, descriptive, and under 40 characters (e.g., `Attention_Is_All_You_Need_2017`).
   - *Cleaning rules:* Replace spaces, hyphens, slashes, backslashes, dots, question marks, curly braces, and `'s` with single underscores. Strip double, leading, or trailing underscores.
3. **tag:** Category of the file, selected from `default_tags` defined in the plugin's `tags.json` file.
4. **tag_list:** List of up to 5 relevant tags for indexing (excluding any tags defined in `negative_tags` in the plugin's `tags.json` file). Use PascalCase.
5. **abstract:** Copy the exact abstract from the paper. Replace unicode characters with their ASCII/LaTeX counterparts. Format inline math using `$...$`.
6. **topic1:** Summarize the main theory or method of the paper in 1 short sentence starting with a direct action verb (e.g., "Presents...").
7. **topic2:** Summarize the second theory or method in 1 short sentence starting with an action verb.
8. **topic3:** Summarize the discussion in 1 short sentence starting with an action verb.
9. **topic4:** Summarize the results in 1 short sentence starting with an action verb.

### Step A4: Check Relevance of Branch B & Ask for User Confirmation
- Check if the ingested document contains concepts, findings, or open questions relevant to existing projects, collaborators, or wiki pages. Identify potential updates or syntheses that could be performed (matching Branch B).
- Present the extracted metadata (Title, Filename, Category, Tag list, Abstract, Topics) to the user, and list any identified Branch B wiki updates/syntheses.
- Ask the user to confirm: **"Is this information correct? And would you like to also perform general concept synthesis to update relevant wiki pages with this source's findings (Branch B)?"**

### Step A5: Save, Index, and Synthesize (Once Confirmed)
1. **Copy Source File:** Copy the original file to `Wiki/Library/<filename>.<ext>`. If a temporary downloaded file was used, clean it up after copying.
2. **Execute Branch B Synthesis (If Confirmed):** If the user agreed to Branch B synthesis in Step A4, execute Step B2 (Create or Update Topic Pages) and Step B3 (Update Navigation Indices) using the paper's contents.
3. **Create Markdown Notes (Only for PDFs):** If the file is a `.pdf`, create a Markdown note file at `Wiki/Library/<filename>.md` containing:
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
3. **Update Index (`Wiki/_Index.md`):** Prepend the formatted metadata entry to the top of `Wiki/_Index.md`:
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
   *(Note: If the source is not a PDF, omit the `- :luc_file:` line in the index entry).*
4. **Log the Action:** Prepend a log entry to `Wiki/log.md` (Format: `## [YYYY-MM-DD HH:MM] ingest | <title>`).

---

## Branch B: General Research Notes & Project Ingestion
*Use this workflow when the user provides raw research notes, discussion questions, project updates, or meeting minutes.*

### Step B1: Synthesize Raw Material
- Read the user's input thoroughly to identify the core concept, project updates, scientific methods, or open questions.
- Identify the key takeaways and discuss/clarify them with the user if any requirements or concepts are ambiguous.

### Step B2: Create or Update Topic Pages
- Draft or modify relevant concept, project, or synthesis pages in the `Wiki/Projects/` or `Wiki/` folder.
- Do not blindly overwrite existing files; merge information, noting if the new inputs refine, expand, or contradict previous claims.
- **Deep Interlinking:** Review existing wiki notes and dynamically add Obsidian-style links (`[[Link]]`) to connect the new concepts to existing projects, collaborators, and methods.

### Step B3: Update Navigation Indices
- Prepend a log entry to `Wiki/log.md` (Format: `## [YYYY-MM-DD HH:MM] ingest | <Title>`).
- If new pages were created, add their links to `Wiki/wiki.md` under the appropriate category.

---

## Tool Constraints & Reminders
- **Obsidian-Style Links:** ALWAYS link between files using Obsidian-style markdown (e.g., `[[Link]]`).
- **Preserve Cross-References:** When editing an existing Wiki page, make sure not to accidentally delete linkages.
- **Tone:** Maintain a dry, objective, structural, scientific, and concise tone.