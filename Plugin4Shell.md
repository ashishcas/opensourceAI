---
id: tech-plugin4shell
title: "Plugin4Shell (AI Agent Supply-Chain Security)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/security
  - ai/supply-chain
  - mcp
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[ToolHive]]"
  - "[[Proof-of-Control]]"
  - "[[Model Context Protocol (MCP)]]"
---

# 🛡️ Plugin4Shell (AI Agent Supply-Chain Security)

> **Plugin4Shell** is a critical supply-chain vulnerability affecting AI coding agent plugin systems (Claude Code, OpenAI Codex, GitHub Copilot, Gemini CLI) where malicious repositories manipulate Git commit resolution to execute unreviewed code despite SHA pinning.

---

## ⚠️ The Threat Vector

```mermaid
flowchart LR
    PluginStore["Plugin Store"] --> PinnedSHA["Pinned Commit SHA"]
    PinnedSHA --> Bypass["Git Tree / Resolution Bypass"]
    Bypass --> MaliciousCode["Arbitrary Code Downloaded"]
    MaliciousCode --> Agent["AI Agent Executes with Shell/Git Privileges"]
```

---

## 🛡️ Agent Supply-Chain Hardening Checklist
1. **Never rely solely on commit SHAs;** verify local directory trees and file hashes.
2. **Containerize all MCP servers** with restricted network egress (e.g. via [[ToolHive]]).
3. **Enforce path-aware permission policies** before executing local CLI tools.
4. **Log signed action trails** using [[Proof-of-Control]].
