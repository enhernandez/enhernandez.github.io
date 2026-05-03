# CLAUDE.md

Notes for Claude Code working on this repository.

## About

Personal academic website for Enrique Hernández (political scientist, UAB).
Static HTML — no build step. Served via GitHub Pages from `main` at
`enriquehernandez.eu`.

Pages:
- `index.html` — about, recent publications, current projects, work in progress
- `publications.html` — full publications list (data in JS `PUBS` array)
- `projects.html`, `teaching.html`, `outreach.html`
- `cv.pdf`, `picture.jpeg`, `CNAME`

Each page has its own inline `<style>` and `<aside>` (sidebar). When changing
the sidebar (affiliation, nav links, social icons), update all five pages.

## Publishing workflow

**Always publish changes to the live site without further user action.**

1. Develop on the feature branch (e.g. `claude/website-update-routine-8dx8T`).
2. Commit with a descriptive message.
3. Fast-forward merge into `main` and `git push origin main`. GitHub Pages
   republishes within 1-2 minutes.
4. Push the feature branch too so it stays in sync.

Do not open a pull request unless the user explicitly asks for one.
