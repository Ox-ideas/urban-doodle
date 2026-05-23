---
tags:
  - concept
created: 2026-05-22
updated: 2026-05-22
sources:
  - "[[Source - Wanderloots LLM Wiki Guide]]"
---

# LLM Wiki

A persistent, compounding artifact that sits between a user and raw sources. Unlike traditional RAG, which re-derives knowledge per query, an LLM Wiki "compiles" knowledge into a structured collection of markdown files.

## Core Properties
- **Persistent**: Changes are saved and build over time.
- **Compounding**: New sources update existing pages and create new links.
- **Agent-Maintained**: The LLM handles the "grunt work" of summarizing and cross-referencing.

## Structure
Defined by a three-layer architecture:
1. **Raw Sources**: Immutable source documents.
2. **The Wiki**: LLM-generated summaries and concept pages.
3. **The Schema**: Rules and workflows (e.g., `AGENTS.md`).
