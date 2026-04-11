---
name: add-project
description: Use when adding a new project card to the jelinson.com projects page.
---

# Add Project

Adds a new card to `projects.html`, updates `llms.txt`, and opens the result locally for feedback.

## Steps

### 1. Gather inputs (ask all at once if not provided)

- **Name** — display name for the card
- **Description** — one-line blurb for the card (`<p>` text)
- **URL** — link the card points to (external URL or local `projects/name.html`)
- **Image source** — one of:
  - `screenshot` — take a Playwright screenshot of the URL and crop/resize to 600×300
  - `file:<path>` — use an existing image file (resize to 600×300 if needed)
  - `url:<image-url>` — download an image and resize to 600×300
- **Position** — which card to place it after (e.g. "after InspectionX"), or "last"

### 2. Prepare the preview image

- Save to `images/<slug>-preview.png` (slug = lowercased name, spaces → hyphens)
- Resize to exactly **600×300 px** using Pillow:
  ```python
  from PIL import Image
  img = Image.open(src)
  # For screenshots: crop to 2:1 from top, then resize
  cropped = img.crop((0, 0, img.width, img.width // 2))
  cropped.resize((600, 300), Image.LANCZOS).save(dest)
  ```

### 3. Add the card to `projects.html`

Insert after the target card's closing `</a>` tag. Use this template:

```html
<a href="URL" class="project-card" target="_blank" rel="noopener noreferrer">
  <div class="project-image">
    <img src="images/SLUG-preview.png" alt="NAME" loading="lazy">
  </div>
  <div class="project-info">
    <h2>NAME</h2>
    <p>DESCRIPTION</p>
    <span class="project-link">HOSTNAME</span>
  </div>
</a>
```

- Omit `target="_blank" rel="noopener noreferrer"` for internal links (`projects/...`)
- Omit `<span class="project-link">` for internal links
- HOSTNAME = bare domain only (e.g. `cjmountainguiding.com`)

### 4. Update `llms.txt`

- If the project has a detail page (`projects/name.html`): add a bullet under `## Projects`
- If external/no detail page: add the project to the prose blurb in `## Projects`

### 5. Update `sitemap.xml`

- Only if a detail page (`projects/name.html`) exists — add a `<url>` entry

### 6. Open for feedback

```bash
open /Users/jelinson/Documents/projects/jelinson.com/projects.html
```
