# AGENTS.md — New Portfolio

Operating guide for any agent working in this workspace. Read this first.

---

## Project context

This is Kean's personal portfolio site — a rebuild of the Sep 2026 Next.js portfolio. One thesis: **PM who codes**. Work, scholarships, and freelance are lanes on one site, not separate identities.

Source of truth for *what just changed* lives in `context/` (latest dated file). Site brief, IA, and design constraints live in `brief/`. Case-study / project copy lives in `content/`. Site code will live under `app/` (or `src/`) once scaffolded.

**Not this repo:** bio/CV source of truth stays in Kean's Assistant (`about/`, dated `context/`). Do not invent CV facts here — pull from Assistant or from locked copy already in `brief/` / `content/`.

Older live codebase (reference only, do not edit as if it were this project): `../2026-09-06 Portofolio`.

---

## Quick facts (locked)

- **Name on site:** Kean · **Legal:** Kennard Mahib Bariumanto
- **Thesis:** Product manager who codes. I used to write the PRD. Now I ship the build.
- **Location:** Jakarta-born. Based in Kuta, Bali. Apple Developer Academy, Bali (Mar 2026–present).
- **Primary CTA:** Email `kennard.mahib@gmail.com` · **Secondary:** LinkedIn + CV PDF
- **Do not publish** a phone number on the public site.
- **Voice:** Direct, warm, peer-to-peer. Short sentences. Technical is fine. No “crafting experiences,” no “passionate about,” no emoji, no dummy Latin.
- **Stack:** TBD (previous site was Next.js). Update `context/` when chosen.

Full visual / IA brief: `brief/2026-09-05-portfolio-site-brief.md` (until a newer brief supersedes it).

---

## Rules

- **Ask clarifying questions before starting a complex task.** When scope, format, or intent is ambiguous, ask first rather than guessing.
- **Show your plan and steps before executing.** Lay out the approach and let Kean adjust before you run.
- **Always record material changes.** After any meaningful update (structure, design decision, scaffold, content, deploy), create a **new** dated file `context/YYYY-MM-DD-context.md`. Never silently overwrite an older context file. Open with a pointer to the previous dated file, then a `## What changed` section.
- **Read the latest `context/` file before acting** so you know the current state — not just this AGENTS.md.
- **Do not invent** palette, light mode, Inter/Geist as the system font, or a fake Mac desktop (dock, wallpaper, menu bar). Follow `brief/` when visual work starts.
- **Cite sources** when doing research.

---

## Project structure

Categorize by **what it is**, then by company/name when needed. All formats for the same thing live together.

```
AGENTS.md          ← this file (agent operating guide)
CLAUDE.md          ← mirror pointer for Claude Code
cv/<company>/      ← CVs (pdf + docx together), e.g. cv/agoda/
brief/             ← site brief, IA, design tokens, prompts
content/           ← case studies / project entries (markdown)
context/           ← dated changelogs only (YYYY-MM-DD-context.md)
public/            ← site static assets (images, favicons) once the site exists
app/ or src/       ← site code (add when scaffolded)
```

- `cv/` — Every CV cut. Subfolder per company (`cv/agoda/`). PDF and DOCX stay in the same folder. Do not split by file type across trees.
- `brief/` — Locked product/design docs.
- `content/` — Case-study / project write-ups.
- `context/` — Append-only history of what changed. Latest file by date wins.
- `public/` — Assets the live site serves (not a place to hide company CVs).

---

## Commands

Fill in once the stack is scaffolded:

- **Dev:** `python3 -m http.server 4173` from `site/` → http://127.0.0.1:4173
- **Build:** none. The site is static HTML and CSS in `site/`.
- **Deploy:** serve `site/` as the web root.

---

## Do not

- Invent a new visual system when a brief already exists in `brief/`.
- Ship a light-mode toggle unless Kean asks.
- Publish phone number or private scholarship docs.
- Treat `../2026-09-06 Portofolio` as the working tree for this project.
- Overwrite `context/` files — always add a new dated snapshot.
