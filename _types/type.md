---
type: Type
order: 0
visible: false
_organized: true
---
# Type

A Type defines shared metadata and defaults for a category of notes in this
vault. Each file in `_types/` is one type, and its H1 is the name notes refer to
with `type:` in their frontmatter.

## Common properties

- **icon** — the sidebar icon for this type.
- **color** — the accent colour for its notes.
- **order** — where it sits in the sidebar.
- **visible** — set `false` to keep the type out of the sidebar.

Types are edited as files rather than through the interface for now: add a
document here and it exists. It appears in the sidebar once at least one note
actually uses it.
