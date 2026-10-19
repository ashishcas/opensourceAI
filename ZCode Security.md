---
id: tech-zcode-security
title: "ZCode Privacy & Local Codebase Indexing"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/security
  - ai/privacy
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Plugin4Shell]]"
  - "[[Proof-of-Control]]"
---

# 🔐 ZCode Privacy & Local Codebase Indexing

> Following security incidents where cloud coding tools silently uploaded local repositories to third-party servers, **Local Codebase Indexing** has become a mandatory enterprise requirement.

---

## 🛡️ Zero-Exfiltration Local Architecture
```text
Local Repo ──> Local Embedder (MiniCPM / BGE) ──> Local Vector Store (Qdrant) ──> Local Agent
```
Sensitive source code never leaves localhost; only scrubbed context diffs are transmitted to frontier models.
