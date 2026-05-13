[📋 Index](README.md) | [Next: Learning Resources →](01-resources.md)

---

# Week 0 — Setup (~3 hours)

One-time setup before Phase 1 begins.

## Checklist

1. **Update Claude Code to v2.1.139+** (`claude --version`; update via `npm i -g @anthropic-ai/claude-code`). Versions before v2.1.139 lack Agent View, which Phase 1 uses.

2. **Install Claude Desktop** (macOS or Windows). All three tabs — Chat, Cowork, Code — get used during the program. Linux is CLI-only for now.

3. **Plan check.** Pro is fine through Phase 3. By Phase 4 you'll want Max — multi-agent work burns tokens. Rate limits doubled on May 6, 2026 and peak-hour throttling on Pro/Max was removed, so Pro stretches further than it used to.

4. **Dev environment.** Node 22+, Python 3.12+, `uv`, `pnpm`, Git.

5. **GitHub.** Create a dedicated org or account for this work. Everything goes in public repos. (This mentorship repo is the first one.)

6. **Telegram.** Create a Telegram account if you don't have one. Message `@BotFather` and create a throwaway test bot just to confirm the flow works. Real bots come in Phase 5.

7. **Anthropic Academy.** Sign up at `anthropic.skilljar.com`. Free, official, you'll come back here several times — first course is in Phase 1 Week 1.

8. **Bookmark `code.claude.com/docs`** and read the landing page end-to-end once. Subscribe to `code.claude.com/docs/en/whats-new` — features ship weekly.

9. **Initialize this repo.** If you're reading this on GitHub, you're done. If you're reading it locally, push it to a public repo (`gh repo create claude-code-mentorship --public --source=. --push`).

10. **Initialize `learning-journal/`.** Either inside this repo (public) or as a sibling private repo (if you want privacy on the journal). See [journal/README.md](journal/README.md) for what to track.

---

[📋 Index](README.md) | [Next: Learning Resources →](01-resources.md)
