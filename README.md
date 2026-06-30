# ⚽ FIFA World Cup 2026 — Friends Pool & Live Bracket

A single-page web app for a friends betting pool on the **2026 FIFA World Cup**, with a **live knockout bracket** that updates automatically from real match results.

🔗 **Live site:** https://jennychristian77-ux.github.io/FIFA2026/

---

## What it does

- **Poll selections** — 10 participants, each with one or more picked countries. Picks are locked/final.
- **Live knockout bracket** — Round of 32 → Final, auto-synced from a live World Cup data feed:
  - Real results overwrite predictions and advance the actual winner.
  - **Penalty shootouts** are resolved from the feed's penalty scores.
  - Eliminated teams are dropped from all future rounds.
  - **Live matches pulse** red (● LIVE); **today's** matches show a **kick-off countdown** ("starts in 3h 42m") using each venue's real time zone.
  - Each match shows its **date + kick-off time**.
- **Still in Contention** — which participants still have at least one country alive.
- **Win Chances** — each participant's probability of their pick winning the cup, computed by simulating the remaining bracket (currently **bracket-position based**: every remaining knockout match is a 50/50 coin flip).
- **Voter initials** on each bracket team (tap on mobile to see the full name).
- **Anonymous visit counter** (views + unique visitors) at the bottom.

## How it works

- **Pure static site** — one `index.html` file, no build step, hosted on **GitHub Pages**.
- **Live results** come from the free, no-key, CORS-enabled feed at [worldcup26.ir](https://worldcup26.ir/get/games). The page polls every 2 minutes (every 30 s while a match is live).
- **Shared data** (locked votes, visit counts/log) uses **Firebase Realtime Database**.

## Project structure

| File | Purpose |
|------|---------|
| `index.html` | The entire app (HTML + CSS + JS in one file). |
| `preview-server.js` | Tiny local Node static server for previewing (`node preview-server.js` → http://localhost:8080). Not used for hosting. |

## Updating the site

It's GitHub Pages, so any push to `main` redeploys within ~1 minute:

```bash
git add -A
git commit -m "update"
git push
```

## Notes

- Match data is from a community feed, not official FIFA — generally accurate, with a graceful fallback to predictions if it's unavailable.
- The visit counter is anonymous (no names/identities, no location).
- The FIFA-weighted Win Chances model is kept in the code and can be re-enabled.

🤖 Built with [Claude Code](https://claude.com/claude-code).
