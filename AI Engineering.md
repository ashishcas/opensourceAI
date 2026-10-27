---
id: concept-ai-engineering
title: "AI Engineering: Systems, Inference & Reliable Agents"
type: concept
status: evergreen
tags:
  - wiki/concept
  - ai/engineering
  - ai/systems
  - ai/inference
  - ai/agents
  - llmops
up: "[[index]]"
related:
  - "[[Prefill-Decode Disaggregation]]"
  - "[[Durable Execution for AI Agents]]"
  - "[[vLLM]]"
  - "[[Model Routing]]"
  - "[[Model Context Protocol (MCP)]]"
  - "[[Persistent Memory Systems]]"
  - "[[LLM Wiki]]"
  - "[[Langfuse]]"
  - "[[Master Guide - AI & Open-Source Engineering]]"
---

# 🛠️ AI Engineering: Systems, Inference & Reliable Agent Architecture

> **AI Engineering** is the discipline of transitioning artificial intelligence from experimental prompting and non-deterministic scripts into resilient, observable, high-performance production systems. It encompasses computational inference optimization, durable workflow orchestration, tool protocols, and compounding memory architectures.

---

## 🏛️ The Production AI Engineering Spectrum

Production AI engineering operates across four deeply interdependent infrastructure layers:

```mermaid
flowchart TD
    subgraph Layer1 ["1. Inference & Serving Infrastructure"]
        L1A["[[Prefill-Decode Disaggregation]]\n(Compute vs Bandwidth Decoupling)"]
        L1B["[[vLLM]]\n(PagedAttention & Disaggregated Prefilling)"]
        L1C["[[Model Routing]] & [[Clef]]\n(System-1 Gating & Tiered Inference)"]
    end

    subgraph Layer2 ["2. Agent Reliability & Orchestration"]
        L2A["[[Durable Execution for AI Agents]]\n(Checkpointed LangGraph / Temporal Graphs)"]
        L2B["[[AWS Strands Harness]]\n(Session Budgets & Token Caps)"]
        L2C["[[Project - AI Test Engineer (Playwright + BDD + MCP)]]\n(Autonomous Closed-Loop Quality)"]
    end

    subgraph Layer3 ["3. Tool Interfaces & Sandboxing"]
        L3A["[[Model Context Protocol (MCP)]]\n(Standardized Tool Discovery)"]
        L3B["[[ToolHive]] & [[Fly.io Sprites]]\n(Micro-VM Credential & Egress Isolation)"]
        L3C["[[Proof-of-Control]]\n(Tamper-Evident Action Signing)"]
    end

    subgraph Layer4 ["4. Compounding Memory & Observability"]
        L4A["[[Persistent Memory Systems]] & [[LLM Wiki]]\n(Compounding Markdown Knowledge)"]
        L4B["[[Langfuse]] & [[Token Meter]]\n(Span-Level Evals & Cost Telemetry)"]
    end

    Layer1 --> Layer2 --> Layer3 --> Layer4
```

---

## ⚡ 1. Inference Engineering & Serving Topologies

Inference engineering focuses on the physical placement of computation and memory bandwidth to serve autoregressive models under strict latency and cost constraints:

* **Computational Asymmetry:** Generating text splits into two radically different tasks:
  1. **Prefill (Prompt Processing):** Compute-bound GEMM operations constructing the KV cache.
  2. **Decode (Token Generation):** Memory-bandwidth-bound GEMV operations fetching KV pages step-by-step.
* **Prefill–Decode Disaggregation:** Rather than allowing long prompt prefill bursts to stall concurrent token generation, production clusters decouple prefill workers from decode workers via high-speed KV transfer protocols (e.g. Mooncake, NIXL). See [[Prefill-Decode Disaggregation]] and [[vLLM]].
* **Latency Triad:** Engineering targets must balance **Time to First Token (TTFT)**, **Inter-Token Latency (ITL)**, and total **Throughput**.

---

## 🛡️ 2. Agent Reliability: Durable Execution & Idempotency

Moving from toy chatbots to reliable production agents requires treating workflows as distributed transactions:

* **Durable Workflows:** Using graph engines like LangGraph (with persistent `SqliteSaver` or PostgreSQL) and Temporal to record step boundaries. If a container crashes 15 minutes into a multi-step task, execution rehydrates from the last checkpoint rather than restarting.
* **Human-in-the-Loop Interrupts:** Safely pausing asynchronous execution using native interrupts (`interrupt()`) and resuming when human sign-off arrives (`Command(resume=True)`).
* **Mitigating Duplicate Side Effects:** Applying deterministic idempotency keys (`workflow_id` + `operation_id`) and pre-execution existence queries to prevent duplicated real-world side effects (e.g. double charging cards, duplicate PRs). See [[Durable Execution for AI Agents]].

---

## 🧠 3. Memory Compounding vs. Ephemeral RAG

Rather than relying purely on vector embeddings that force models to re-synthesize domain knowledge from scratch on every turn:
* The **[[LLM Wiki]]** pattern operationalizes knowledge as a persistent, compounding Markdown graph in Obsidian maintained by autonomous agents.
* Cognitive memory is partitioned into active working memory, episodic logs, semantic concepts, and deterministic procedural tool definitions (see [[Persistent Memory Systems]]).

---

## 🔭 4. Full-Lifecycle Observability & Telemetry

Production systems require span-level instrumentation:
* **[[Langfuse]]:** Tracing multi-agent handoffs, separating prefill latency from decode latency, tracking human interrupt duration, and clustering failure modes.
* **[[Token Meter]]:** Measuring dollar cost per successful task completion rather than raw token counts.

---

## 🧭 Vault Navigation & Schema
* **Operating Protocol:** See [[AGENTS.md]] for the AI maintainer schema and fast navigation protocol.
* **Master Architectural Compendium:** Read the [[Master Guide - AI & Open-Source Engineering]].
