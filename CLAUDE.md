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

DISTILLED_AESTHETICS_PROMPT = """
<frontend_aesthetics>
You tend to converge toward generic, "on distribution" outputs. In frontend design, this creates what users call the "AI slop" aesthetic. Avoid this: make creative, distinctive frontends that surprise and delight. Focus on:
 
Typography: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics.
 
Color & Theme: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes. Draw from IDE themes and cultural aesthetics for inspiration.
 
Motion: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions.
 
Backgrounds: Create atmosphere and depth rather than defaulting to solid colors. Layer CSS gradients, use geometric patterns, or add contextual effects that match the overall aesthetic.
 
Avoid generic AI-generated aesthetics:
- Overused font families (Inter, Roboto, Arial, system fonts)
- Clichéd color schemes (particularly purple gradients on white backgrounds)
- Predictable layouts and component patterns
- Cookie-cutter design that lacks context-specific character
 
Interpret creatively and make unexpected choices that feel genuinely designed for the context. Vary between light and dark themes, different fonts, different aesthetics. You still tend to converge on common choices (Space Grotesk, for example) across generations. Avoid this: it is critical that you think outside the box!
</frontend_aesthetics>
"""
