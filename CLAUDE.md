# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website (jelinson.com). Static site hosted on Cloudflare Pages. No build tools, package manager, or framework — plain HTML and CSS.

Cloudflare Pages serves from the `public/` subdirectory (configured via `wrangler.toml`). Files at the repo root (CLAUDE.md, README.md, wrangler.toml) are not served.

## Structure

- `public/index.html` — homepage
- `public/projects.html` — project grid (all projects)
- `public/projects/<name>.html` — detail pages (only Google and Interview Club have these so far)
- `public/styles.css` — single shared stylesheet
- `public/images/` — preview images for project cards
- `public/robots.txt` — currently blocks all crawlers (`Disallow: /`)
- `public/sitemap.xml` — lists all pages; referenced in robots.txt for when crawling is re-enabled
- `public/llms.txt` — structured summary for LLMs following the llmstxt.org convention

## When Adding a New Project

When a new project is added, update all three of these:

1. **`public/projects.html`** — add a card to the `.projects-grid`
2. **`public/sitemap.xml`** — add a `<url>` entry if the project has its own detail page
3. **`public/llms.txt`** — add a link under `## Projects` if there's a detail page, or mention it in the prose blurb for linkless projects

Projects without detail pages are described in prose in `llms.txt` under `## Projects`, not as links.
