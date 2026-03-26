# Kos's Hydration Pit Stop

Water drinking reminder app with a racing theme. Goal: grow into a full SaaS platform that helps the world drink more water.

## Project overview

- **Current phase**: MVP — single-file HTML app (`index.html`) with embedded CSS + JS
- **Target audience**: Anyone who forgets to drink water (starting with Kos)
- **Core identity**: Racing theme (speedometer, pit stops, race cars, checkered flags)
- **Language**: Dutch UI, English code

## Tech stack

- Vanilla HTML/CSS/JavaScript (no framework yet)
- External CDN deps: `canvas-confetti`, Google Fonts (`Orbitron`)
- Data persistence: `localStorage` (key: `kos-hydration-data`)
- Audio: Web Audio API (no external sound files)
- No build step, no bundler, no package manager

## Development

```bash
# Local dev — just open in browser, or:
python -m http.server 8000
# Then visit http://localhost:8000
```

There are no tests, linters, or CI pipelines yet.

## Code style

- 4-space indentation
- Vanilla JS — no TypeScript, no frameworks
- CSS custom properties for theming (defined in `:root`)
- Dutch for user-facing text, English for code (variable names, comments)
- Single file for now; when splitting, use ES modules (`import`/`export`)

## Design system

| Token              | Value     | Usage                    |
|--------------------|-----------|--------------------------|
| `--bg-dark`        | `#1a1a2e` | Page background          |
| `--bg-panel`       | `#16213e` | Card/panel background    |
| `--racing-red`     | `#e63946` | Alerts, accents          |
| `--racing-yellow`  | `#f1c40f` | Warnings, highlights     |
| `--racing-green`   | `#2ecc71` | Success, CTA buttons     |
| `--text-light`     | `#ffffff` | Primary text             |
| `--text-muted`     | `#a0a0b8` | Secondary text           |

Font: **Orbitron** (headings + UI), monospace fallback for timers.

## Architecture decisions

- **Single HTML file**: Keeps it simple for now. When we add a backend or routing, split into proper project structure.
- **localStorage only**: No backend, no auth. Will need a database + accounts when going SaaS.
- **Web Audio API for sounds**: No external audio files to load or host.
- **CDN dependencies**: No node_modules. When adding a bundler, vendor or install these properly.

## Key features & how they work

- **60-min reminder**: `setInterval` (1s tick) comparing `Date.now()` to stored target time — drift-resistant
- **Confetti + race car**: `canvas-confetti` library + CSS keyframe animation on emoji element
- **Speedometer**: Pure CSS `conic-gradient` gauge with positioned needle div
- **Day reset**: Automatic — compares stored date to `getToday()` on every tick and drink action

## SaaS roadmap considerations

When evolving toward SaaS, key decisions ahead:
- Frontend framework (likely React or Svelte)
- Backend + API (Node/Express or similar)
- Database (PostgreSQL)
- Auth (OAuth / magic links)
- Multi-user support + team features
- Mobile app (PWA first, then native)
- Notification system (push notifications, email reminders)

Update this file as the stack evolves.
