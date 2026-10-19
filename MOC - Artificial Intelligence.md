---
id: moc-artificial-intelligence
title: "MOC - Artificial Intelligence & Agentic Engineering"
type: moc
status: evergreen
tags:
  - wiki/moc
  - ai/agents
  - ai/llmops
  - ai/security
  - mcp
up: "[[index]]"
related:
  - "[[MOC - Agentic System Design]]"
  - "[[MOC - LLMOps & Infrastructure]]"
  - "[[MOC - DevSecOps & Security]]"
  - "[[Persistent Memory Systems]]"
  - "[[LLM Wiki]]"
  - "[[Master Guide - AI & Open-Source Engineering]]"
---

# 🧠 MOC - Artificial Intelligence & Agentic Engineering

> **Central Map of Content** for agent architectures, inference systems, local SLMs, security governance, and automated testing runtimes.

---

## 🗺️ Visual Ecosystem Topology

```mermaid
flowchart TD
    MOC["🧠 AI Engineering Hub"]
    
    subgraph Decision ["1. Decision & Routing Layer"]
        Jev["[[Jev]] (System 1)"]
        Router["[[Model Routing]]"]
        SolLuna["[[GPT-6 Sol and Luna]]"]
        MiniCPM["[[MiniCPM5-2B]] (Local SLM)"]
        Beam["[[Reflection Beam]] (501B MoE)"]
    end
    
    subgraph Harness ["2. Agent Harness & Runtime"]
        Strands["[[AWS Strands Harness]]"]
        SolPi["[[SoL-Pi]] (Context Compression)"]
        Hermes["[[Hermes Agent]]"]
        ClaudeProjects["[[Claude Code Projects]]"]
        OpenCode["[[OpenCode]] (Distributed Local Agent)"]
        AgentScope["[[AgentScope]] (SOP Pipelines)"]
        Copilot["[[GitHub Copilot Harness]]"]
        Taskflow["[[GitHub Taskflow Agent]]"]
    end
    
    subgraph ToolingProtocol ["3. Tool Protocol & Orchestration"]
        MCP["[[Model Context Protocol (MCP)]]"]
        Speakeasy["[[Speakeasy OpenAPI Generator]]"]
        Kestra["[[Kestra 2.0]] (Deterministic Flows)"]
        Paper2Agent["[[Paper2Agent]]"]
        Isaac["[[Isaac ROS 5.0]]"]
    end
    
    subgraph SecurityObservability ["4. Security, Verification & LLMOps"]
        PoC["[[Proof-of-Control]] (Signed Evidence)"]
        P4S["[[Plugin4Shell]] (Supply Chain)"]
        TH["[[ToolHive]] (MCP Sandboxing)"]
        Sprites["[[Fly.io Sprites]] (Agent Sandboxing)"]
        AIGateway["[[AI Gateway Security]] (LiteLLM CVEs)"]
        GHScan["[[GitHub AI Scan]] (PR Security)"]
        TM["[[Token Meter]] (Cost Telemetry)"]
        ZCode["[[ZCode Security]] (Local Residency)"]
    end
    
    subgraph Memory ["5. Agent Memory & Knowledge Architecture"]
        PMS["[[Persistent Memory Systems]]"]
        LLMWiki["[[LLM Wiki]] (Persistent Graph)"]
    end
    
    MOC --> Decision & Harness & ToolingProtocol & SecurityObservability & Memory
```

---

## 📚 Core Knowledge Categories

### 1. Decision & Routing Engines
* [[Jev]]: Fast, typed System-1 decision intelligence (70–500ms) for action gating and failure triage.
* [[Model Routing]]: Dynamic cost/latency allocation across local SLMs and frontier models.
* [[GPT-6 Sol and Luna]]: Economic model tiering ($0.10 Luna vs $2.00 Sol).
* [[MiniCPM5-2B]]: High-performance local small language model for discrete tasks.
* [[Reflection Beam]]: Open-weight 501B/23B MoE model focused on high-efficiency useful work per token.

### 2. Agent Runtimes & Harness Optimization
* [[OpenCode]]: Terminal-native coding agent supporting remote Ollama backends over LAN and MCP servers.
* [[AgentScope]]: Industrial multi-agent framework enforcing Standard Operating Procedures (SOPs) and TeamPipelines.
* [[AWS Strands Harness]]: Enterprise agent SDK managing token limits, cancellation, and sessions.
* [[SoL-Pi]]: Context compression, action fusion, and ObservationPack saving 45–50% token volume.
* [[Hermes Agent]]: Multi-agent peer-to-peer communication and persistent execution.
* [[GitHub Taskflow Agent]]: Closed-loop fuzzing, crash triage, and automated harness refinement.
* [[Claude Code Projects]]: Coordinator-worker patterns with Git branch isolation.

### 3. Tool Protocols & Deterministic Orchestration
* [[Model Context Protocol (MCP)]]: The universal open standard for AI agent-tool interfaces.
* [[Speakeasy OpenAPI Generator]]: Auto-generation of type-safe SDKs, CLIs, and MCP servers from OpenAPI specs.
* [[Kestra 2.0]]: Executing deterministic CI/CD and test workflows exposed as MCP tools.
* [[Paper2Agent]]: Automated tool synthesis and verification against reference test suites.
* [[Isaac ROS 5.0]]: Domain-specific agent skills for complex robotics and automation pipelines.

### 4. Security, Verification & Telemetry
* [[Fly.io Sprites]]: Disposable micro-VM execution sandboxes separating agent credentials from command execution.
* [[AI Gateway Security]]: Threat modeling, SSRF defenses, and CVE-2026-35029/59823 mitigation in AI routing proxies.
* [[GitHub AI Scan]]: Contextual LLM security analysis for pull request scripts, Terraform, and Dockerfiles.
* [[Proof-of-Control]]: Open standard for tamper-evident action interception and signed evidence trails.
* [[Plugin4Shell]]: Critical supply-chain vulnerability in AI agent commit-pinning resolution.
* [[ToolHive]]: Containerized MCP gateway and egress network sandboxing.
* [[Token Meter]]: Open-source local telemetry dashboard tracking cost-per-successful-task.
* [[ZCode Security]]: Codebase privacy, local indexing, and zero-data-retention practices.

### 5. Agent Memory & Knowledge Architecture
* [[LLM Wiki]]: Persistent agent-compiled Markdown knowledge base replacing ephemeral RAG.
* [[Persistent Memory Systems]]: Multi-tier episodic, semantic, and procedural long-term memory architectures.

---

## 📚 Master Guides & Thematic Syntheses
* [[Master Guide - AI & Open-Source Engineering|📚 Master Engineering Guide]]
* [[Synthesis - Agent Runtimes & MCP Sandboxing|Synthesis: Agent Runtimes & MCP Sandboxing]]
* [[Synthesis - Multi-Agent Swarms & Governed Loops|Synthesis: Multi-Agent Swarms & Governed Loops]]
* [[Synthesis - Decision Layers & Execution Verification|Synthesis: Decision Layers & Execution Verification]]
* [[Synthesis - Context Compression & Supply-Chain Security|Synthesis: Context Compression & Supply-Chain Security]]
* [[Synthesis - Closed Feedback Loops & Auto-Generated MCP Tools|Synthesis: Closed Feedback Loops & Auto-Generated MCP Tools]]
