[← Previous: Setup](00-setup.md) | [📋 Index](README.md) | [Next: Phase 1 →](02-phase-1-foundations.md)

---

# Learning Resources

The program assumes meaningful time on outside material. Here's the prioritized set, ordered by ROI.

## Free Official: Anthropic Academy

Hosted at `anthropic.skilljar.com`. Free, well-made by the team that builds Claude Code. Eight relevant courses, taken roughly in this order to align with the phases:

| Course | When | Why |
|--------|------|-----|
| **Claude Code 101** | Week 1 | Sets the basics. The team's mental model leaks through. |
| **Claude Code in Action** | Week 1–2 | Hands-on official course. Slash commands, MCP, agents. |
| **Sub-agents in Claude Code** | Week 6–7 | Direct prerequisite for Phase 3 and Phase 5. |
| **Agent Skills (in Claude Code)** | Week 6–7 | Frontmatter format, trigger descriptions, directory structure. |
| **Introduction to MCP** | Week 9–10 | Prerequisite for Phase 4. Three primitives, MCP Inspector. |
| **MCP: Advanced Topics** | Week 11–12 | Sampling, notifications, transports. Production MCP patterns. |
| **Building with the Claude API** | Week 13–14 | 8+ hour deep dive. Phase 5 background. |
| **AI Fluency: Framework & Foundations** | Optional | Strategic thinking. If you have time. |

Certificates are real (issued by the model provider). Worth adding to LinkedIn after each.

## Free Official: Frontend Masters

One fully-free course worth taking. No subscription required.

**Claude Code by Lydia Hallie** (`frontendmasters.com/courses/claude-code/`)
— ~1.9 hours, 16 lessons, May 2026. Taught by a member of the Claude Code
team at Anthropic (previously Head of DX at Bun, Staff DevRel at Vercel).

Covers: CLAUDE.md, Plan/Deny mode, effort levels, model selection, skills,
hooks, sub-agents, agent teams, plugins, MCP, Agent SDK, Cowork.

**When to take:** during Phase 1, alongside Claude Code in Action.
Reinforces the Anthropic Academy material with a different teacher's
framing, and previews Phase 3–5 territory weeks before you formally
get there. Previewing topics ahead of formal study aids consolidation.

**Note:** Brian Holt's MCP course on the same platform is paywalled
beyond a 10-minute preview. Skip it — the Anthropic Academy MCP
courses plus the Python FastMCP tutorial in Phase 4 cover the same
ground hands-on and for free.

---

## Paid Course (Optional, Expensive): Matt Pocock — *Claude Code for Real Engineers*

`aihero.dev` — $795, 2-week cohort. The most credible advanced practical course currently available.

**You don't need this course to do the program.** The patterns it teaches — Plan/Execute/Clear loop, vertical-slice planning, AGENTS.md, custom skills with progressive disclosure, stop hooks, the Ralph Wiggum autonomous loop, AFK mode pulling from a GitHub Issues backlog — are baked directly into this mentorship's tasks, called out where they appear.

What the course gives you that this program doesn't: live office hours with Pocock, a private Discord with other senior engineers going through the same material, the accountability of a 2-week deadline. If you want that specifically, take it. If you want the patterns, you have them here.

## Affordable Paid Options Worth Considering

Wait for $10–20 sale prices on Udemy — never pay full ($199+). Worth considering at sale prices:

- *"AI Coder: Vibe Coder to Agentic Engineer in 3 Weeks"* — short, transformation-flavored.
- *"Claude Code: Building Faster with AI, from Prototype to Prod"* — production lifecycle.

Skip:
- Scrimba's *Vibe Coding with Claude Code* — interactive but pitched at intermediates; below your level.
- Most "Build X with Claude Code in 60 minutes" YouTube-driven course offers.

## Code w/ Claude 2026 Session Recordings (Free)

The May 2026 event archive at `claude.com/code-with-claude`. Two essential watches:

1. **Live Coding with Bun and Claude Code** — Boris Cherny + Jarred Sumner doing their actual daily workflow, unfiltered. Closest thing to a master class with the creator.
2. **Cat Wu / Boris Cherny May 6 keynote** — launch announcements for Dreaming, Outcomes, Multi-agent orchestration.

Watch both in Phase 1. Re-watch the live coding session in Phase 2 once you've done some Agent Teams work yourself — you'll catch things you missed first time.

## YouTube — Specific Talks, Not Channel Blanket Subscriptions

Most "Claude Code tutorial" content is beginner-pitched. Filter aggressively.

