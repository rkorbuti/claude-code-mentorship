[← Previous: Phase 5](06-phase-5-multi-agent.md) | [📋 Index](README.md) | [Next: Monetization & After →](08-monetization-and-after.md)

---

# Phase 6 — Capstone: Web + Telegram, Multi-Agent Core

**Weeks 18–24 · ~40 hours**

Seven weeks to ship one product. The core differentiator must be the orchestrated agent team — not a single-agent wrapper.

## Constraints

- **Two interfaces:** Next.js web app + Telegram bot. Same backend.
- **Agent team at the core:** ≥3 specialist subagents, real orchestration.
- **Custom MCP:** plugs in your Phase 4 MCP or a new one.
- **Custom agents and skills:** uses or extends Phase 3 work.
- **Quality control:** Outcomes rubric on the user-facing AI output.
- **Monetization:** Stripe Checkout or Lemonsqueezy. Test mode at minimum; live preferred.
- **5 real users:** beta-test with 5+ humans who are not you.
- **Public:** repo open, launch post written.

## Capstone Options

Pick before Week 18. Don't drift.

### ResearchOS
Niche subscription briefings. Multi-agent team produces dailies for each subscribed niche. Discoverer + writer + summarizer + Telegram poster.
- *Differentiator:* the multi-agent decomposition is real, not theatrical.
- *Monetization:* niche briefings at $5–$15/mo sell well to power users.
- *Risk:* "AI newsletter generator" is a crowded space. Differentiator must be a specific niche the big players ignore or rubric quality.

### CodexOfMe
Personal knowledge base + journaling tool. Daily Telegram check-in, weekly multi-agent synthesis. Daily-check-in agent + retrieval agent + weekly-synthesizer + optional pattern-finder.
- *Differentiator:* you're the only customer who matters — removes a huge category of failure.
- *Monetization:* none initially; could open up later.
- *Risk:* it's tempting to ship something janky because "it's just for me."
- *Best if:* the "tune just for me" goal is the real driver.

### InboxFlow
Gmail triage SaaS. Classifier + responder + escalator + summarizer agents.
- *Differentiator:* email triage is genuinely valuable.
- *Risk:* Gmail OAuth, threading, and "what counts as urgent" are nasty edge cases. Email is a graveyard of failed startups for non-technical reasons.

### ThreadFactory
LinkedIn/X thread generator. Researcher + drafter + hook-writer + editor.
- *Differentiator:* clear paid market (creators).
- *Risk:* agents are doing thinner work — most value is in a single agent's prompts. Doesn't extend your range much beyond Project E.

### FreelancerOS
Time tracking + invoice + client status. Multi-agent team writes follow-ups and weekly client reports.
- *Risk:* commoditized space; AI agents bolt-on rather than essential.

## Suggested Weekly Cadence

| Week | Focus |
|------|-------|
| 18 | Scope lock using your methodology framework's brainstorm. Spec, wireframes, schema. |
| 19 | Backend skeleton, auth, DB. MCP integration. |
| 20 | Agent team core. Outcomes rubric. First end-to-end run. |
| 21 | Telegram bot. Web frontend skeleton. |
| 22 | Frontend polish, payment flow, e2e smoke tests. |
| 23 | 5-user beta + iterate. Use Routines (and your digest bot!) for monitoring. |
| 24 | Public launch — Product Hunt, HN, /r/SideProject, X/Twitter, LinkedIn. Launch post. |

## Phase 6 Milestone
- [ ] Deployed at a real URL.
- [ ] Telegram bot live and used.
- [ ] 5 external beta users.
- [ ] Stripe wired.
- [ ] Outcomes rubric in production.
- [ ] Launch post published.
- [ ] Journal: full 24-week retrospective.

---

[← Previous: Phase 5](06-phase-5-multi-agent.md) | [📋 Index](README.md) | [Next: Monetization & After →](08-monetization-and-after.md)
