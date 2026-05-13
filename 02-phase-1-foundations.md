[← Previous: Resources](01-resources.md) | [📋 Index](README.md) | [Next: Phase 2 →](03-phase-2-methodology.md)

---

# Phase 1 — Foundations + First Subagents

**Weeks 1–3 · ~18 hours · [Day-by-day walkthrough](appendix-a-week-1-walkthrough.md)**

## Goals
- Multi-surface fluency: CLI, Desktop (Chat/Cowork/Code), Agent View, mobile dispatch.
- The May 2026 control surface: `CLAUDE.md`, slash commands, Plan/Auto/Ask modes, hard deny rules, file checkpointing, `/recap`, `/bg`, `/schedule`.
- **Your first custom subagent** in `.claude/agents/`.
- Install and use the starter plugin stack: feature-dev, frontend-design, Context7, claude-mem.

## External Learning This Phase
- Anthropic Academy: **Claude Code 101** and **Claude Code in Action**.
- Watch the **Cherny + Sumner live coding session** from Code w/ Claude 2026.
- Read Simon Willison's `Code w/ Claude 2026` live blog (May 6, 2026).
- Subscribe to Simon Willison's blog; skim his last 6 months of `claude-code` posts.

## Tasks

### 1.1 — Personal `CLAUDE.md` and dotfiles (Week 1, ~2h)
Global `~/.claude/CLAUDE.md`: coding preferences, default stack (locked — see [README](README.md)), non-negotiables ("always write tests", "explain before refactoring", "prefer TS over JS", "Hono not Express"). Commit to a public `dotfiles` repo.

Also create an `AGENTS.md` alongside it. AGENTS.md is the cross-harness convention (works with Claude Code, Codex CLI, and most other agentic harnesses); CLAUDE.md is Claude-specific. The convention forming in mid-2026: put portable engineering preferences in AGENTS.md, Claude-specific quirks in CLAUDE.md, each file referencing the other. Most teams converging on AGENTS.md as primary.

### 1.2 — Calibration refactor (Week 1, ~3h)
Pick a small repo you own. Run Claude Code on it in CLI, then Desktop's Code tab, then Cowork. Generate a project-level `CLAUDE.md`. Suggest three improvements, implement one. Note differences between surfaces in your journal.

### 1.3 — First plugins (Week 2, ~2h)
Install: `feature-dev` (Anthropic official, ~89k installs — the 7-phase workflow), `frontend-design`, `Context7` (live docs lookup, kills the "API deprecated 3 months ago" hallucination class), `claude-mem` (persistent memory across sessions), `typescript-lsp`, the `github` and `playwright` partner plugins.

Use each at least twice on real work. Read what they actually do before installing the next.

### 1.4 — Your first custom subagent (Week 2, ~2h)
Create `.claude/agents/code-reviewer.md`. Define a code reviewer subagent: own model (route to Haiku 4.5 to save cost), own tools, own context window, its own system prompt. Use it via the Task tool on real code.

Before writing yours, browse 5–10 examples in `wshobson/agents` on GitHub. Pattern recognition matters more than docs here.

The goal: feel the difference between "main Claude with a longer prompt" and "main Claude delegates to a specialist that returns with a structured result." This is the foundational mental model for everything from Phase 5 onwards.

### 1.5 — Agent View familiarity (Week 2, ~1h)
Open Agent View (`/agents` or via the Desktop sidebar). Dispatch 2–3 background sessions for unrelated tasks. Switch between them. Use `/bg` from inside a session to spawn a background task. Reply to a session without attaching to the full transcript.

### 1.6 — Project A: Landing page (Weeks 2–3, ~8h)
A landing page for a fake (or real) micro-product. **Stack: Next.js App Router + Tailwind + shadcn/ui.** Use the `frontend-design` plugin throughout.

Workflow: Plan mode first, approve plan, switch to Auto accept edits to execute. Use `commit-commands`'s `/commit` for atomic commits.

Requirements:
- Hero, three feature cards, pricing tiers, FAQ, footer.
- Deploy to Vercel.
- One subtle interaction (animated counter, accordion).
- Use your code-reviewer subagent to review the final code before merging to main.

## Phase 1 Milestone
- [ ] Personal `CLAUDE.md` in a public dotfiles repo.
- [ ] 5+ plugins installed; each used at least twice.
- [ ] One custom subagent in `.claude/agents/`, used on real code.
- [ ] Anthropic Academy: 101 and Claude Code in Action complete (certificates collected).
- [ ] Agent View comfortable — you can dispatch and switch without thinking.
- [ ] Project A deployed.
- [ ] Journal entry: "Three ways Claude Code differs from Copilot in my daily flow."

## Stretch
- Build a second subagent: a `commit-message-writer` that takes a diff and produces conventional commit messages.
- Try the `learning-output-style` plugin — it narrates as it goes.
- Watch one of Cherny's strategic talks (AI Ascent or AI Engineer World's Fair) end-to-end.

---

[← Previous: Resources](01-resources.md) | [📋 Index](README.md) | [Next: Phase 2 →](03-phase-2-methodology.md)
