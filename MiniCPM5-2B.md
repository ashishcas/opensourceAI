---
id: tech-minicpm5-2b
title: "MiniCPM5-2B (Small Local Model)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - ai/slm
  - ai/local-inference
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[Model Routing]]"
  - "[[vLLM]]"
  - "[[Ollama]]"
---

# 🧠 MiniCPM5-2B (Small Local Model)

> **MiniCPM5-2B** (by OpenBMB) is a 2-billion parameter model demonstrating that high-quality synthetic data and optimized architectures enable compact SLMs to match or exceed older 7B–14B models on discrete tasks.

---

## 🎯 Best Roles for MiniCPM5-2B in Local Pipelines
* **Task Routing:** Classify whether a prompt needs a frontier model or local processing.
* **Log Triage:** Categorize stack traces and extract failure lines in <50ms.
* **Extraction:** Extract structured JSON from raw web scraping or terminal output.
* **Gatekeeper:** Pre-filter safe/unsafe tool calls locally before contacting cloud APIs.
