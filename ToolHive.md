---
id: tech-toolhive
title: "ToolHive (MCP Security Gateway & Sandboxing)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/security
  - mcp
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Model Context Protocol (MCP)]]"
  - "[[Plugin4Shell]]"
  - "[[Proof-of-Control]]"
---

# 🛡️ ToolHive (MCP Security Gateway & Sandboxing)

> **ToolHive** is a containerized security gateway and proxy for Model Context Protocol (MCP) servers that enforces fine-grained authorization, network egress filtering, and isolated runtime sandboxes.

---

## 🔒 Security Layers
1. **Container Isolation:** Every tool runs inside ephemeral OCI containers.
2. **Egress Firewalling:** Prevents prompt-injected agents from exfiltrating environment variables or code.
3. **Schema Sanitization:** Validates incoming/outgoing payloads against strict JSON schemas.
