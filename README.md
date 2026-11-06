<div align="center">

  <h1>⚡ Supercharged MCP</h1>

  <p><strong>A battle-tested arsenal of production Model Context Protocol (MCP) servers, 1-click configurations, security sandboxes, and Python FastMCP starters for Claude Desktop, Cursor, and autonomous AI agents.</strong></p>

  <p>
    <img src="https://img.shields.io/badge/Protocol-Model%20Context%20Protocol-blueviolet?style=for-the-badge&logo=anthropic" alt="MCP" />
    <img src="https://img.shields.io/badge/Clients-Claude%20%7C%20Cursor%20%7C%20Antigravity-orange?style=for-the-badge&logo=visualstudiocode" alt="Clients" />
    <img src="https://img.shields.io/badge/Python-FastMCP%20Ready-blue?style=for-the-badge&logo=python" alt="Python" />
    <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License" />
  </p>

  <p>
    <a href="#-1-click-copy-paste-configurations"><img src="https://img.shields.io/badge/Configs-Claude%20%26%20Cursor%20JSON-blue?style=flat-square" /></a>
    <a href="#-the-6-core-mcp-server-suites"><img src="https://img.shields.io/badge/Suites-6%20Production%20Categories-blueviolet?style=flat-square" /></a>
    <a href="#-the-30-second-custom-mcp-server-fastmcp"><img src="https://img.shields.io/badge/Python-Build%20Custom%20Tools-orange?style=flat-square" /></a>
    <a href="#-security--sandbox-envelopes"><img src="https://img.shields.io/badge/Security-Docker%20Sandboxes-red?style=flat-square" /></a>
    <img src="https://img.shields.io/badge/PRs-Welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome" />
  </p>

  <sub>Star ⭐ this repository to equip your Claude, Cursor, and agentic workflows with verified superpower tools!</sub>

</div>

---

## 📑 Table of Contents

