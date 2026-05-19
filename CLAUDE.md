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

## Website update routine

The user maintains their CV (`cv.tex` → `cv.pdf`) outside this repo. When
they have an update they will either:

- **Describe the new item** in chat (new publication, talk, grant, etc.), and
  optionally
- **Upload a new `cv.pdf`** when the CV has changed.

For each described item, decide where it belongs using the routing table
below, update the relevant HTML files, show a summary of what changed, wait
for confirmation, then publish.

When the user uploads a new `cv.pdf`, replace the existing one at the repo
root and publish.

### Routing table

What kind of item goes where on the web:

| Type                       | publications.html | index.html               | Other                  |
|----------------------------|:-----------------:|--------------------------|------------------------|
| Published article          | ✓                 | Recent pubs (ask first)  |                        |
| Forthcoming article        | ✓                 | Recent pubs (ask first)  |                        |
| Book chapter               | ✓                 | Recent pubs (ask first)  |                        |
| Working paper / WIP        |                   | Work in progress         |                        |
| Dataset release            | ✓                 |                          |                        |
| New grant (won)            |                   | Current projects         | `projects.html`        |
| Conference / invited talk  | — (CV only)       |                          |                        |
| Award / honour             | — (CV only)       |                          |                        |
| Editorial / reviewing      | — (CV only)       |                          |                        |
| New teaching course        |                   |                          | `teaching.html`        |
| Media / outreach piece     |                   |                          | `outreach.html`        |
| New affiliation / title    |                   | About lede               | sidebar (all 5 pages)  |

For items marked "CV only" the user will only mention them so you know what
the new `cv.pdf` contains — do not add them to the website.

For ambiguous cases, ask before editing.

### "Recent publications" on index.html

`index.html` shows 4 hand-picked recent publications. When the new item is a
candidate (article / chapter / forthcoming), **ask the user**: list the
current 4 plus the candidate and let them choose which to drop (or whether
to skip Recent and only add to `publications.html`).

### Confirmation

Before publishing, show a brief summary of what will change (files touched
and a one-line per change) and wait for the user's "ok" or equivalent.
