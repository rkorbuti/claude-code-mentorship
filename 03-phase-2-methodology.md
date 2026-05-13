[← Previous: Phase 1](02-phase-1-foundations.md) | [📋 Index](README.md) | [Next: Phase 3 →](04-phase-3-agents-skills.md)

---

# Phase 2 — Methodology + Local Multi-Agent

**Weeks 4–6 · ~18 hours**

The multi-agent foundation. You will use Claude Code's **Agent Teams** experimental feature and git worktrees to run several Claude instances on the same project at once.

## Goals
- Use three methodology frameworks on real code; pick a primary + secondary.
- Use Claude Code's Agent Teams (experimental, v2.1.32+): `export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`.
- Use git worktrees to give each agent isolated working directories.
- Try **one** community orchestrator (claude-squad) — just one.
- Codex plugin for cross-model adversarial review.

## Core Workflow Patterns This Phase Teaches

Three patterns to internalize. You will use all three in every subsequent phase. They are the spine of every methodology framework dressed up differently.

**Plan/Execute/Clear loop.** Do planning work in its own session (or use `/plan` mode), execute in a fresh session with the plan as input, then clear the session before the next task. Mixing plan and execute in one session burns context fast and degrades both. This is the single highest-leverage workflow habit you'll learn — Pocock's course centers on it, but it's also baked into Superpowers, GSD, and feature-dev's flows.

**Vertical slices, not horizontal phases.** When decomposing a feature, default to slices that cross DB + API + UI for one user-visible behavior at a time ("tracer bullets"). AI agents default to horizontal phases — all DB work, then all API work, then all frontend work — which delays end-to-end feedback for weeks. Fight this instinct in every plan you write. If a slice can't be vertical, make it the smallest possible horizontal step and revert to vertical immediately after.

**Interview-then-execute.** Before executing a non-trivial spec, ask Claude to interview *you* using the AskUserQuestion tool until the spec is unambiguous. Then start a fresh session with the locked spec and execute. The interview surfaces decisions you didn't know you'd left ambiguous, and it's much cheaper to find them at spec time than at execute time.

## External Learning This Phase
- Jesse Vincent, "Superpowers: How I'm using coding agents in October 2025" — `blog.fsck.com/2025/10/09/superpowers/`.
- `obra/superpowers` README + the `getting-started/SKILL.md` it bootstraps.
- `gsd-build/get-shit-done` README + `docs/USER-GUIDE.md`.
- codecentric.de "GSD for Claude Code: A Deep Dive into the Workflow System".
- Garry Tan's `gstack` repo README.
- Shipyard's "Multi-agent orchestration for Claude Code in 2026".
- Addy Osmani's "The Code Agent Orchestra" — three-tier taxonomy of orchestration tools.

## Tasks

### 2.1 — Install the methodology + orchestration stack (Week 4, ~1.5h)
```
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
/plugin marketplace add jnuyens/gsd-plugin
/plugin install gsd@gsd-plugin
/plugin install feature-dev@claude-plugins-official
/plugin marketplace add garrytan/gstack
/plugin install gstack@gstack
/plugin install codex@<current-marketplace-path>  # install OpenAI Codex CLI first

export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1
brew install claude-squad   # or your package manager equivalent

/reload-plugins
```

Why claude-squad first: terminal multiplexer for multiple Claude sessions. Smallest abstraction, easiest to understand. Don't install Conductor, Vibe Kanban, or others until you've felt where claude-squad falls short.

### 2.2 — Project B: AI changelog generator, built with Agent Teams (Weeks 4–6, ~13h)
**The point of this project is using 3+ Claude sessions in parallel on real code, not the product.**

Build an AI changelog generator: user pastes a GitHub diff URL (or PR number), the service uses the Anthropic API to produce a clean user-facing changelog, optionally tagged by type (feature/fix/breaking).

**Stack: Next.js App Router + Tailwind + shadcn/ui, Postgres on Neon, deployed to Vercel.** Anthropic API call is server-side, so this is Node/TS end-to-end.

Workflow:
1. Use `/feature-dev` to scope. Before accepting the plan, have Claude interview *you* on anything ambiguous using AskUserQuestion (the interview-then-execute pattern). Lock the spec, then start a fresh session to execute (Plan/Execute/Clear).
2. Decompose into 4–5 **vertical slices** — each slice ships an end-to-end thin path. Example: slice 1 = "submit a diff URL and see a single-bullet changelog rendered." Slice 2 = "save and view changelog history." Slice 3 = "tag entries by type." Resist horizontal decomposition.
3. Open Agent Teams. Lead session coordinates. Spawn 2–3 teammates in git worktrees, each picking up a slice in parallel.
4. Teammates message each other directly when they hit shared decisions (e.g., schema changes).
5. Merge in waves. After each wave, run `/codex:adversarial-review` for a second opinion from a different model family.
6. Add auth (Clerk or NextAuth), Stripe Checkout in test mode, deploy.

Expect coordination problems. Expect to redo things. The friction is the lesson.

### 2.3 — Pick your methodology and write it down (Week 6, ~1.5h)
500 words: when do you reach for Superpowers vs GSD vs feature-dev vs gstack? Pick a primary and a secondary. Commit to the journal.

### 2.4 — claude-squad on a real refactor (Week 6, ~2h)
Open an old repo of yours. Use claude-squad to open 3 sessions targeting different concerns. Merge them. Notice what claude-squad gives you that Agent Teams doesn't (process isolation, separate tmux panes you can watch) and what it costs (no message-passing between sessions, you're the integrator).

## Phase 2 Milestone
- [ ] Project B deployed, working, used by you on a real diff.
- [ ] Built using Agent Teams with ≥2 teammates working in parallel worktrees.
- [ ] Codex adversarial review used at least once.
- [ ] Primary methodology chosen.
- [ ] Journal: methodology comparison + Agent Teams vs claude-squad reflection.

---

[← Previous: Phase 1](02-phase-1-foundations.md) | [📋 Index](README.md) | [Next: Phase 3 →](04-phase-3-agents-skills.md)
