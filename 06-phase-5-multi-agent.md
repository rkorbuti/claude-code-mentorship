[← Previous: Phase 4](05-phase-4-mcp.md) | [📋 Index](README.md) | [Next: Phase 6 →](07-phase-6-capstone.md)

---

# Phase 5 — Programmatic Multi-Agent + Project E

**Weeks 14–17 · ~24 hours**

The big phase. Three approaches to multi-agent in sequence: hand-built → Anthropic Managed Agents → one community orchestrator. You build the same scaffolding three ways to feel what each layer hides. Then you ship **Project E: the Claude Code daily digest bot** — your continuing-education infrastructure for the rest of the program.

## Goals
- Build a multi-agent system three ways.
- Outcomes for rubric-based grading.
- Advisor tool for cost-routing (Sonnet executor + Opus advisor).
- Project E: a working multi-agent Telegram bot that delivers a daily Claude Code / vibe coding digest, used by you daily.

## Core Patterns This Phase Teaches

Two advanced patterns that Project E specifically leans on:

**Ralph Wiggum loop.** An autonomous agent pattern where the agent pulls work from a queue (a GitHub Issues backlog, a database table, a TODO file), does the work, evaluates against criteria, retries on failure, and loops until the queue is empty or the day is done. Named after the Simpsons character; the joke is that "do the next thing on the list, then check if it's good" beats sophisticated coordination most of the time. Your Phase 3 stop hook was the mechanism; this is the architecture. Project E's coordinator pulls "today's sources," dispatches work, evaluates each item against the Outcomes rubric, retries failures, ships when done. The full pattern is documented with a runnable repo in `shanraisshan/claude-code-best-practice` — read it before week 14.

**Subagent challenge pattern.** When you want quality on an output, spawn multiple subagents with different perspectives that challenge each other before consensus. Cherny's `/code-review` command does this — style checker, history reader, bug flagger all run in parallel from different angles, with a final synthesizer reconciling. The adversarial dynamic produces cleaner results than a single critical reviewer. You will use this for Project E's editor: spawn a fact-checker and a redundancy-checker alongside the main editor, have them argue before the digest ships.

## External Learning This Phase
- Anthropic Academy: **Building with the Claude API**.
- Claude Agent SDK docs in full: `platform.claude.com/docs/en/agent-sdk`.
- Managed Agents docs: `platform.claude.com/docs/en/managed-agents` (beta header `managed-agents-2026-04-01`).
- Anthropic's May 6, 2026 "New in Claude Managed Agents" blog post.
- letsdatascience.com "Build Production AI Agents with Claude Agent SDK".
- Advisor tool docs (beta header `advisor-tool-2026-03-01`).
- One community orchestrator's docs in full — pick one.

## Tasks

### 5.1 — Hand-built coordinator + specialists (Week 14, ~6h)
Build a small multi-agent system from scratch with the **Agent SDK directly in Python**. No framework. Coordinator + 3 specialists doing a research task end-to-end.

Why: teaches you the primitives. How messages flow, how context is isolated, how subagents return structured results, how to handle partial failures. **Don't skip this for the abstraction.** Phase 5.4 will be easier because of this.

### 5.2 — Same scaffolding, Managed Agents multi-agent API (Week 15, ~3h)
Rebuild 5.1 using Anthropic's Managed Agents multi-agent API. YAML config, coordinator decides at runtime when to delegate. Write down what the abstraction gives you (state, retries, persistence, console traces) and what it costs (less escape-hatch, vendor lock).

### 5.3 — Try one community orchestrator (Week 15, ~3h)
Pick **one**: claude-flow, maestro-orchestrate, or Conductor. Build a third version or extend the existing one. Don't try them all.

### 5.4 — Project E: Claude Code Daily Digest Bot (Weeks 16–17, ~12h)

**The product:** A Telegram bot that delivers a daily 5–7 item briefing of new content in the Claude Code / agentic coding ecosystem. Personal use first; openable to others later.

**Why this specifically:**
- Genuinely useful to you — the ecosystem moves fast enough that staying current is real work.
- Real multi-agent decomposition (5 specialist agents with different jobs).
- Outcomes rubric is natural and powerful here (does the editor say the digest is high-quality?).
- Personal use means you'll actually iterate based on real signal.
- Doubles as your continuing-education infrastructure for Phase 6 and beyond.

**Sources to monitor:**

