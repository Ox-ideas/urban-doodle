---
tags:
  - concept
created: 2026-05-22
updated: 2026-05-22
sources:
  - "[[Source - Karpathy LLM Wiki Guide]]"
---

# Wiki vs RAG

A comparison of knowledge management strategies for LLMs.

## Traditional RAG (Retrieval-Augmented Generation)
- **Mechanism**: Chunks documents at query time.
- **Problem**: Rediscover knowledge from scratch on every question; no accumulation; ephemeral.

## LLM Wiki
- **Mechanism**: Incrementally compiles and integrates knowledge at ingest time.
- **Advantage**: Persistent, compounding artifact. Cross-references and contradictions are pre-flagged. Synthesis already reflects the breadth of knowledge.
