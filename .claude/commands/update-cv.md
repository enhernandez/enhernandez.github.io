---
description: Update CV (.tex) and website with new academic information
argument-hint: <free-text describing the new item>
---

The user is providing new academic information to add to their CV and (where
relevant) to their website. Follow the **CV update routine** documented in
`CLAUDE.md` at the repo root.

User input:
$ARGUMENTS

Reminders:

- This command requires Claude Code CLI on the user's Mac with the CV folder
  accessible (`--add-dir` to the CV_AUTO_CLAUDE Dropbox path). If you can't
  see `cv.tex`, stop and tell the user how to relaunch.
- **Read cv.tex first** to learn its conventions before editing.
- Use the routing table in `CLAUDE.md` to decide what goes on the website.
  For ambiguous categories or for "Recent publications" curation on
  `index.html`, ask the user before editing.
- Show a summary of all .tex and web edits and **wait for confirmation**
  before compiling the PDF and publishing.
- After confirmation, compile with `latexmk -pdf cv.tex`, copy the resulting
  `cv.pdf` into the website repo, then commit + fast-forward merge to `main`
  + push (no PR).
