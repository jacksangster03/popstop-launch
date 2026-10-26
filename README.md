# POPSTOP launch page

Static landing page for **POPSTOP**, a concept for a popcorn brand with a companion phone app. The app would use the phone microphone to listen to the gaps between pops and alert the user when to stop the microwave before the popcorn burns.

Concept and course submission. **The app does not exist.** This repository contains the product plan and the launch website only; nothing here listens to audio.

## What is in the repository

| Path | Purpose |
|---|---|
| `public/` | The deployable site (`index.html`, `styles.css`), published as-is |
| `index.html`, `styles.css` | Root copies of the page |
| `PRD.md` | Planned v1 app: on-device pop detection, stop alert, privacy and safety screens (React Native with Expo, not built) |
| `DESIGN.md` | Visual system for the page and planned app screens |
| `CLAUDE.md`, `AGENTS.md`, `memory/`, `tasks/` | Working notes used while building the page with AI coding agents |
| `netlify.toml` | Netlify config: publishes `public/`, adds basic security headers, single-page fallback |

## Run locally

No build step.

```bash
cd public && python3 -m http.server 8000   # then open http://localhost:8000
```

## Status and limits

- Page only; no app, no popcorn product, no backend, no analytics.
- The planned app would not control the microwave; the user would have to stop it.
- Estimates in the plan depend on popcorn, microwave, room noise and phone placement.
