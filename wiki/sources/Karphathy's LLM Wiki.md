---
title: Karphathy's LLM Wiki
type: source-summary
sources:
  - raw/sources/Karphathy's LLM Wiki.md
related:
  - LLM Wiki
  - Knowledge Graph
  - Agentic AI
created: 2026-05-24
updated: 2026-05-24
tags:
  - llm
  - wiki
  - knowledge-management
  - ingestion
---

Source: raw/sources/Karphathy's LLM Wiki.md

## Summary
This source defines the core LLM Wiki pattern: build a persistent, LLM-maintained markdown wiki that sits between raw sources and query-time retrieval. It emphasizes incremental compilation over repeated RAG-style synthesis, preserving raw material while letting the LLM maintain summaries, cross-references, and structured artifacts.

## Key points
- Raw sources are immutable and preserved.
- The wiki is an LLM-owned layer of interlinked markdown pages.
- The schema is the contract that guides the agent's behavior and enforces consistency.
- Ingest means read new sources, extract key ideas, create/update wiki pages, update the index, and append a log entry.
- Query means search the wiki, synthesize answers, and optionally file valuable output back into the wiki.
- Lint means periodically health-check the wiki for contradictions, orphans, missing pages, and stale claims.

## Concepts
- [[LLM Wiki]]
- [[Knowledge Graph]]
- [[Agentic AI]]