| Source | What to extract |
|--------|-----------------|
| `code.claude.com/docs/en/whats-new` | New Claude Code features per week |
| `claude.com/blog` and `anthropic.com/news` | Official announcements |
| X/Twitter: `@bcherny`, Cat Wu, `@AnthropicAI`, `@indydevdan` | Team takes, hints, soft launches |
| `simonwillison.net` — `claude-code` tag | High-signal commentary |
| `blog.fsck.com` (Jesse Vincent) | Methodology and Superpowers evolution |
| `/r/ClaudeCode` and `/r/ClaudeAI` | Top of day |
| Hacker News | Filter for Claude/Anthropic/agent terms |
| GitHub trending: `claude-code`, `mcp`, `anthropic` topics | New tooling |
| `claude.com/plugins` | New plugins in the official marketplace |
| Selected YouTube channels (Anthropic, The Algorithm, Edmund Yong, Latent Space, IndyDevDan) | New videos |

**Agent team:**

- **Coordinator** — orchestrates the daily run, manages state. Implements the **Ralph Wiggum loop**: pull from source queue, dispatch, evaluate, retry, ship.
- **Source pollers** (one per source family, run in parallel) — fetch new content since last run.
- **Curator** — dedupes, picks top 5–7 by likely relevance, considers your feedback history.
- **Summarizer** — writes 1–2 sentence summaries with links.
- **Editor (subagent challenge pattern)** — three subagents running in parallel: clarity checker, fact-checker (validates URLs and source credibility), redundancy-checker (against the last 7 days). A final synthesizer reconciles their flags. Outcomes-graded; can send the whole run back for another pass.
- **Telegram poster** — formats with inline buttons (read more / save / "show less of this topic" — last one feeds the curator).

**Stack:**
- Python service with Claude Agent SDK + `python-telegram-bot`.
- Postgres on Neon (sources, items, feedback log, daily history).
- Scheduled run via Fly.io scheduled machines or a cron container.
- Deployed to Fly.io.

**Outcomes rubric (starting point — refine after first week):**
```
Each item must:
- Have a working URL (HEAD-check it).
- Have a 1–2 sentence summary, no more, no less.
- Not duplicate any item from the last 7 days.
- Be genuinely about Claude Code, agents, or vibe coding (not generic AI news).
- Be from a credible source (no SEO content farms).

Each digest must:
- Have 5–7 items.
- Cover at least 2 of: tooling, methodology, plugin/MCP releases, talks/podcasts, community projects.
- Be ready by 9am local time.
```

**Requirements for milestone:**
- ≥4 specialist subagents besides the coordinator.
- Outcomes rubric in production (editor uses it; logs of grades persist).
- Advisor tool active: Sonnet 4.6 executor, Opus 4.7 advisor on hard editorial calls.
- Telegram interface with inline keyboards.
- Webhook on failure to your inbox.
- Running daily, used by you for ≥7 days before Phase 5 ends.
- Feedback signal (clicks, saves) logged for use by the curator.

**Architecture decisions to make explicitly:**
- Source pollers in parallel or sequential? (Start parallel — that's the multi-agent value.)
- How do you handle rate limits on sources? (Cache aggressively, respect robots.txt, identify your bot.)
- Should the editor have veto power? (Yes — Outcomes rubric should be able to send back. This is the Ralph Wiggum retry loop.)
- How does feedback feed back into the curator? (Log clicks → weight source preferences nightly.)
- Is the editor a single agent or a challenge team? (Use the subagent challenge pattern.)

## Phase 5 Milestone
- [ ] Hand-built coordinator system works (5.1).
- [ ] Same scaffolding rebuilt via Managed Agents API (5.2).
- [ ] Same scaffolding extended via one community orchestrator (5.3).
- [ ] Honest written opinion on tradeoffs between the three approaches.
- [ ] Project E deployed, running daily, used for ≥7 days.
- [ ] Ralph Wiggum loop running in Project E's coordinator (queue → dispatch → evaluate → retry → ship).
- [ ] Subagent challenge pattern running in Project E's editor (≥3 challengers + synthesizer).
- [ ] Outcomes rubric in active use, refined at least once.
- [ ] Advisor cost-routing measurable in your usage data.

## Stretch
- Apply for **Dreaming** access at `claude.com/form/claude-managed-agents`. If granted, add nightly memory curation — perfect fit for the digest bot.
- Real eval harness with a directory of test inputs + expected behaviors, run in CI.
- Open the bot to 2–3 other people; collect feedback.

---

[← Previous: Phase 4](05-phase-4-mcp.md) | [📋 Index](README.md) | [Next: Phase 6 →](07-phase-6-capstone.md)
