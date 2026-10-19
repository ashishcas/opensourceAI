---
id: tech-jev
title: "Jev (System 1 Decision Layer)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/decision-layer
  - ai/agents
  - ai/llmops
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Model Routing]]"
  - "[[AWS Strands Harness]]"
  - "[[Playwright]]"
---

# 🧠 Jev (System 1 Decision Layer)

> **Jev** (by TypeSafe AI) is a specialized class of **"System One" models** designed strictly for sub-second, structured decision intelligence rather than conversational text generation.

---

## ⚡ The Architecture: Fast Decisions vs. Heavy Reasoning

```mermaid
flowchart TD
    Event(["Application Event / Error"]) --> Agent["🤖 Agent Orchestrator"]
    Agent --> Gate{"Triage Decision"}
    
    Gate -->|Sub-second Tactical Decisions (70-500ms)| Jev["🧠 [[Jev]] (System 1)
• Boolean Checks
• Confidence Scores
• Action Routing
• Gate Approvals"]
    
    Gate -->|Deep Reasoning / Code Gen| LLM["👑 Frontier LLM (System 2)
• Architecture
• Code Synthesis
• Complex Debugging"]
```

---

## 🎯 Primary Use Cases in AI Test Automation

| Decision Problem | Traditional LLM Approach | Jev / System-1 Approach |
|---|---|---|
| **Playwright Test Flake** | Prompts GPT-4o (3–5s, $0.03) to ask if test should retry | Jev evaluates failure classification in **120ms ($0.0001)** |
| **Model Selection** | Hardcoded logic or heavy LLM router | Jev scores task complexity and emits typed route enum |
| **Tool Approval Gate** | Unsafe auto-exec or slow human interrupt | Jev assesses risk score and triggers human review only if $>0.8$ |

---

## 💡 Practical Takeaway for Playwright AI Engineer

```text
Playwright Failure Trace
       │
       ▼
   ┌───────┐
   │  Jev  │ ────> { action: "RETRY", confidence: 0.94, reason: "network_timeout" }
   └───────┘
```

Never burn expensive frontier tokens on basic state triage. Keep System 1 (Jev) on the hot path.
