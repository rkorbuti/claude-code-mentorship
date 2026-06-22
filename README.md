# Claude Code Mentorship Program

A 24-week, self-directed program for an experienced developer learning the Claude Code ecosystem, with multi-agent orchestration as the spine.

**Time:** 5–7 hrs/week
**Stack (locked):** React + Next.js/Vite frontend, Node.js (TypeScript) and Python alternating backend, Telegram for bot interfaces
**Outcome:** 6 public projects, ≥1 monetizable, real multi-agent fluency

---

## Index

### Foundation
- [Week 0 — Setup](00-setup.md)
- [Learning Resources](01-resources.md)

### Phases
- [Phase 1 — Foundations + First Subagents (Weeks 1–3)](02-phase-1-foundations.md)
- [Phase 2 — Methodology + Local Multi-Agent (Weeks 4–6)](03-phase-2-methodology.md)
- [Phase 3 — Custom Agents + Skills + Hooks + Routines (Weeks 7–9)](04-phase-3-agents-skills.md)
- [Phase 4 — Building MCP Servers (Weeks 10–13)](05-phase-4-mcp.md)
- [Phase 5 — Programmatic Multi-Agent + Project E (Weeks 14–17)](06-phase-5-multi-agent.md)
- [Phase 6 — Capstone (Weeks 18–24)](07-phase-6-capstone.md)

### Closing
- [Monetization, Communities, Maintenance, Final Note](08-monetization-and-after.md)

### Appendices (day-by-day walkthroughs)
- [Appendix A — Week 1 Day-by-Day](appendix-a-week-1-walkthrough.md)
- *(more added as we go)*

### Journal
- [How to use the journal/ folder](journal/README.md)

---

## How To Use This Repo

This is a living document. Treat it like a working repo, not a finished book.

**Read:** browse on github.com, in your IDE, or clone as an Obsidian vault. Phase files have `← Previous | 📋 Index | Next →` nav at top.

**Edit:** as you go through the program, you'll notice things to refine — better resources, sharper rubrics, your own preferences. Edit the files. Commit your changes. Use Claude Code on the repo itself; the meta is the point.

**Journal:** keep weekly entries in `journal/`. Each phase ends with a journal prompt — answer it honestly. After 24 weeks, the journal is portfolio material (talk submissions, blog posts, interview stories).

**Expansion:** Claude (in chat) will generate day-by-day walkthroughs as appendices when you start each phase. They get committed as `appendix-x-phase-N-walkthrough.md`. The phase files themselves stay stable; appendices are where the granular detail lives.

---

## Three Things to Internalize Up Front

These show up in every phase:

1. **Don't stack orchestrators.** Pick one community orchestrator in Phase 5 and go deep. The instinct to "try them all" wastes weeks and leaves you fluent in nothing.
2. **Don't reach for Managed Agents before you've hand-built orchestration.** Abstractions without foundations leave you helpless when they leak.
3. **Don't try to monetize the early projects.** Projects 1–3 are training. Treat money as a Phase 4+ concern.

---

## Stack Decisions (Locked)

**Frontend:** React via Next.js App Router for fullstack; Vite for SPAs. Tailwind + shadcn/ui. Deployed to Vercel.

**Node.js (TypeScript):** Hono or Fastify. Used for realtime work, Telegram bot endpoints (grammY), agent orchestration servers, anything I/O-heavy. Deployed to Fly.io or Railway.

**Python:** FastAPI + `uv`. Used for MCP servers (FastMCP), Agent SDK work, anything where the AI tooling ecosystem is materially denser. Telegram bots in Python use `python-telegram-bot`. Deployed to Fly.io.

**Storage:** Postgres via Neon or Supabase. Redis when there's genuine need.

**Why two backend languages:** Node owns I/O concurrency; Python owns the AI ecosystem. Use the right tool per service.

---

## Version

v6 (June 2026). Living document — edit as you go. See
[CHANGELOG.md](CHANGELOG.md) for version history.
