---
title: LLM Wiki
type: concept
sources:
  - raw/sources/Karphathy's LLM Wiki.md
  - raw/sources/How To Build LLM Wiki In Obsidian? 🧠 A Memory Layer For Any Agentic AI.md
  - raw/sources/Don't Use Karpathy's Second Brain (I BUILT SOMETHING BETTER).md
related:
  - Knowledge Graph
  - Infinite Brain
  - Agentic AI
created: 2026-05-24
updated: 2026-05-24
tags:
  - llm
  - wiki
  - architecture
---

The LLM Wiki is a persistent, compounding knowledge layer built by an LLM on top of raw source material.

## Core idea
Instead of re-deriving knowledge from raw sources at query time, the LLM reads new sources, extracts the key insights, and integrates them into an interlinked markdown wiki. The wiki is maintained over time, so queries can use structured pages and relationships rather than rediscovering information from scratch.

## Layers
- Raw sources: immutable source material in `raw/sources/`.
- Wiki: generated markdown pages in `wiki/` that capture summaries, concepts, entities, comparisons, and analysis.
- Schema: the contract that tells the agent how to create pages, use frontmatter, name files, and preserve consistency.

## Benefits
- reduces repeated retrieval cost
- keeps synthesis and cross-references up to date
- makes knowledge easier to browse and audit
- supports logging and maintenance workflows
