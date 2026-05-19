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

## CV update routine

When the user provides new academic information (publication, talk, grant,
award, etc.), run this routine. **Requires Claude Code CLI on the user's Mac**
with the CV folder in scope (cv.tex is not reachable from the web sandbox).

CV source folder on the Mac:
`/Users/enriquehernandez/Dropbox/UAB/Burocracia/Bio, CV, Fotos/CV_AUTO_CLAUDE/`

Recommended invocation:
```
cd ~/path/to/enhernandez.github.io
claude --add-dir "/Users/enriquehernandez/Dropbox/UAB/Burocracia/Bio, CV, Fotos/CV_AUTO_CLAUDE"
```

Then call `/update-cv <free-text description of the change>`.

### Steps

1. **Read the cv.tex** to understand its current structure and conventions
   before editing (sections, ordering, citation style, indentation).
2. **Update the .tex** in the appropriate section(s), preserving formatting.
3. **Update the website** with items that are publicly relevant — see the
   routing table below.
4. **Show a summary** of all the changes (.tex edits + each web file touched)
   and **wait for confirmation** before compiling and publishing.
5. After confirmation:
   1. Compile the CV: `cd` to the CV folder, run `latexmk -pdf cv.tex`
      (fall back to `pdflatex cv.tex` twice + `bibtex` if needed). Fix
      errors and re-run until the build succeeds.
   2. Copy the new `cv.pdf` to the website repo root, overwriting the
      existing one.
   3. Commit on the current feature branch, fast-forward merge to `main`,
      and push (per the publishing workflow above).

### Routing table

What kind of item goes where:

| Type                       | cv.tex | publications.html | index.html               | Other                  |
|----------------------------|:------:|:-----------------:|--------------------------|------------------------|
| Published article          | ✓      | ✓                 | Recent pubs (ask first)  |                        |
| Forthcoming article        | ✓      | ✓                 | Recent pubs (ask first)  |                        |
| Book chapter               | ✓      | ✓                 | Recent pubs (ask first)  |                        |
| Working paper / WIP        | ✓      |                   | Work in progress         |                        |
| Dataset release            | ✓      | ✓                 |                          |                        |
| New grant (won)            | ✓      |                   | Current projects         | `projects.html`        |
| Conference / invited talk  | ✓      |                   |                          |                        |
| Award / honour             | ✓      |                   |                          |                        |
| Editorial / reviewing      | ✓      |                   |                          |                        |
| New teaching course        | ✓      |                   |                          | `teaching.html`        |
| Media / outreach piece     | ✓      |                   |                          | `outreach.html`        |
| New affiliation / title    | ✓      |                   | About lede               | sidebar (all 5 pages)  |

For ambiguous cases, ask the user before editing.

### "Recent publications" on index.html

`index.html` shows 4 hand-picked recent publications. When the new item is a
candidate (article / chapter / forthcoming), **ask the user**: list the
current 4 plus the candidate and let them choose which to drop (or whether
to skip Recent and only add to `publications.html`).
