---
name: compress
description: >
  Compress natural language memory files (CLAUDE.md, todos, preferences) into caveman format
  to save input tokens. Preserves all technical substance, code, URLs, and structure.
  Compressed version overwrites the original file. Human-readable backup saved as FILE.original.md.
  Trigger: /caveman:compress <filepath> or "compress memory file" or "compress [filename]"
---

# Caveman Compress

Compress natural language files → caveman-speak. Reduce input tokens. Backup original as `<filename>.original.md`.

## Process

1. Read target file
2. Apply compression rules below
3. Validate: no code/URLs/paths altered
4. Write compressed version to original path
5. Save backup to `<filepath>.original.md`

## Compression Rules

**Remove:**
- Articles: a, an, the
- Filler: just, really, basically, actually, simply, essentially, generally
- Pleasantries: "sure", "certainly", "of course", "happy to", "I'd recommend"
- Hedging: "it might be worth", "you could consider", "it would be good to"
- Redundant: "in order to" → "to", "make sure to" → "ensure", "the reason is because" → "because"
- Connective fluff: however, furthermore, additionally, in addition

**Preserve EXACTLY (never modify):**
- Code blocks (fenced ``` and indented)
- Inline code (`backtick content`)
- URLs and links
- File paths
- Commands
- Technical terms (library names, API names, protocols)
- Proper nouns (project names, people, companies)
- Dates, version numbers, numeric values
- Environment variables

**Preserve Structure:**
- All markdown headings (compress body below)
- Tables (compress cell text, not structure)
- Lists (compress item text)
- YAML frontmatter (compress values, not keys)

## Target: 40-60% token reduction
