---
id: tech-speakeasy-openapi
title: "Speakeasy OpenAPI Generator (Auto-MCP Synthesis)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - openapi
  - mcp
  - ai/tools
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Model Context Protocol (MCP)]]"
  - "[[Kestra 2.0]]"
---

# 🧩 Speakeasy OpenAPI Generator

> **Google and Speakeasy's Open-Source Code Generator** automatically turns **OpenAPI 3.x specifications** into type-safe client SDKs, CLIs, and **Model Context Protocol (MCP) servers** across 7 languages.

---

## 🚀 The Single-Contract Workflow

```mermaid
flowchart TD
    Contract["📜 OpenAPI 3.x Contract"] --> Gen["🧩 Speakeasy Generator"]
    Gen --> SDK["📦 TypeScript & Python SDKs"]
    Gen --> CLI["💻 Terminal CLI Tools"]
    Gen --> MCP["🔌 Model Context Protocol Server"]
```

Eliminates manual wrapper authoring by compiling API contracts directly into verifiable AI agent tools.
