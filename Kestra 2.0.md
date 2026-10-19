---
id: tech-kestra-2
title: "Kestra 2.0 (Deterministic Workflow Orchestration as MCP)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/orchestration
  - mcp
  - testing/playwright
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Model Context Protocol (MCP)]]"
  - "[[Playwright]]"
  - "[[Speakeasy OpenAPI Generator]]"
---

# 🧩 Kestra 2.0 (Deterministic Workflows as MCP)

> **Kestra 2.0** (Apache 2.0) is an open-source orchestration platform that exposes deterministic workflows directly as **Model Context Protocol (MCP) tools**.

---

## 🏛️ Architecture: AI Selection + Deterministic Execution

```mermaid
flowchart LR
    Agent["🤖 AI Agent"] -->|Selects Action| MCP["🔌 [[Model Context Protocol (MCP)]]"]
    MCP --> Kestra["🧩 [[Kestra 2.0]] Engine"]
    
    subgraph DeterministicPipelines ["Deterministic Execution Engine"]
        Kestra --> DB["Database Migrations"]
        Kestra --> CI["CI/CD Deployment"]
        Kestra --> PW["Playwright Regression Suite"]
    end
    
    PW --> Results["Allure Reports & Artifacts"]
    Results --> Agent
```

---

## 💡 Practical Takeaway for Playwright AI Engineer
Never let the LLM ad-hoc script complex test runners or database reset sequences in bash. Expose a pre-validated **Kestra Workflow** via MCP and allow the agent to trigger and monitor it deterministically.
