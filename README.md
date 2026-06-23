# PhD Wiki Management Plugin

This plugin provides a collection of agentic skills for Claude/Gemini to manage, query, and synthesize a local Markdown-based Wiki (such as Obsidian) tailored for PhD students and academic researchers.

It enables automated organization of research notes, project tracking, bibliography indexing, collaborator profiles, and automated progress reporting.

## Core Features & Workflow

- **Obsidian Compatibility:** All skills use Obsidian-style markdown cross-references (`[[Link]]`) to maintain a highly interconnected knowledge graph.
- **Fail-Safe Analytics:** Summary and analytics skills are strictly **read-only**, ensuring no accidental modifications are made to local data when compiling reports or briefs.
- **Academic Tone:** Generates objective, scientific, and concise summaries suitable for PhD-level review.

## Recommended Folder Structure

The wiki skills expect the workspace and wiki folder to be organized as follows:

```text
<workspace_root>/
├── Daily Notes.md               # Daily logs, meeting notes, and quick drafts
├── Projects and Todos.md        # Project tracking table and high-level todo lists
└── Wiki/                        # Main research wiki directory
    ├── wiki.md                  # Living wiki index (entry point for searches)
    ├── log.md                   # Cumulative chronology log of updates
    ├── Project Overview.md      # Status summary of active and old projects
    ├── Persons/                 # Profiles of collaborators and supervisors
    │   ├── Person-A.md
    │   └── Person-B.md
    ├── Projects/                # Folders or files for individual projects
    │   ├── Project-1/
    │   └── Project-2/
    ├── ServerClusters/          # Documentation on your cclusters (e.g., GPU nodes, SSH)
    ├── Synthesis/               # Mathematical theorems, research syntheses, tables
    └── Library/                 # PDF papers, slide decks, and publication notes
```

---

## Exposed Skills

### 📊 Reporting & Planning

#### 1. `wiki-daily`
- **Purpose:** Generates a highly condensed daily overview to start the work day.
- **Scope:** Read-Only.
- **Outputs:** Active projects, incomplete tasks/todos from daily notes, recent open questions, and active/future deadlines (ignoring stale/past deadlines).

#### 2. `wiki-report`
- **Purpose:** Generates a retrospective summary report over a specified timeframe (defaulting to 8 days).
- **Scope:** Read-Only.
- **Outputs:** Project progress lists, active collaborator involvement/contributions, and unresolved questions or blockers.

---

### 🗃️ Knowledge Ingestion & Maintenance

#### 3. `wiki-ingest`
- **Purpose:** Ingests and processes new files, articles, or reference material into the wiki.
- **Scope:** Read/Write.

#### 4. `wiki-person`
- **Purpose:** Standardizes, creates, and updates collaborator profiles (researchers, PIs, co-authors) in the `Persons/` folder, linking them to projects and publications.
- **Scope:** Read/Write.

#### 5. `wiki-log`
- **Purpose:** Appends project-specific progress logs to chronological records (`Wiki/log.md`) when describing accomplishments.
- **Scope:** Read/Write.

#### 6. `wiki-query`
- **Purpose:** Searches, traverses, and synthesizes information from the wiki index (`Wiki.md`) and individual concept notes to answer research questions.
- **Scope:** Read-Only.

#### 7. `wiki-lint`
- **Purpose:** Audits the health of the wiki by searching for orphaned notes, broken links, and metadata inconsistencies.
- **Scope:** Read/Write.

---

## Configuration & Customization

### Centralized Tag Management (`tags.json`)
You can customize the tags and categories used during literature ingestion by editing [tags.json](tags.json).
- **`default_tags`**: List of primary categories for imported documents (e.g., `["Paper", "Book", "Presentation"]`).
- **`negative_tags`**: Blocklist of generic keywords/tags to filter out during metadata extraction to prevent indexing clutter.

