---
name: wiki-person
description: Creates or updates a person profile in the Wiki's Persons directory following the standardized framework. Use when the user wants to add a contact, researcher, or colleague to the Wiki.
---

# Add & Update Person Skill

## Instructions

1. **Check for Existing Profile:** Consult `Wiki/wiki.md`. If a profile exists, update it rather than creating a duplicate.
2. **Gather Data:** Collect Name, Email, Lab/University, Role/Responsibilities, Research Areas, and Tone (e.g. Friend, Professional). Fill gaps from reputable scientific databases or official institutional sites.
3. **Request Missing Info:** If critical details remain unknown, ask the user.
4. **Document Publications:** List key/relevant publications. Format as a wiki link (e.g. `[[Library/Publication.pdf]]`) only if the file is present in `Library`; otherwise list as a plain citation.
5. **Identify Connections:** Review `Wiki/Persons/` for collaborators or co-authors and list them under **Related People**.
6. **Create/Update File:** Write `Wiki/Persons/<Name>.md` using the template below.
7. **Finalize Navigation:** Update `Wiki/wiki.md` and prepend to `Wiki/log.md`: `## [YYYY-MM-DD HH:MM] Add Person | <Name>`.

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

## Reminders
- Use Obsidian links (`[[Link]]`); never create files in `Library`.
- Tone: dry, objective, scientific, concise.
