[← Previous: Phase 2](03-phase-2-methodology.md) | [📋 Index](README.md) | [Next: Phase 4 →](05-phase-4-mcp.md)

---

# Phase 3 — Custom Agents + Skills + Hooks + Routines

**Weeks 7–9 · ~20 hours**

Build three custom subagents and three skills, package both as a plugin, implement two types of hooks, and ship one Routine. Mental model: **agents are specialists with their own context; skills are procedural know-how; hooks are deterministic automation at well-defined points in the agent loop**.

## Goals
- 3 custom subagents in `.claude/agents/` you actually use.
- 3 skills in `.claude/skills/` you actually use.
- 1 PostToolUse hook and 1 Stop hook in your plugin.
- One plugin published with marketplace structure.
- One Routine running in production.

## External Learning This Phase
- Anthropic Academy: **Sub-agents in Claude Code** and **Agent Skills**.
- The `skill-creator` skill itself — invoke `skill-creator` inside Claude Code.
- mejba.me's "Top 10 Claude Code Skills, Plugins & CLIs for 2026" — the Skill Creator A/B-testing section is the most useful 10 minutes you'll spend this phase.
- Read 2–3 popular skills from `claudemarketplaces.com` and 5–10 custom agents from `wshobson/agents`.

## Tasks

### 3.1 — Three custom subagents (Week 7, ~6h)
Pick three (or substitute your own):

- `pr-reviewer` — checks a diff for your team's style rules. Model: Sonnet 4.6.
- `release-notes-writer` — turns merged PRs into user-facing release notes. Model: Haiku 4.5 (cheap, fine).
- `test-gen` — given an API route file, writes a Vitest or pytest suite. Model: Sonnet 4.6.
- `api-docs-from-route` — generates OpenAPI YAML from a route file.
- `migration-writer` — given a TypeScript interface change, writes the SQL migration.

Each gets `.claude/agents/<name>.md` with frontmatter declaring model, allowed tools, system prompt. Dogfood for a week before moving on.

### 3.2 — Three custom skills (Week 8, ~5h)
Different scope from agents. Skills are reusable procedural knowledge any agent (including main) can invoke. Pick three:

- `bug-report-to-test` — converts a bug report markdown into a failing test.
- `conventional-commits-rewriter` — rewrites a commit message to conventional commits.
- `tdd-feature-scaffold` — given a feature description, writes failing tests first, then implementation skeleton.
- `api-changelog-from-diff` — produces a changelog entry from a route diff (reusable in your capstone).
- `db-seed-from-schema` — generates seed data from a Postgres schema.

Use `skill-creator` to author. Test by triggering on real cases.

### 3.3 — Package as a plugin and publish (Week 9, ~5h)
Marketplace structure:
```
my-toolkit-plugin/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── agents/
│   ├── pr-reviewer.md
│   └── ...
└── skills/
    ├── bug-report-to-test/SKILL.md
    └── ...
```

Public GitHub repo with real README. Submit one skill or agent to the official marketplace at `claude.ai/settings/plugins/submit`.

### 3.4 — Your first Routine (Week 9, ~2h)
Pick a recurring task. Examples:
- Every Monday 9am: summarize last week's git activity across your repos and DM you on Telegram.
- Every PR merge: regenerate the README's "what's new" section using your `release-notes-writer` agent.
- Every night 11pm: scan a list of niche subreddits, summarize new content, save to a markdown file.

Use `/schedule` in Cowork or a session-start hook. Real and used, not theoretical.

### 3.5 — Stop hooks and PostToolUse hooks (Week 9, ~2h)
Hooks are deterministic automation at well-defined points in the agent loop. Two patterns to know cold:

**PostToolUse hook** — fires after Claude calls a tool. Canonical use: auto-run a linter or formatter after every edit. Add one to one of your Phase 3 skills.

**Stop hook** — fires when Claude says "I'm done." Canonical use: auto-run your test suite. If tests fail, the hook tells Claude to fix the failure and keep going, so the session doesn't actually end until tests pass. Boris Cherny calls this out as the highest-leverage power-user pattern in Claude Code — *"you can just make the model keep going until the thing is done."*

Implement one of each. Both should be in your published plugin. The stop hook example is the one you'll port forward into Phase 5 — it's the core mechanism behind the Ralph Wiggum autonomous loop you'll build there.

## Phase 3 Milestone
- [ ] 3 custom subagents in production daily use.
- [ ] 3 skills in production daily use.
- [ ] 1 PostToolUse hook and 1 Stop hook implemented and in your plugin.
- [ ] Plugin published; installable via `/plugin marketplace add yourname/my-toolkit-plugin`.
- [ ] 1 submission to the official marketplace.
- [ ] 1 Routine running for ≥7 days.
- [ ] Anthropic Academy: Sub-agents and Agent Skills courses complete.
- [ ] Journal: "What makes a subagent or skill description trigger reliably."

---

[← Previous: Phase 2](03-phase-2-methodology.md) | [📋 Index](README.md) | [Next: Phase 4 →](05-phase-4-mcp.md)