- [💡 What is Model Context Protocol (MCP)?](#-what-is-model-context-protocol-mcp)
- [🏗️ How MCP Works (Architecture Diagram)](#️-how-mcp-works-architecture-diagram)
- [🚀 1-Click Copy-Paste Configurations](#-1-click-copy-paste-configurations)
  - [Claude Desktop Configuration (`claude_desktop_config.json`)](#claude-desktop-configuration)
  - [Cursor IDE Configuration (`.cursor/mcp.json`)](#cursor-ide-configuration)
- [🧰 The 6 Core Production MCP Server Suites](#-the-6-core-mcp-server-suites)
  - [1. Database & State Suite (PostgreSQL, SQLite, Redis)](#1-database--state-suite)
  - [2. Developer & Git Suite (GitHub, Local Filesystem, Git CLI)](#2-developer--git-suite)
  - [3. Live Web & Research Suite (Brave Search, Fetch, Puppeteer)](#3-live-web--research-suite)
  - [4. Persistent Memory & Knowledge Graph Suite](#4-persistent-memory--knowledge-graph-suite)
  - [5. Execution & Terminal Sandboxing Suite](#5-execution--terminal-sandboxing-suite)
  - [6. Productivity & Issue Tracking Suite (Slack, Linear, Notion)](#6-productivity--issue-tracking-suite)
- [🐍 The 30-Second Custom MCP Server (Python FastMCP Starter)](#-the-30-second-custom-mcp-server-python-fastmcp-starter)
- [🛡️ Security & Sandbox Envelopes (Don't Wipe My Hard Drive)](#️-security--sandbox-envelopes-dont-wipe-my-hard-drive)
- [⭐ Explore My Other Repositories](#-explore-my-other-repositories)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

---

## 💡 What is Model Context Protocol (MCP)?

The **Model Context Protocol (MCP)**, introduced as an open standard by Anthropic, is the **USB-C port for AI applications**.

Before MCP, connecting an AI model (like Claude or GPT-4) to your tools required writing custom, fragile API wrappers for every platform. MCP standardizes communication between **LLM Clients** (Claude Desktop, Cursor, Antigravity) and **Local/Remote Tool Servers** via JSON-RPC 2.0 over standard I/O (`stdio`) or Server-Sent Events (`sse`).

With MCP enabled, your AI agent can:
* Directly inspect PostgreSQL schemas and run validated SQL queries.
* Inspect, diff, branch, and push Git repositories autonomously.
* Browse the live web, scrape dynamic JavaScript pages, and bypass paywalls.
* Store persistent knowledge graphs that survive chat context resets.

---

## 🏗️ How MCP Works (Architecture Diagram)

```mermaid
flowchart LR
    subgraph Host_Environment ["AI Client Host"]
        ClaudeDesktop["Claude Desktop"]
        CursorIDE["Cursor IDE"]
        AgentRuntime["Autonomous AI Agent"]
    end

    subgraph MCP_Protocol ["JSON-RPC 2.0 via Stdio / SSE Transport"]
        ProtocolPipe["MCP Standard Protocol Bridge"]
    end

    subgraph Production_Servers ["MCP Tool Servers"]
        direction TB
        PostgresMCP["🗄️ PostgreSQL MCP\n(Schema inspection & SQL)"]
        GitHubMCP["🐙 GitHub MCP\n(PRs, commits & code search)"]
        WebMCP["🌐 Brave Search / Fetch MCP\n(Live internet & dynamic DOM)"]
        MemoryMCP["🧠 Memory Graph MCP\n(Persistent entity relationships)"]
        DockerMCP["🐳 Sandboxed Terminal MCP\n(Isolated code execution)"]
    end

    ClaudeDesktop --> ProtocolPipe
    CursorIDE --> ProtocolPipe
    AgentRuntime --> ProtocolPipe

    ProtocolPipe --> PostgresMCP
    ProtocolPipe --> GitHubMCP
    ProtocolPipe --> WebMCP
    ProtocolPipe --> MemoryMCP
    ProtocolPipe --> DockerMCP
```

---

## 🚀 1-Click Copy-Paste Configurations

### Claude Desktop Configuration
Locate your configuration file:
* **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
* **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
* **Linux:** `~/.config/Claude/claude_desktop_config.json`

Copy and paste this production-ready configuration:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "C:\\Users\\YOUR_USERNAME\\Projects"
      ]
    },
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://postgres:password@localhost:5432/my_database"
      ]
    },
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_yourPersonalAccessTokenHere"
      }
    },
    "brave-search": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-brave-search"
      ],
      "env": {
        "BRAVE_API_KEY": "BSA_yourBraveSearchAPIKeyHere"
      }
    },
    "memory": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-memory"
      ]
    }
  }
}
```

---

### Cursor IDE Configuration
Create or edit `.cursor/mcp.json` in your repository root or global Cursor settings:

```json
{
  "mcpServers": {
    "git": {
      "command": "uvx",
      "args": ["mcp-server-git"]
    },
    "fetch": {
      "command": "uvx",
      "args": ["mcp-server-fetch"]
    },
    "sqlite": {
      "command": "uvx",
      "args": ["mcp-server-sqlite", "--db-path", "./app.db"]
    }
  }
}
```

---

## 🧰 The 6 Core Production MCP Server Suites

---

### 1. Database & State Suite

| Server | Transport | Command | What It Gives Your Agent |
| :--- | :---: | :--- | :--- |
| **`server-postgres`** | `stdio` | `npx -y @modelcontextprotocol/server-postgres <CONN_STRING>` | Inspect schemas, foreign keys, explain queries, run `SELECT` statements directly from chat. |
| **`server-sqlite`** | `stdio` | `uvx mcp-server-sqlite --db-path <PATH>` | Embedded database analysis for local projects, test fixtures, and telemetry logs. |
| **`mcp-server-redis`** | `stdio` | `uvx mcp-server-redis --url <REDIS_URL>` | Inspect cache keys, token buckets, user sessions, and pub/sub queues. |

---

### 2. Developer & Git Suite

| Server | Transport | Command | What It Gives Your Agent |
| :--- | :---: | :--- | :--- |
| **`server-github`** | `stdio` | `npx -y @modelcontextprotocol/server-github` | Autonomous PR opening, repository search, commit creation, and issue triage. |
| **`server-filesystem`** | `stdio` | `npx -y @modelcontextprotocol/server-filesystem <DIR>` | Safe, scoped directory reading, file editing, and directory tree traversal. |
| **`mcp-server-git`** | `stdio` | `uvx mcp-server-git` | Read git history, view branches, inspect uncommitted diffs, and generate changelogs. |

---

### 3. Live Web & Research Suite

| Server | Transport | Command | What It Gives Your Agent |
| :--- | :---: | :--- | :--- |
| **`server-brave-search`** | `stdio` | `npx -y @modelcontextprotocol/server-brave-search` | Live internet web search, real-time news retrieval, and documentation lookups. |
| **`server-fetch`** | `stdio` | `uvx mcp-server-fetch` | Converts HTML web pages into clean, LLM-optimized Markdown while stripping advertising bloat. |
| **`server-puppeteer`** | `stdio` | `npx -y @modelcontextprotocol/server-puppeteer` | Headless Chrome browser automation: execute clicks, fill forms, and take screenshots. |

---

### 4. Persistent Memory & Knowledge Graph Suite

| Server | Transport | Command | What It Gives Your Agent |
| :--- | :---: | :--- | :--- |
| **`server-memory`** | `stdio` | `npx -y @modelcontextprotocol/server-memory` | Constructs an open knowledge graph (`Entities` ➔ `Relations` ➔ `Observations`) that persists across new chats. |

* **Example:** Tell Claude: *"Remember that our production database is hosted on Neon and uses PostgreSQL 16."* When you start a brand new conversation next week, Claude retrieves that memory from the knowledge graph.

---

### 5. Execution & Terminal Sandboxing Suite

| Server | Transport | Command | What It Gives Your Agent |
| :--- | :---: | :--- | :--- |
| **`mcp-shell`** *(Dockerized)* | `stdio` | `docker run -i --rm mcp/shell-sandbox` | Gives agents a bash terminal wrapped in an isolated Linux container with memory limits. |

---

### 6. Productivity & Issue Tracking Suite

| Server | Transport | Command | What It Gives Your Agent |
| :--- | :---: | :--- | :--- |
| **`server-slack`** | `stdio` | `npx -y @modelcontextprotocol/server-slack` | Read incident channels, post build notifications, and summarize team discussions. |
| **`mcp-server-linear`** | `stdio` | `npx -y mcp-server-linear` | Create tickets, update sprint boards, link commits, and assign bug fixes. |
| **`mcp-server-notion`** | `stdio` | `npx -y @modelcontextprotocol/server-notion` | Search company wikis, read product specs, and update internal roadmaps. |

---

## 🐍 The 30-Second Custom MCP Server (Python FastMCP Starter)

Anthropic’s official `mcp` Python library includes **FastMCP**, an ultra-clean framework inspired by FastAPI:

### 1. Install FastMCP
```bash
pip install "mcp[cli]"
```

### 2. Write your custom server (`my_tools.py`)
```python
from mcp.server.fastmcp import FastMCP
import datetime
import subprocess

# Initialize MCP Server
mcp = FastMCP("Developer-Tools")

@mcp.tool()
def get_system_uptime() -> str:
    """Returns the current machine timestamp and local date."""
    return f"Current server time: {datetime.datetime.now().isoformat()}"

@mcp.tool()
def calculate_token_cost(prompt_tokens: int, completion_tokens: int, model: str = "claude-3-5-sonnet") -> dict:
    """Calculates the exact API billing cost for a given token volume."""
    rates = {
        "claude-3-5-sonnet": {"input": 3.00 / 1_000_000, "output": 15.00 / 1_000_000},
        "gpt-4o": {"input": 2.50 / 1_000_000, "output": 10.00 / 1_000_000},
    }
    rate = rates.get(model, rates["claude-3-5-sonnet"])
    total_cost = (prompt_tokens * rate["input"]) + (completion_tokens * rate["output"])
    return {
        "model": model,
        "input_cost": f"${prompt_tokens * rate['input']:.6f}",
        "output_cost": f"${completion_tokens * rate['output']:.6f}",
        "total_cost": f"${total_cost:.6f}"
    }

if __name__ == "__main__":
    mcp.run(transport="stdio")
```

### 3. Register it with Claude Desktop
Add to `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "my-dev-tools": {
      "command": "python",
      "args": ["C:\\path\\to\\my_tools.py"]
    }
  }
}
```

---

## 🛡️ Security & Sandbox Envelopes (Don't Wipe My Hard Drive)

Giving an autonomous LLM agent tool-calling access to your terminal or database can be catastrophic if not guarded:

```
[Agent Suggestion] ➔ "rm -rf /" or "DROP TABLE users;" ➔ [Disaster]
```

### The 3 Golden Rules of Production MCP Security:

1. **Read-Only Database Credentials:**
   * Never connect `server-postgres` using a superuser (`postgres`) account.
   * Create a dedicated read-only role with no `DELETE`, `UPDATE`, or `DROP` permissions:
     ```sql
     CREATE ROLE mcp_readonly WITH LOGIN PASSWORD 'strong_password';
     GRANT CONNECT ON DATABASE my_db TO mcp_readonly;
     GRANT USAGE ON SCHEMA public TO mcp_readonly;
     GRANT SELECT ON ALL TABLES IN SCHEMA public TO mcp_readonly;
     ```
2. **Directory Scoping for Filesystem MCP:**
   * Never grant access to root (`C:\` or `/`). 
   * Only point the filesystem server to a specific workspace directory (e.g., `~/Projects/app`).
3. **Containerized Terminal Execution:**
   * Run command-line execution tools inside a Docker envelope with capped memory ($256\text{MB}$) and disabled root privileges (`--user 1000:1000`).

---

## ⭐ Explore My Other Repositories

| Repository | Description | Domain |
| :--- | :--- | :--- |
| ⚡ [**Zero-Bill-Cloud-Stack**](https://github.com/Gana-Y/Zero-Bill-Cloud-Stack) | A curated matrix and production reference architecture for $0.00 cloud infrastructure. | `Cloud Infrastructure` |
| 🧠 [**LLM-System-Patterns**](https://github.com/Gana-Y/LLM-System-Patterns) | Production design patterns, latency budgets, failure modes, and architectural trade-offs for real-world LLMs. | `AI System Design` |
| 🚀 [**Florix_AI**](https://github.com/Gana-Y/Florix_AI) | Production-grade multimodal AI study platform with in-database RAG and adaptive spaced repetition. | `Full-Stack RAG / AI` |
| ⚡ [**vesper-engine**](https://github.com/Gana-Y/vesper-engine) | Hardened, high-performance sandboxed code execution engine & online judge arbiter enforcing Linux cgroups. | `Systems / Linux / Python` |
| 📈 [**OrderCore**](https://github.com/Gana-Y/OrderCore) | High-throughput Limit Order Book & matching engine in Python (FastAPI/WebSockets) achieving 136k orders/sec. | `Low-Latency Systems / FinTech` |
| 🎓 [**Free-Courses**](https://github.com/Gana-Y/Free-Courses) | Curated catalog of verified 100% free technical courses & certifications from NVIDIA, Anthropic, AWS, Google, Harvard, and MIT. | `Developer Education` |

---

## 🤝 Contributing

Contributions, new MCP servers, and verified configuration templates are welcome!

1. Fork this repository (`git checkout -b feature/add-new-mcp-server`).
2. Add your server under the appropriate suite with 1-click JSON configurations.
3. Commit with a semantic message (`git commit -m "feat: add ClickHouse MCP server"`).
4. Open a Pull Request.

---

## 👨‍💻 Maintainer

Maintained with ❤️ by **[Ganesh Yandigeri](https://github.com/Gana-Y)**

- 🌐 **Portfolio:** [ganesh-y.vercel.app](https://ganesh-y.vercel.app)
- 💼 **LinkedIn:** [linkedin.com/in/ganesh-yandigeri](https://linkedin.com/in/ganesh-yandigeri)
- 🐙 **GitHub:** [@Gana-Y](https://github.com/Gana-Y)

---

## 📜 License

Distributed under the [MIT License](LICENSE). Build autonomous, powerful tools!
