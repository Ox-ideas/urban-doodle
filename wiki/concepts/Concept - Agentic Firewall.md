---
tags:
  - concept
created: 2026-05-22
updated: 2026-05-22
sources:
  - "[[Source - Wanderloots LLM Wiki Guide]]"
---

# Agentic Firewall

A security pattern used to prevent AI agents from accessing unauthorized directories or vaults. 

It typically involves a "wrapper" around the agent's file-system tools (like the Obsidian CLI) that checks requests against a list of approved paths. If an agent tries to write to or read from an unauthorized vault, the firewall blocks the action.
