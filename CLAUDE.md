# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website (jelinson.com). Static site hosted on Cloudflare Pages. No build tools, package manager, or framework — plain HTML and CSS.

## Structure

- `index.html` — homepage
- `projects.html` — project grid (all projects)
- `projects/<name>.html` — detail pages (only Google and Interview Club have these so far)
- `styles.css` — single shared stylesheet
- `images/` — preview images for project cards
- `robots.txt` — currently blocks all crawlers (`Disallow: /`)
- `sitemap.xml` — lists all pages; referenced in robots.txt for when crawling is re-enabled
- `llms.txt` — structured summary for LLMs following the llmstxt.org convention

## When Adding a New Project

When a new project is added, update all three of these:

1. **`projects.html`** — add a card to the `.projects-grid`
2. **`sitemap.xml`** — add a `<url>` entry if the project has its own detail page
3. **`llms.txt`** — add a link under `## Projects` if there's a detail page, or mention it in the prose blurb for linkless projects

Projects without detail pages are described in prose in `llms.txt` under `## Projects`, not as links.
