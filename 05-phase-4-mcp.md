[← Previous: Phase 3](04-phase-3-agents-skills.md) | [📋 Index](README.md) | [Next: Phase 5 →](06-phase-5-multi-agent.md)

---

# Phase 4 — Building MCP Servers

**Weeks 10–13 · ~24 hours**

The highest-leverage phase for portfolio. A useful MCP server is rare, gets installed, and can become a product on its own or a managed-hosting offer. 2,000+ MCP servers exist in the official registry as of Q1 2026; the majority are mediocre. Yours doesn't have to be.

## Goals
- Build a real MCP server (Python + FastMCP — that's the lane, no stack choice).
- Three primitives: **tools** (actions with side effects), **resources** (readable data), **prompts** (templates).
- Deploy remote MCP with OAuth 2.1 + PKCE.
- Test from ≥3 clients: Claude Code, Claude Desktop, Cursor or ChatGPT.

## External Learning This Phase
- Anthropic Academy: **Introduction to MCP** and **MCP: Advanced Topics**.
- `modelcontextprotocol.io/docs/develop/build-server`.
- tech-insider.org's "MCP Server Tutorial: 12 Steps Python FastMCP [2026]".
- Composio and MintMCP blog posts on enterprise MCP.
- The "50 MCP vulnerabilities, 30 CVEs in 60 days, 13 critical" report — read before you deploy.
- One MCP server source from `github.com/modelcontextprotocol/servers`.

## Tasks

### 4.1 — Hello-world MCP server (Week 10, ~4h)
Weather-server example in Python with FastMCP. Connect to Claude Code and Claude Desktop. Verify via MCP Inspector.

### 4.2 — Scaffold with the `mcp-builder` skill (Week 10, ~2h)
Install Composio's `mcp-builder` plugin. Scaffold a second hello-world. Compare to what you wrote by hand.

### 4.3 — Project D: A useful MCP server (Weeks 11–13, ~18h)
Pick something specific and genuinely useful. The best portfolio MCPs wrap one thing well.

Project ideas:
- An MCP for a niche API with no good coverage yet (Pocket, Goodreads, Reddit Saved, a budgeting app, your bank's API if it has one).
- A "personal KB" MCP that lets Claude query your Obsidian or Logseq notes locally.
- A "local dev" MCP exposing your local Docker containers, DB schemas, and recent logs as resources.
- A "Notion second-brain" MCP that augments the official Notion MCP with workflows it doesn't cover.
- *(Consider:)* A "news source" MCP that your [Project E digest bot](06-phase-5-multi-agent.md) can consume — pre-compounding.

Requirements:
- ≥5 tools, ≥2 resources, ≥1 prompt template.
- Auth: API keys via env vars in v1; OAuth 2.1 + PKCE if time allows.
- README with quickstart + real use cases.
- Deploy remotely (Fly.io recommended).
- Tested from 3+ MCP clients.
- Listed on a public MCP registry.

## Phase 4 Milestone
- [ ] Hello-world MCP runs and is connected.
- [ ] Project D deployed remotely, publicly listed, used by you on real work.
- [ ] Verified working from 3 clients.
- [ ] You can explain tools vs resources vs prompts without checking docs.
- [ ] Anthropic Academy: MCP Intro and MCP Advanced courses complete.
- [ ] Journal: what surprised you, what you'd do differently.

---

[← Previous: Phase 3](04-phase-3-agents-skills.md) | [📋 Index](README.md) | [Next: Phase 5 →](06-phase-5-multi-agent.md)
