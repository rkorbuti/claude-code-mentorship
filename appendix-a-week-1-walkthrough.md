[📋 Index](README.md) | [← Phase 1](02-phase-1-foundations.md)

---

# Appendix A — Week 1 Day-by-Day Walkthrough

The first three days of Phase 1, expanded. About 6 hours total — front-loaded into the kick-off momentum window. Pick whichever day-shape fits your week (one weekend block + two evenings, or three evenings).

## Day 1 — Tooling + First Real Read (~2.5 hours)

### Block 1: Versions and accounts (~30 min)
Since you've already dabbled in Claude Code, you mostly need to confirm version and surfaces.

```bash
claude --version              # need ≥ v2.1.139 for Agent View
npm i -g @anthropic-ai/claude-code   # if you need to update
```

Install Claude Desktop from `claude.com/download` if you don't have it. Sign in. Open it and click through all three tabs (Chat, Cowork, Code) just to see them — you don't need to use them yet. Sign up for Anthropic Academy at `anthropic.skilljar.com`. Confirm your Claude.ai plan; Pro is fine for now.

### Block 2: Anthropic Academy — Claude Code 101 (~45 min)
It's short. Take it at 1.25× if you find sections slow but don't skip. Two things to note in your journal as you go: anything that contradicts how you've been using Claude Code in your "dabble" phase, and anything that surprises you because Copilot doesn't work that way.

### Block 3: Dotfiles repo + first CLAUDE.md (~75 min)
Create a new public repo `dotfiles` on GitHub. Clone it. Add a `claude/CLAUDE.md` at the root with this starter — adapt to your taste, don't just copy verbatim:

```markdown
# Personal CLAUDE.md

## Who I am
15-year developer pivoting toward fullstack and multi-agent systems.
Strong in TS, Python, Java. Treat me as a senior peer — skip basics,
save explanation budget for non-obvious decisions.

## Default stack
- Frontend: React via Next.js (App Router) for fullstack; Vite for SPAs.
- Styling: Tailwind + shadcn/ui.
- Backend Node: Hono or Fastify (TypeScript). Not Express.
- Backend Python: FastAPI, `uv` for deps.
- DB: Postgres (Neon or Supabase).
- Deploy: Vercel for frontend, Fly.io for Python services.

## How I work
- Tests before or alongside, not after.
- Vertical slices over horizontal phases — ship end-to-end thin paths first.
- Plan in one session, execute in another. Don't pile both into one context.
- For non-trivial specs, interview me with AskUserQuestion until the spec is unambiguous.
- Don't add TODOs or stubs silently. Tell me, and I'll decide.

## Code style
- TS: named exports, strict typing, no `any`.
- Python: type hints on all function signatures.
- Comments are for *why*, not *what*.
- No `try/except Exception` swallow-all blocks. Let me see the error.

## What I'm practicing
Multi-agent orchestration. When a problem decomposes into specialists
(review, plan, execute, verify), reach for subagents via the Task tool
rather than doing it all in main context.
```

Symlink it: `ln -s ~/dotfiles/claude/CLAUDE.md ~/.claude/CLAUDE.md`. Commit, push public.

### End of Day 1
Environment confirmed, Academy 101 done, dotfiles repo live with one real CLAUDE.md. Write one paragraph in `learning-journal/day-01.md`: what surprised you in Claude Code 101.

---

## Day 2 — Calibration Refactor + AGENTS.md (~1.5–2 hours)

### Block 1: Pick a calibration repo (~10 min)
A small repo you own — ideally something between 5k and 50k lines, in TS or Python, that you know intimately but haven't touched in a few months. Not a fresh project; not a giant monorepo. The point is to have strong opinions about whether Claude's suggestions are correct.

### Block 2: Calibration refactor (~75 min)
In a fresh Claude Code session in that repo, run this sequence:

```
Read the codebase enough to understand it. Then:
1. Draft a project-level CLAUDE.md that captures the rules I'd want
   a teammate to follow when working here. Show me a draft first.
2. After I approve the CLAUDE.md, suggest three concrete improvements,
   ranked by ROI. Don't implement anything yet.
3. After I pick one, plan the change before executing.
```

