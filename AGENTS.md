# 📜 AGENTS.md — Autonomous Knowledge Base Operating Protocol

> **Operating Constitution & Navigation Schema** for AI agents (Antigravity, Claude Code, OpenCode, Cursor, Copilot) maintaining the `opensourceAI` Obsidian knowledge vault.
> **Primary Directive**: Prevent redundant reading. Consult `index.md` and `log.md` before inspecting any individual notes.

---

## 🧭 Fast Navigation Protocol (Stop Reading Everything!)

To eliminate token waste and avoid repeatedly scanning or reading every file in this vault, follow this strict lookup order:

1. **Start with `index.md` (Content Catalog):**
   - Contains a classified, curated list of all concept notes, tools, runtimes, security models, and syntheses with one-line descriptions.
   - Identify the exact 1–3 target notes relevant to your task instead of scanning the directory.

2. **Check `log.md` (Append-Only Audit Stream):**
   - Inspect the recent operations using `grep "^## \[" log.md | tail -n 10` to understand recent changes, active topics, and node history.

3. **Check the Relevant Map of Content (MOC):**
   - `[[MOC - Artificial Intelligence]]`: For inference systems, local SLMs, LLMOps, model routing, and security.
   - `[[MOC - Agentic System Design]]`: For agent runtimes, multi-agent swarms, tool protocols (MCP), memory architectures, and durable workflows.

4. **Read ONLY Targeted Sections:**
   - Use targeted range reads (`StartLine`, `EndLine`) or exact symbol searches rather than reading whole 500+ line documents.
   - Never run unbounded scans across all `.md` files when answering a scoped query.

---

## 🏛️ Knowledge Vault Architecture: The LLM Wiki Pattern

This repository implements the **[[LLM Wiki]]** pattern (compounding Markdown compilation over ephemeral RAG):
* **No Daily Ephemeral Folders:** All concept notes live at the root level as evergreen, thematic Markdown files (`[[Concept Name]]`).
* **Bidirectional Associative Graph:** All core concepts must be linked using Obsidian wikilinks: `[[Target Note Name]]`.
* **Zero Opaque State:** The filesystem is the single source of truth. No hidden vector databases.

### File Taxonomies & Conventions

| File Prefix / Type | Purpose | Example |
| :--- | :--- | :--- |
| `MOC - ...` | High-level architectural maps of content | `[[MOC - Artificial Intelligence]]` |
| `Synthesis - ...` | Thematic deep-dives connecting multiple tools & concepts | `[[Synthesis - Decision Layers & Execution Verification]]` |
| `Project - ...` | Executable reference implementations & pipelines | `[[Project - AI Test Engineer (Playwright + BDD + MCP)]]` |
| `Guide - ...` | Step-by-step practical guides | `[[Guide - Hardening MCP Servers with ToolHive]]` |
| `Master Guide - ...`| Consolidated master architectural guide | `[[Master Guide - AI & Open-Source Engineering]]` |
| Plain Names | Individual concept, tool, model, or protocol notes | `[[vLLM]]`, `[[Clef]]`, `[[Model Context Protocol (MCP)]]` |
| Catalogs & Logs | System telemetry and indexes | `[[index]]`, `[[log]]`, `[[README]]` |

---

## 📋 Mandatory Frontmatter Schema

Every note created or refactored in the vault MUST include YAML frontmatter adhering to this schema:

```yaml
---
id: concept-kebab-name          # e.g., concept-durable-agents, tech-vllm
title: "Human Readable Title"
type: concept                   # concept | tech | project | synthesis | moc | guide | index
status: evergreen               # seed | growing | evergreen | deprecated
tags:
  - wiki/concept                # or wiki/tech, wiki/moc, wiki/synthesis
  - ai/agents                   # domain tags
  - ai/inference
up: "[[MOC - Artificial Intelligence]]"    # Parent MOC or index
related:
  - "[[Related Note 1]]"
  - "[[Related Note 2]]"
---
```

---

## 🔄 Standard Ingest Workflow (Compounding Protocol)

When the user provides new research, briefings, or technical documentation to ingest:

1. **Extract Core Architectural Claims:**
   - Break the briefing into discrete concepts, performance trade-offs, and practical code experiments.
2. **Create / Update Evergreen Concept Nodes:**
   - Create focused, high-density concept notes with architecture diagrams (`mermaid`), trade-off tables, code examples, and common pitfalls.
   - If an existing note is a stub or related, update and populate it rather than leaving fragments.
3. **Graph Fan-Out (Compounding Links):**
   - Update **5 to 10 existing related notes** across the vault.
   - Insert contextual cross-links (`[[New Concept]]`) into related concept pages, project runtimes, memory notes, and syntheses.
4. **Register in Navigational Catalogs:**
   - Add new entries to `[[index]]` under the appropriate category.
   - Add new nodes to `[[README]]` ecosystem diagrams if they represent primary architectural components.
   - Update parent `MOC` diagrams (`[[MOC - Artificial Intelligence]]` or `[[MOC - Agentic System Design]]`).
5. **Append to Audit Log:**
   - Add a structured entry to `log.md` with:
     ```markdown
     ## [YYYY-MM-DD] Ingest | "<Briefing / Source Title>"
     - **Created**: [[New Note 1]], [[New Note 2]]
     - **Updated**: [[Existing Note 1]], [[Existing Note 2]], [[index]], [[README]]
     - **Synthesized**: Brief description of architectural reconciliations made.
     ```

---

## 🚫 Anti-Patterns & Operational Guardrails

- ❌ **Do NOT read all files into context** to answer simple queries. Use `index.md`.
- ❌ **Do NOT create date-stamped briefing files** (e.g. `2026-10-26 Briefing.md`). Ingest insights directly into evergreen concept nodes.
- ❌ **Do NOT orphan notes.** Every new note must have an `up:` parent link, `related:` links, and be registered in `index.md`.
- ❌ **Do NOT leave empty placeholder notes.** Either populate them with authoritative technical detail or leave them uncreated.
- ❌ **Do NOT use generic links.** Always use `[[WikiLinks]]` matching exact file names without `.md` extension.
