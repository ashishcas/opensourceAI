---
id: tech-hermes-agent
title: "Hermes Agent (Multi-Agent Peer Framework)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/agents
  - ai/multi-agent
  - ai/memory
up: "[[MOC - Agentic System Design]]"
related:
  - "[[Persistent Memory Systems]]"
  - "[[Claude Code Projects]]"
  - "[[Model Context Protocol (MCP)]]"
  - "[[ToolHive]]"
  - "[[LLM Wiki]]"
---

# 🐍 Hermes Agent

> **Hermes Agent** is an open-source autonomous agent framework featuring peer-to-peer agent messaging (`hermes peer`), native skill libraries, secure MCP authorization, and persistent file-backed memory.

---

## 🏛️ Architecture & Peer Coordination

```mermaid
flowchart TD
    subgraph Host ["Hermes Runtime Environment"]
        Core["🤖 Hermes Primary Agent"]
        Mem["💾 Persistent Memory\n([[Persistent Memory Systems]])"]
        Skills["🛠️ Dynamic Skills Engine"]
        Core <--> Mem
        Core <--> Skills
    end

    subgraph PeerSwarm ["Peer-to-Peer Agent Mesh (`hermes peer`)"]
        Peer1["🤖 Peer Agent A (Data Extraction)"]
        Peer2["🤖 Peer Agent B (Code Review)"]
        Peer3["🤖 Peer Agent C (Verification)"]
        Core <-->|Secure IPC / RPC| Peer1 & Peer2 & Peer3
    end

    subgraph Tools ["MCP Sandboxed Tools"]
        MCPGateway["🛡️ [[ToolHive|MCP Gateway]]"]
        Core <--> MCPGateway
        MCPGateway --> ToolsSet["Tools: Shell, Browser, Git, DB"]
    end
```

---

## 🔑 Key Features & Subsystems

1. **Peer-to-Peer Messaging (`hermes peer`):** Enables decentralized agent-to-agent task delegation without requiring a monolithic global orchestrator.
2. **Persistent Memory Subsystem:** Stores operational heuristics, user preferences, and project context in local Markdown files, interoperating directly with the [[LLM Wiki]] and [[Persistent Memory Systems|Persistent Memory]] standards.
3. **MCP Tool Integration:** Connects to [[Model Context Protocol (MCP)]] servers with strict privilege separation, secret redaction, and user confirmation prompts.
4. **Autonomous Skills Engine:** Encapsulates domain-specific workflows (e.g. Git workflows, Playwright browser automation) as modular, version-controlled skill directories.
5. **Bot Mode & Daemon Execution:** Can run headlessly in background daemons or as interactive terminal companions.
