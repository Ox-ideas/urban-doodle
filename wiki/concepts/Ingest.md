---
title: Ingest
type: concept
sources:
  - raw/sources/Karphathy's LLM Wiki.md
  - raw/sources/How To Build LLM Wiki In Obsidian? 🧠 A Memory Layer For Any Agentic AI.md
related:
  - Raw Sources
  - Wiki
  - Agentic AI
created: 2026-05-24
updated: 2026-05-24
tags:
  - ingest
  - pipeline
  - source-processing
---

Ingest is the process of converting new raw sources into structured wiki content.

## Steps
1. detect new raw files in `raw/sources/`
2. read the source and extract its key ideas
3. create or update `wiki/sources/` summary pages
4. update relevant concept and entity pages
5. update `wiki/index.md`
6. append an entry to `wiki/log.md`

## Goal
- convert raw material into reusable knowledge nodes
- preserve the original source while making its insights accessible
- bootstrap the wiki with structured, linkable content
