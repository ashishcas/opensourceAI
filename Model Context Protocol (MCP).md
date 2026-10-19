---
id: tech-mcp
title: "Model Context Protocol (MCP)"
type: concept
status: evergreen
tags:
  - wiki/tech
  - mcp
  - ai/tools
  - architecture/agentic
up: "[[MOC - Artificial Intelligence]]"
related:
  - "[[ToolHive]]"
  - "[[Speakeasy OpenAPI Generator]]"
  - "[[Kestra 2.0]]"
  - "[[Proof-of-Control]]"
  - "[[Plugin4Shell]]"
  - "[[LLM Wiki]]"
  - "[[Persistent Memory Systems]]"
---

# 🔌 Model Context Protocol (MCP)

> **MCP (Model Context Protocol)** is the open, universal standard created to connect AI agents with external tools, data sources, and execution environments safely and uniformly.

---

## 🏛️ Architecture

```mermaid
flowchart LR
    subgraph Host ["Agent Host Environment"]
        Agent["🤖 AI Agent"]
        Client["🔌 MCP Client"]
        Agent <--> Client
    end
    
    subgraph Protocol ["JSON-RPC 2.0 Transport (Stdio / SSE)"]
        Client <--> Gateway["🛡️ [[ToolHive|Security Gateway]]"]
    end
    
    subgraph Servers ["Specialized MCP Servers"]
        Gateway <--> PW["🌐 [[Playwright|Playwright MCP]]"]
        Gateway <--> GitS["🐙 Git MCP"]
        Gateway <--> KestraS["🧩 [[Kestra 2.0|Kestra Workflows]]"]
        Gateway <--> LogS["📊 Log / DB MCP"]
        Gateway <--> QmdS["💎 [[LLM Wiki|qmd Hybrid Knowledge MCP]]"]
    end
```

---

## 🔑 Key Concepts
1. **Resources:** Read-only data endpoints (file trees, logs, schemas) that provide passive context.
2. **Prompts:** Pre-packaged prompt templates and workflows exposed by the server.
3. **Tools:** Executable functions callable by the model with JSON Schema parameter definitions.

---

## 🛠️ Implementation Example (FastMCP in Python)

```python
from mcp.server.fastmcp import FastMCP
import subprocess

mcp = FastMCP("Playwright-Test-Runner")

@mcp.tool()
def run_playwright_test(spec_path: str, browser: str = "chromium") -> dict:
    """Executes a Playwright test specification and returns structured results."""
    cmd = ["npx", "playwright", "test", spec_path, f"--browser={browser}", "--reporter=json"]
    proc = subprocess.run(cmd, capture_output=True, text=True)
    return {
        "exit_code": proc.returncode,
        "stdout": proc.stdout[:2000],
        "failed": proc.returncode != 0
    }

if __name__ == "__main__":
    mcp.run()
```

---

## 🛡️ Security & Supply Chain Checklist
* Run servers inside isolated containers (e.g. [[ToolHive]]).
* Enforce strict input validation via JSON schema.
* Cryptographically audit server code to prevent [[Plugin4Shell]] supply-chain hijacking.
* Record every tool invocation into [[Proof-of-Control]] verifiable audit trails.