**Watch these specific talks:**

- **"Claude Code & the evolution of agentic coding"** — Boris Cherny, AI Engineer World's Fair, 18 min. Strategic framing from the creator.
- **"Why Coding Is Solved, and What Comes Next"** — Boris Cherny at AI Ascent 2026 with Sequoia's Lauren Reeder.
- **"Agentic coding with Claude Code creator Boris Cherny"** — Bessemer Ventures discussion, includes demo.
- **AI & I podcast (Dan Shipper / Every)** — Cat Wu + Boris Cherny episode, ~90 minutes, full transcript available. Densest "how the team actually uses it" content available.
- **Lenny's Podcast** — separate Cherny and Wu episodes. Less technical but excellent product-thinking content.

**Channels (selective):**

- **IndyDevDan** (`@indydevdan`, `agenticengineer.com`) — the "evolve together" channel. 10+-year engineer betting his career on agentic engineering; methodology-focused, anti-hype, with a dedicated *Claude Code Deep Mastery* playlist. His GitHub (`disler`) has repos that overlap directly with this program: `claude-code-hooks-multi-agent-observability` (Phase 3 hooks), `single-file-agents` (Phase 5 patterns), `just-prompt` (Phase 4 MCP reference). He sells paid courses, but unlike platform-pushers he's selling *technique* not *competing tools*. Subscribe and let new videos flow into your Project E digest bot.
- **Anthropic** official channel — model launches, Boris/Cat appearances, Code w/ Claude sessions.
- **The Algorithm** — weekly project-based content; emphasizes decision-making over demonstration.
- **Edmund Yong** — practical tips, "unknown tricks" type content.
- **Latent Space** (swyx) — ecosystem and harness coverage.

## Podcasts

- **Lenny's Podcast** — most accessible Cherny/Wu interviews.
- **Latent Space** (swyx) — technical, ecosystem-deep, frequent Claude Code coverage.
- **AI & I** (Dan Shipper / Every) — long-form interviews.

## Running Blogs (Subscribe)

- **Simon Willison's blog** — filter to the `claude-code` tag. Densest single feed in the ecosystem. If you only read one, read this.
- **Anthropic engineering blog** — official deep dives.
- **Jesse Vincent's blog** (`blog.fsck.com`) — Superpowers thinking, ongoing experiments.
- **Lenny's Newsletter** — occasional but high-signal Claude Code posts.
- **Buildtolaunch** (substack) — honest plugin reviews.

## GitHub Pattern Libraries — Read Like Documentation

- **`shanraisshan/claude-code-best-practice`** — running wiki of community-tested practices, sub-tables sorted by what's currently hot. The `🔥` items are what to mimic; the `🚫👶` items are what beginners do wrong.
- **`wshobson/agents`** — large library of `.claude/agents/*.md` definitions. Read 10–20 to internalize good patterns before writing your own in Phase 3.
- **`obra/superpowers`** — actual skill source code. Reading good skills is the fastest way to write good skills.
- **`anthropics/skills`** — Anthropic's official examples, including `skill-creator`.
- **`disler/*`** — IndyDevDan's repos, especially the hooks observability one and single-file-agents.

## Advanced Patterns to Know by Name

Look these up specifically when you encounter them:

- **Ralph Wiggum loop** — autonomous pattern where the agent loops on its own backlog until done. Matt Pocock's course covers it; `shanraisshan/claude-code-best-practice` has a working repo. Named after the Simpsons character.
- **Stop hooks** — automated actions when Claude finishes a task. Boris Cherny's highest-recommended power-user pattern.
- **Subagent challenge pattern** — multiple subagents with different perspectives challenge each other before consensus. Cherny's `/code-review` uses this.
- **AGENTS.md** — cross-harness alternative/complement to CLAUDE.md. Newer convention; portable across Codex CLI, Claude Code, and others.
- **Antfooding** — Anthropic's term for their own dogfooding (employees = "ants"). Concept: you should antfood your own tools daily.

## Communities

- **Anthropic Developer Discord** — primary, linked from `claude.com`.
- **`obra/superpowers` Discord** — focused community around the framework.
- **r/ClaudeAI** and **r/ClaudeCode** — uneven, but useful for "what are people actually shipping."
- **X/Twitter follows:** `@AnthropicAI`, `@simonw`, `@obrajesse`, `@bcherny`, Cat Wu, `@indydevdan`.

---

[← Previous: Setup](00-setup.md) | [📋 Index](README.md) | [Next: Phase 1 →](02-phase-1-foundations.md)
