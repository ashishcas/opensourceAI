---
id: tech-claude-code-projects
title: "Claude Code Projects (Multi-Agent Swarm Orchestration)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/agents
  - ai/multi-agent
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Hermes Agent]]"
  - "[[AWS Strands Harness]]"
  - "[[LLM Wiki]]"
  - "[[Persistent Memory Systems]]"
---

# 🧑‍💻 Claude Code Projects

> **Claude Code Projects** implements a coordinator-worker multi-agent architecture where a primary coordinator delegates subtasks to parallel agent workers operating on isolated Git branches.

```mermaid
flowchart TD
    Coord["🤖 Coordinator Agent"]
    Coord --> WorkerA["👷 Worker A (Branch feat/backend)"]
    Coord --> WorkerB["👷 Worker B (Branch feat/tests)"]
    Coord --> WorkerC["👷 Worker C (Branch feat/frontend)"]
    WorkerA & WorkerB & WorkerC --> Merge["Git PR & Merge Evaluation"]
    
    subgraph KnowledgeLayer ["Persistent Memory & Schema"]
        Schema["📜 CLAUDE.md\n(Operating Schema & Rules)"]
        Wiki["💎 [[LLM Wiki]]\n(Architecture & Decisions)"]
    end
    Coord <--> Schema & Wiki
```

---

## 📜 Role of `CLAUDE.md` as Knowledge Schema

In Claude Code, project-level conventions, architecture guidelines, and repository behaviors are governed by `CLAUDE.md`. Under the [[LLM Wiki]] pattern:
* **Operating Schema (Layer 3):** `CLAUDE.md` specifies the directory taxonomy, frontmatter requirements, and workflows for ingesting, querying, and linting project documentation.
* **Persistent Memory (Layer 2):** Agent workers read and compile design decisions, test outcomes, and architectural changes directly into markdown notes, ensuring knowledge compounds across branch merges rather than being lost in closed PR comments.

