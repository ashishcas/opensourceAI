---
id: concept-model-routing
title: "Model Routing & Tiered Inference Architectures"
type: concept
status: evergreen
tags:
  - wiki/concept
  - ai/routing
  - ai/inference
  - ai/llmops
  - local-ai
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Clef]]"
  - "[[Jev]]"
  - "[[GPT-6 Sol and Luna]]"
  - "[[MiniCPM5-2B]]"
  - "[[Reflection Beam]]"
  - "[[OpenCode]]"
  - "[[Synthesis - Decision Layers & Execution Verification]]"
  - "[[Synthesis - Context Compression & Supply-Chain Security]]"
  - "[[Prefill-Decode Disaggregation]]"
  - "[[vLLM]]"
---

# 🔀 Model Routing & Tiered Inference Architectures

> **Model Routing** is the architectural practice of dynamically dispatching incoming prompts, agent decisions, and tool executions to the most cost-effective and latency-appropriate model tier rather than funneling all queries into a single monolithic frontier model.

---

## 🏛️ The Three-Tier Model Routing Hierarchy

```mermaid
flowchart TD
    Request["Incoming Agent Request / Decision Point"] --> Gate{"Classifier / System-1 Gate"}
    
    subgraph Tier1 ["Tier 1: System-1 Decision Layer (Sub-Second)"]
        Gate -->|Discrete Choice / Boolean / Fast Triage| T1["⚡ [[Clef]] / [[Jev]]\n• Latency: 70–400ms\n• Cost: ~$0 (Local Ollama / Clef-Flash)\n• Mode: Single-Pass Typed JSON"]
    end

    subgraph Tier2 ["Tier 2: Local & Mid-Tier Execution (Fast Generation)"]
        Gate -->|Routine Coding / Local Diagnosis| T2["💻 Gemma 3 12B / [[MiniCPM5-2B]] / [[GPT-6 Sol and Luna|GPT-6 Luna]]\n• Latency: 1–3s\n• Cost: Local GPU/NPU or $0.10/1M tokens\n• Mode: Unit tests, log extraction, simple functions"]
    end

    subgraph Tier3 ["Tier 3: Frontier Reasoning & Architecture (Deep Synthesis)"]
        Gate -->|Complex Architecture / Multi-File Refactor| T3["👑 Frontier / [[Reflection Beam]] / GPT-6 Sol\n• Latency: 5–30s\n• Cost: $2.00–$15.00/1M tokens\n• Mode: Extended reasoning, complex bug synthesis"]
    end
```

---

## ⚖️ Routing Tradeoff Matrix

| Tier | Candidate Models | Ideal Tasks | Latency | Relative Cost |
| :--- | :--- | :--- | :--- | :--- |
| **System-1 Decision** | [[Clef]] (Ollama), [[Jev]] | Retry vs Escalate, schema validation, sentiment | 70–400 ms | $\sim 0 \times$ |
| **Workhorse Local SLM** | Gemma 3 12B, [[MiniCPM5-2B]] | Playwright test debug, single-file code gen, RAG summaries | 1–3 s | $1 \times$ |
| **Frontier Reasoning** | Claude 3.7 Sonnet, GPT-6 Sol, [[Reflection Beam]] | System architecture, complex distributed debugging | 5–20 s | $20–50 \times$ |

---

## ⚡ Inference Serving Topology: Disaggregation vs. Monolithic Serving

Model routing decisions should not only consider model parameter size, but also the serving engine's **computational topology**:

* **Asymmetric Token Ratios:** A prompt with 30,000 input tokens and a 500-token response places severe demand on prompt evaluation (prefill). Routing this request into a monolithic engine executing active user streams degrades the **Inter-Token Latency (ITL)** of concurrent users.
* **Prefill-Decode Disaggregation:** In clusters managed via [[vLLM]] or SGLang, routing systems dispatch prefill workloads to compute-dense nodes and generation to memory-bandwidth-dense nodes, transferring intermediate KV caches across fast interconnects (Mooncake/NIXL). See [[Prefill-Decode Disaggregation]] for architecture details.

---

## 💡 Practical Implementation in Local Workstations

On a Mac mini M4 paired with Ollama:
1. Use **Clef** (or `clef:flash`) via `/v1/systemone` for immediate task branching.
2. Route passing or solvable failures to local **Gemma 3 12B**.
3. Fall back to cloud models only when confidence is low or retries are exhausted.
4. Record latency, token expenditure, and routing decisions in [[Langfuse]].