This sequence is deliberate. It tests:
- Whether Claude can read your codebase well enough to write a useful CLAUDE.md (some codebases confuse it — that's a signal).
- Whether the suggestions are real or generic ("add tests" without specifying which tests is a fail).
- Whether the plan-before-execute discipline holds when you don't explicitly enforce it.

Then run the same setup in Desktop's Code tab. Note in your journal: which surface felt better for which step. Spoiler: you'll probably prefer CLI for the read-and-plan phase, Desktop for the execute phase.

### Block 3: AGENTS.md + push public (~20 min)
Add an `AGENTS.md` next to your CLAUDE.md:

```markdown
# AGENTS.md

## Stack
- Frontend: React (Next.js App Router or Vite) + Tailwind + shadcn/ui.
- Backend: Node.js with Hono/Fastify (TS), or Python with FastAPI.
- DB: Postgres (Neon/Supabase).
- Deploy: Vercel, Fly.io, Railway.

## Engineering principles
- Tests before merge, no exceptions.
- Vertical slices over horizontal phases.
- Strict typing in TS and Python.
- Comments are for "why" not "what".

## Claude-specific
Claude-specific quirks live in CLAUDE.md alongside this file.
This file is for things any agentic harness should know.
```

Symlink it too: `ln -s ~/dotfiles/claude/AGENTS.md ~/.claude/AGENTS.md`. Commit, push.

### End of Day 2
`learning-journal/day-02.md` answering the prompt *"Three things Claude Code did that surprised me, good or bad."* Be specific. "It was smart" is a failed entry. "It picked up a pattern from line 47 of file X and used it three files over without me mentioning it" is the bar.

---

## Day 3 — First Subagent + Agent View (~1.5–2 hours)

### Block 1: Browse `wshobson/agents` on GitHub (~20 min)
Read 5–10 agent definitions. Pay attention to the frontmatter (model, tools), the structure of the system prompt, and what they tell the agent *not* to do. The "not" clauses often carry more information than the positive instructions.

### Block 2: Build your code-reviewer subagent (~45 min)
Create `~/.claude/agents/code-reviewer.md` (or in your repo `.claude/agents/` — your call):

```markdown
---
name: code-reviewer
description: Reviews code changes for correctness, AGENTS.md/CLAUDE.md style adherence, and potential bugs. Use after writing a non-trivial chunk of code or before opening a PR.
model: claude-sonnet-4-6
tools: Read, Grep, Glob, Bash
---

You are a senior code reviewer. Your job is to find problems, not to compliment.

## How you work
1. Read AGENTS.md and CLAUDE.md if they exist in the repo.
2. Read the diff or files under review.
3. Output a structured review with these categories:
   - **Bugs**: things actually broken or that will break.
   - **Style violations**: things that contradict AGENTS.md/CLAUDE.md.
   - **Risk**: things that work but are fragile or expensive.
   - **Suggestions**: things you'd do differently but aren't wrong.

## What you don't do
- Don't compliment good code; assume it's the baseline.
- Don't flag pure-taste preferences as issues.
- Don't rewrite code yourself — point, don't fix. That's the main agent's job.

If the diff is clean, say so in one sentence and stop.
```

Use it twice on real code via the Task tool. Once on a diff you wrote recently and feel good about (it'll either confirm your judgment or find something — both are useful). Once on a diff from a few months ago you've since forgotten the context of. Compare its findings to what you'd say if reviewing yourself.

### Block 3: Agent View familiarity (~30 min)
Open Agent View (`/agents` slash command, or via Claude Desktop's sidebar). Run three exercises:

1. Dispatch a background session: ask it to write a CONTRIBUTING.md for the calibration repo from Day 2. Don't watch; switch back to your main session.
2. While that runs, dispatch a second background session on something unrelated — "read this repo and produce a one-paragraph elevator pitch."
3. Use `/bg` from inside a foreground session to spawn a third task.

Switch between them. Reply to one without attaching to its full transcript. The goal isn't to learn the keystrokes — it's to feel the shift in working style. You're no longer talking to *Claude*; you're managing *Claudes, plural*. That mental shift is the whole foundation for Phase 5.

### End of Day 3
Code-reviewer subagent committed to dotfiles. `learning-journal/day-03.md` answering *"When did the subagent see something I missed? When did I see something it missed?"* Both directions matter — they're how you'll calibrate trust.

---

## After Day 3

You're roughly halfway through Phase 1. Day 4–7 is lighter: finish *Claude Code in Action* on Academy (about 90 min), install the starter plugin stack (`feature-dev`, `frontend-design`, `Context7`, `claude-mem`), and start [Project A](02-phase-1-foundations.md#16--project-a-landing-page-weeks-23-8h).

One honest expectation: Day 1 will probably take 3 hours instead of 2.5. Something will go wrong — wrong Node version, Desktop crash on first launch, an Academy course that's longer than billed. Don't compress Day 2 to compensate; just accept Week 1 might run 7 hours instead of 6 and move on. The schedule normalizes by Week 2.

---

[📋 Index](README.md) | [← Phase 1](02-phase-1-foundations.md)
