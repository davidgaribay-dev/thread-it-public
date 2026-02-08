# Thread It

A word-chain puzzle game built with Next.js 16. Build bridges between words by finding intermediate connections. 22 levels with progressive difficulty, global leaderboards, achievements, and a mobile-first PWA experience.

**Live:** [threadit.davidgaribay.dev](https://threadit.davidgaribay.dev)

---

## How It Works

Each level gives you a **start word** and an **end word**. Type words one at a time to build a chain between them. Connections have a **strength** (strong or weak), and your performance is scored against a target **par**.

```
OCEAN → WAVE → SOUND → STRING → GUITAR
  🟢      🟢      🟡       🟢
```

The word graph is hidden — you discover connections as you go.

## Features

- **22 levels** with progressive difficulty
- **Server-side game engine** — all validation runs on the server
- **Hint system** — 2 progressive hints per level
- **Undo & restart** — experiment freely
- **Scoring** — rated against par (Genius / Perfect Thread / So Close / Nice Work / Threaded)
- **Global leaderboard** — ranked by chain length with avatars
- **12 achievements** across gameplay, streaks, and milestones
- **Daily streaks**
- **User profiles** — avatar uploads, usernames, bios
- **Share results** — emoji recap via Web Share API
- **Synthesized sound effects** — Web Audio API, no audio files
- **Haptic feedback** on mobile
- **PWA** — installable, standalone, portrait-locked
- **Dark mode default** with light mode option
- **Anonymous play** — start instantly, optionally link an email later (all progress transfers)

## Scoring

| Rating | Condition |
|---|---|
| Genius! | Under par |
| Perfect Thread! | At par |
| So Close! | 1 over par |
| Nice Work! | 2 over par |
| Threaded! | 3+ over par |

## Share Example

```
Thread It Level 3 🧵
OCEAN → 4 links → GUITAR
🟢🟢🟡🟢
Par: 4 | You: 4 | No hints
threadit.davidgaribay.dev
```

## Achievements

| Achievement | Description |
|---|---|
| 🧵 First Thread | Complete your first level |
| 🎯 Perfectionist | Complete a level at par |
| 🏆 Genius Move | Complete a level under par |
| 🚲 No Training Wheels | Complete without hints |
| 💡 Hint Master | Use both hints and still finish |
| 💪 Strong Bonds | All strong connections in a level |
| 🥇 Podium Finish | Top 3 on any leaderboard |
| 🔥 Streak Starter | 3-day streak |
| 🔥 On Fire | 7-day streak |
| ⭐ Dedicated | 14-day streak |
| 🌗 Halfway There | Complete 11 levels |
| 👑 Completionist | Complete all 22 levels |

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 16 (App Router, React 19, TypeScript 5) |
| Database | Drizzle ORM + Neon PostgreSQL (serverless) |
| Auth | Better Auth (anonymous + magic link via Resend) |
| Styling | Tailwind CSS v4, shadcn/ui, Radix UI |
| Storage | Vercel Blob (avatars) |
| Audio | Web Audio API (synthesized) |
| Haptics | Vibration API |

## Architecture Highlights

- **Server-side game logic** — the client never holds puzzle data, it's a thin rendering layer
- **Two auth paths** — anonymous guests play immediately; magic link email sign-in transfers all progress to a new account
- **Real-time feedback** — distance-to-end indicator, dead-end detection, connection strength visualization
- **Synthesized audio** — 7 distinct sounds generated with oscillators, no audio files shipped
- **OKLch color system** — perceptually uniform color space for consistent light/dark themes
- **CSS-only animations** — confetti, word slide-in, podium rise, score count-up
- **Mobile-first** — safe area insets, visual viewport API for keyboard handling, haptic patterns
- **Security hardened** — HSTS, CSP, X-Frame-Options, COOP, Permissions-Policy
