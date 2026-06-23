---
name: wiki-person
description: Creates or updates a person profile in the Wiki's Persons directory following the standardized framework. Use when the user wants to add a contact, researcher, or colleague to the Wiki.
---

# Add & Update Person Skill

This skill governs the process of adding or maintaining person profiles within the Wiki.

## Instructions

1. **Check for Existing Profiles:** Consult `Wiki.md` to determine if a profile for the individual already exists. If found, update the existing entry to prevent duplicates.
2. **Gather Data:** Collect essential details, including Name, Email, Role/Responsibilities, Research Areas, and Tone (e.g., Friend, Professional). Use reputable scientific databases or official institutional websites to fill gaps.
3. **Request Missing Information:** If critical details remain unavailable after research, ask the user to provide them.
4. **Document Publications:** List all key/relevant publications for the person. Only format as a wiki link (e.g., `[[Library/Publication.pdf]]`) if the publication is downloaded and present in the `Library` folder. Otherwise, list them as text/citations without wiki links.
5. **Identify Connections:** Review existing files in the `Persons` directory to identify collaborators or co-authors and include them in the **Related People** section.
6. **Create/Update File:** Use `write_file` to create or overwrite the file at `Wiki/Persons/<Name>.md` using the standard template below.
7. **Finalize Navigation:** Update `Wiki.md` and prepend an entry to `Wiki/log.md` (Format: `## [YYYY-MM-DD HH:MM] Add Person | <Name>`)

---

## Standard Template

```markdown
# {{Name}}

**Email:** {{Email}}
**Lab / University:** {{Lab/University}}
**Role/Responsibilities:** {{Responsibilities}}
**Research Areas:** {{Research Areas}}
**Tone:** {{Tone}}

## Related People
- [[Related Person 1]]
- [[Related Person 2]]

## Publications
- [[Library/Downloaded_Publication.pdf]] (Notes: [[Library/Downloaded_Publication]])
- *Other Relevant/Key Publication (Not Downloaded)*

## Links
- [Lab / Personal Website]
- [GitHub]

## Notes

```