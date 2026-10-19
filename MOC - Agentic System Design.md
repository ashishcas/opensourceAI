---
id: moc-agentic-system-design
title: "MOC - Agentic System Design"
type: moc
status: evergreen
tags:
  - wiki/moc
  - ai/agents
  - architecture/agentic
  - pkm
up: "[[index]]"
related:
  - "[[MOC - Artificial Intelligence]]"
  - "[[LLM Wiki]]"
  - "[[Persistent Memory Systems]]"
  - "[[Claude Code Projects]]"
  - "[[Hermes Agent]]"
  - "[[Model Context Protocol (MCP)]]"
---

# 🤖 MOC - Agentic System Design

> **Map of Content** covering the foundational architectural patterns, coordination paradigms, tool protocols, and persistent memory fabrics required to build autonomous, reliable multi-agent systems.

---

## 🗺️ Architectural Topology

```mermaid
flowchart TD
    ASD["🤖 Agentic System Design"]
    
    subgraph ExecutionPlane ["1. Execution Runtimes & Swarm Patterns"]
        Strands["[[AWS Strands Harness]]\n(Session & Token Boundary Management)"]
        Claude["[[Claude Code Projects]]\n(Coordinator-Worker Swarms on Git)"]
        Hermes["[[Hermes Agent]]\n(Peer-to-Peer Messaging & Skills)"]
        Taskflow["[[GitHub Taskflow Agent]]\n(Closed-Loop Fuzzing & Triage)"]
    end

    subgraph MemoryPlane ["2. Memory & Knowledge Compounding"]
        PMS["[[Persistent Memory Systems]]\n(Working, Episodic, Semantic, Procedural)"]
        Wiki["[[LLM Wiki]]\n(Persistent Markdown Knowledge Base)"]
        SolPi["[[SoL-Pi]]\n(Context Compression & ObservationPack)"]
    end

    subgraph ProtocolPlane ["3. Interoperability & Tool Protocol"]
        MCP["[[Model Context Protocol (MCP)]]\n(Universal Agent-Tool Standard)"]
        ToolHive["[[ToolHive]]\n(Containerized MCP Sandboxing)"]
        Kestra["[[Kestra 2.0]]\n(Deterministic Workflow Orchestration)"]
        Speakeasy["[[Speakeasy OpenAPI Generator]]\n(Automated SDK & MCP Synthesis)"]
    end

    subgraph ControlPlane ["4. Decision, Governance & Telemetry"]
        Jev["[[Jev]]\n(Sub-500ms System-1 Gating)"]
        PoC["[[Proof-of-Control]]\n(Signed Tamper-Evident Action Logs)"]
        TM["[[Token Meter]]\n(Cost-Per-Successful-Task Telemetry)"]
        P4S["[[Plugin4Shell]]\n(Supply-Chain Defense)"]
    end

    ASD --> ExecutionPlane & MemoryPlane & ProtocolPlane & ControlPlane
```

---

## 📚 Core System Design Pillars

### 1. Execution Runtimes & Multi-Agent Swarms
* [[AWS Strands Harness]]: Industrial runtime managing agent lifecycles, cancellation tokens, and model fallbacks.
* [[Claude Code Projects]]: Isolated worker branches coordinated by a lead agent for concurrent code synthesis.
* [[Hermes Agent]]: Autonomous local-first agent implementing peer-to-peer delegation, bot modes, and skill discovery.
* [[GitHub Taskflow Agent]]: Closed-loop bug triage and autonomous regression testing.

### 2. Memory Fabrics & Persistent Knowledge
* [[LLM Wiki]]: Inverting ephemeral RAG by having agents incrementally compile and maintain interlinked markdown vaults.
* [[Persistent Memory Systems]]: Layered cognitive architectures separating active context from durable episodic and semantic stores.
* [[SoL-Pi]]: High-efficiency observation packing and context window optimization.

### 3. Tool Standardization & Execution Sandboxing
* [[Model Context Protocol (MCP)]]: Open protocol standardizing how models discover, invoke, and inspect tools.
* [[ToolHive]]: Secure micro-VM and container sandbox preventing hostile code execution during tool calls.
* [[Kestra 2.0]]: Coordinating deterministic multi-step pipelines as agent tools.
* [[Speakeasy OpenAPI Generator]]: Transforming RESTful APIs into validated MCP tool servers.

### 4. Decision Intelligence, Security & Telemetry
* [[Jev]]: Fast, typed System-1 decision intelligence preventing unnecessary frontier model invocations.
* [[Proof-of-Control]]: Cryptographic action signing ensuring auditability of agent executions.
* [[Token Meter]]: Local observability tracking cost-per-successful-task and context saturation.
* [[Plugin4Shell]]: Mitigating unpinned dependencies and prompt injection in dynamic tool ecosystems.
