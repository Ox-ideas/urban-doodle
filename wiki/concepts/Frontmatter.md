---
title: Frontmatter
type: concept
sources:
  - raw/sources/How To Build LLM Wiki In Obsidian? 🧠 A Memory Layer For Any Agentic AI.md
related:
  - Schema
  - Templates
  - Wiki
created: 2026-05-24
updated: 2026-05-24
tags:
  - metadata
  - yaml
  - structure
---

Frontmatter is the structured YAML metadata block at the top of each wiki page.

## Purpose
- record key data about a note, including title, type, sources, and timestamps
- make pages machine-readable for scripts, search, and linting
- support consistent tagging and related-link tracking

## Common fields
- `title`
- `type`
- `sources`
- `related`
- `created`
- `updated`
- `tags`

## Best practices
- keep metadata consistent across pages
- update `updated` whenever a page changes
- include raw source references for traceability
