# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Arnakke Festival** — a static HTML website for a Danish music festival (July 9-12, 2026 at Arnakke Gaard, Svinninge, Denmark).

## Development

No build system, no dependencies. The entire site is a single file: `index.html`.

**To preview locally:**
```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```

## Architecture

Single-file architecture — all HTML, CSS, and JavaScript live in `index.html`:

- **CSS**: Defined in a `<style>` block in `<head>`. All styles are inline — no external stylesheets.
- **JavaScript**: Defined in a `<script>` block at the bottom of `<body>`. Vanilla JS, no libraries.
- **Assets**: Images in `pictures/`, logos (`logo.png`, `logo-hero.png`, `logo-clean.png`) in root.

### CSS Custom Properties (color palette)
```
--paper: #F2EAD7   --ink: #1A1612    --forest: #253527
--terra: #B8351A   --gold: #C09030   --sage: #7A9175   --muted: #7A7060
```

### Fonts (Google Fonts)
- `Lora` — body text
- `Bodoni Moda` — display headings
- `Courier Prime` — UI labels/monospace

### Page Sections (in order)
Navigation → Hero → Info Strip → Tickets → About → Gallery → Program → Practical Info → English (translated) → Footer

### JavaScript Features
- Navbar scroll detection (`.scrolled` class)
- Mobile hamburger menu toggle
- Hero parallax (28% scroll speed)
- Scroll reveal via `IntersectionObserver` (`.reveal` elements get `.v` class; stagger with `.delay-1/2/3`)

### Responsive Breakpoint
Mobile layout at `720px`.
