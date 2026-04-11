# CLAUDE.md — POC Portfolio Project

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website showcasing proof-of-concept projects built by Subodh Shinde (Director of Engineering / Delivery Manager).
This is a single-file static portfolio website (`index.html`) for Subodh Shinde, deployed via GitHub Pages with a custom domain (`shindesubodh.com`, configured in `CNAME`). There is no build step, no framework, and no dependencies — the file is served directly as-is.

## Development

Open `index.html` in a browser directly, or serve it locally:

```bash
# Python (any machine with Python 3)
python -m http.server 8080
```

Then visit `http://localhost:8080`.

## Architecture

Everything lives in `index.html`:

- **CSS** — inline `<style>` block using CSS custom properties (`--ink`, `--accent`, `--surface`, etc.) for theming. Responsive breakpoint at 640px.
- **HTML structure** — five sections: `#hero`, `#about`, `#skills`, `#pocs`, `#contact`, plus a sticky `<nav>` and `<footer>`.
- **JavaScript** — at the bottom of `<body>`. All content data lives in two JS arrays at the top of the script block:
  - `SKILLS` — array of `{ group, tags[] }` objects, rendered into `#skills-grid`
  - `POCS` — array of POC card objects, rendered into `#poc-grid` with tag-based filtering
- **Render logic** — `buildSkills()`, `buildFilters()`, `renderPOCs(filter)` generate HTML from the data arrays. An `IntersectionObserver` drives the `.reveal` scroll animation.
- **Architecture diagrams** — stored in `diagrams/` and referenced by absolute GitHub raw URLs in POC link entries.

## Editing content

- **Bio / meta cards**: edit the `#about` section HTML directly.
- **Skills**: edit the `SKILLS` array in the `<script>` block.
- **POC cards**: edit the `POCS` array. A commented-out template at the end of the array shows all available fields. POC `status` accepts `"live"`, `"demo"`, or `"wip"`.
- **Contact links**: edit the `#contact` section HTML directly.

## Tech Stack
- **Frontend:** Static HTML/CSS/JS — GitHub Pages
- **Domain:** Custom domain (shindesubodh.com) via AWS Route 53
- **Editor:** VS Code with local Git workflow
- **Version Control:** Git → GitHub

## POCs Showcased
1. **AI Recipe Generator** — Flask + Netlify (frontend) + Railway (backend) + PostgreSQL + Claude API
2. **Smart Meeting Assistant** — MCP + Gmail + Google Calendar + React + Railway
3. **Windows Keep-Alive Utility** — Windows utility POC
4. **AI Test Automation Agent** — Two-stage pipeline: screenshots → manual test cases → Playwright TypeScript

## Common Tasks
- Edit portfolio pages in VS Code, commit and push to trigger GitHub Pages deploy
- Add new POC cards to the main page when new projects are built

## Conventions
- Keep code clean and minimal — this is a static site
- Each POC should have its own section/card with: title, description, tech stack, and links
- Maintain professional tone — site is used for client-facing and career positioning
