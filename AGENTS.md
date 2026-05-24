# LLM Wiki Schema

This document defines the idea, structure, conventions, and workflows for maintaining the LLM Wiki.

## The Idea

- Instead of just retrieving from raw documents at query time, the LLM incrementally builds and maintains a persistent wiki. When a new source is added, the LLM doesn't just index it for later retrieval. It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. The knowledge is compiled once and then kept current, not re-derived on every query.
- The wiki is a persistent, compounding artifact. The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. The wiki keeps getting richer with every source you add and every question you ask.

## Directory Structure

- `raw/sources/`: Curated collection of source documents. Articles, papers, images, data files, videos (captions), etc. These are immutable. NEVER modify.
- `raw/assets/`: Images and other attachments.
- `wiki/sources/`: LLM-generated summaries of raw source material.
- `wiki/concepts/`: LLM-generated pages for abstract ideas, techniques, or theories.
- `wiki/entities/`: LLM-generated pages for specific people, organizations, or software tools.
- `wiki/comparisons/`: LLM-generated comparison tables or analyses.
- `wiki/index.md`: Catalog of all pages in the wiki.
- `wiki/log.md`: Chronological record of activity.

### RAW SOURCES DIRECTORY EXAMPLE

raw/
  sources/
    articles/
      2026-03-attention-is-all-you-need-revisited.md
      2026-04-scaling-laws-update.md
    papers/
      transformer-architecture-v2.pdf
      mixture-of-experts-survey.pdf
    repos/
      llama-3-readme.md
      vllm-architecture-notes.md
    data/
      benchmark-results.csv
      model-comparison.json
    images/
      transformer-diagram.png
      scaling-curves.png
  assets/
    # Downloaded images from clipped articles

### WIKI DIRECTORY EXAMPLE

wiki/
  index.md                # Master catalog of all pages
  log.md                  # Chronological activity record
  overview.md             # High-level synthesis
  concepts/
    attention-mechanism.md
    mixture-of-experts.md
    scaling-laws.md
    tokenization.md
  entities/
    openai.md
    anthropic.md
    google-deepmind.md
  comparisons/
    gpt4-vs-claude-vs-gemini.md
    rag-vs-finetuning.md

## Conventions

- **Wiki Pages**: Use Obsidian-style wikilinks `[[Page Name]]`.
- **Frontmatter**: Every wiki page should have YAML frontmatter with the following:
```
---
title: Page Title
type: concept | entity | source-summary | comparison
sources: [list of raw files referenced]
related: [list of wiki pages linked]
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
  - "concept"
  - "sample relevant tag"
---
```
- **Naming**: Use descriptive, title-case filenames for wiki pages.
- **Citations**: Always link back to the source document in `raw/sources/`.
- **Source Notes**: Raw source files or notes should include the following if applicable specially markdown files:
```
---
Title: ""
Author: ""
Reference: ""
ContentType:
  - "markdown"
Created: YYYY-MM-DD
Processed: false
tags:
  - "source"
  - "sample relevant tag"
---
```
- **Tags**: Use simple plain tags.
- **Obsidian Skills:** For all future source ingestions, utilize the Obsidian skills and automation configured in `.github/skills` within this devcontainer or in the case of gemini cli or other ai cli provide a way to install it accordingly. This ensures compatibility with Obsidian plugins, properties, and workflows, and leverages available automation for note creation, metadata, and linking.

## Workflows


### 1. Ingest
When user says "ingest notes-" or requests to process the raw sources, ask which new source file or files to process (if possible provide a list that can be multi-selected):

1. Read the source files in  `raw/`, `raw/sources/` including `raw/assets/` if needed. 
2. Discuss key takeaways with the user.
3. Create a summary page in `wiki/sources/`.
4. Identify and update/create relevant entity pages in `wiki/entities/` and concept pages in `wiki/concepts/`.
5. Update `wiki/index.md` with the new page(s).
6. Append an entry to `wiki/log.md`.
7. Maintain cross-references, and keep everything consistent.
8. Show what you plan to do and ask me before proceeding.

### 2. Query
When the user asks a question:
1. Search `wiki/index.md` for relevant pages.
2. Read the identified pages.
3. Synthesize an answer with [[wikilink]] citations.
4. Do not invent citations or create unsupported claims.
5. Answers can take different forms depending on the question — a markdown page, a comparison table, a slide deck (Marp), a chart (matplotlib), a canvas or others than can be processed with markdown files and obsidian. 
6. If the answer is substantial, propose filing it as a new wiki page or append to a relevant existing page.

### 3. Lint
When user says "lint notes-" or asks to clean or health check the wiki, check for:
- Contradictions between pages.
- Stale claims superseded by newer sources.
- Orphan pages (no inbound links).
- Important concepts mentioned but lacking their own page.
- Missing cross-references.
- Data gaps that could be filled with a web search.
- Suggest questions to investigate next.
- Sample output:
  Wiki Health Report (2026-04-04):

  CONTRADICTIONS (2):
  - concepts/dense-vs-sparse.md claims dense > sparse
    below 10B, but sources/summary-moe-efficiency.md
    shows opposite. Recommend: update with nuance.
  - entities/openai.md says GPT-5 is 200B params,
    but sources/summary-gpt5-leak.md says 300B.

  ORPHAN PAGES (3):
  - concepts/tokenization.md (no inbound links)
  - sources/summary-old-bert-paper.md (no references)
  - comparisons/old-gpu-benchmark.md (outdated)

  MISSING PAGES (4):
  - "RLHF" mentioned 12 times, no concept page
  - "Constitutional AI" mentioned 8 times, no page
  - "KV Cache" referenced in 5 sources, no page
  - "Speculative Decoding" mentioned 3 times, no pages

  SUGGESTED INVESTIGATIONS:
  - No sources on inference optimization post-2025
  - Entity page for Meta AI is thin (only 1 source)
  - The "Scaling Laws" page hasn't been updated in 3 weeks

## Indexing and Logging

### Description

- **index.md** is content-oriented. It's a catalog of everything in the wiki — each page listed with a link, a one-line summary, and optionally metadata like date or source count. Organized by category (entities, concepts, sources, etc.). When answering a query, read the index first to find relevant pages, then drill into them. 
- **log.md** is chronological. It's an append-only record of what happened and when — ingests, queries, lint passes. A useful tip: if each entry starts with a consistent prefix (e.g. ## [2026-04-02] ingest | Article Title), the log becomes parseable with simple unix tools — grep "^## \[" log.md | tail -5 gives you the last 5 entries. The log gives you a timeline of the wiki's evolution and helps the LLM understand what's been done recently.

### Index & Log Format

- **index.md**:
  ```markdown
  # Wiki Index
  
  ## Entities
  - [[Entity Name]] - Short summary.
  
  ## Concepts
  - [[Concept Name]] - Short summary.
  
  ## Sources
  - [[Source Page Name]] - Summary of source.
  ```

- **log.md**:
  ```markdown
  # Wiki Log
  
  ## [YYYY-MM-DD] ingest | [[Source Title]]
  Summary of what was updated.
  ```

## Optional: CLI tools

- At some point we will want to build small tools that help the LLM operate on the wiki more efficiently. A search engine over the wiki pages is the most obvious one — at small scale the index file is enough, but as the wiki grows you want proper search. qmd is a good option: it's a local search engine for markdown files with hybrid BM25/vector search and LLM re-ranking, all on-device. It has both a CLI (so the LLM can shell out to it) and an MCP server (so the LLM can use it as a native tool).
- Make sure that the wiki setup is compatible with qmd.
