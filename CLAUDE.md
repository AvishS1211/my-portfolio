# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file personal portfolio for Avish Shetty (Product Designer), deployed on Vercel at `https://avish-shetty.vercel.app`. The entire site lives in one file — `index.html` — with all CSS and JavaScript inline.

## Development

No build step, no package manager, no dependencies to install. The site is plain HTML/CSS/JS.

**Local preview:** Use the Claude Preview MCP server:
```
preview_start → name: "portfolio", cwd: /Users/avishshetty/my-portfolio
```
Then set viewport: `preview_resize → width: 1440, height: 900` for desktop testing.

**Deploy:** Push to `main` on GitHub — Vercel auto-deploys.

## Architecture

Everything is in `index.html` (~1500 lines). The file is structured as:

1. **`<head>`** — Meta/OG tags, Google Fonts (`Space Grotesk` + `Inter`), `@font-face` for Fungis (3 weights: Regular/Bold/Heavy `.ttf`), all inline `<style>`
2. **`<body>`** — Sections in order: `hero → about → projects → gallery → testimonials → contact → footer`
3. **`<script>`** at the bottom — all JS inline

### CSS Architecture
- CSS variables in `:root` — `--bg`, `--accent` (`#E8FF5A`), `--surface`, `--border`, `--ease`, `--radius`, etc.
- `.reveal` + `.reveal.visible` pattern for IntersectionObserver scroll animations
- `.reveal-delay-1` through `.reveal-delay-5` for staggered entrance timing
- `.vis-1` through `.vis-5` — gradient backgrounds for project card thumbnails
- `.gb-1` through `.gb-5` — CSS grid bento positions for gallery section

### Key JS Systems (all inline in `<script>`)
- **Loader** — fades out after 420ms, adds `.revealed` to hero h1 lines
- **Particle canvas** — `#hero-particles`, mouse-reactive dots in hero
- **Magnetic buttons** — `.magnetic` class elements follow cursor
- **Custom cursor** — `#cursorDot` + `#cursorRing`
- **IntersectionObserver** — adds `.visible` to `.reveal` elements on scroll
- **Gallery lightbox** — click `.gb-item` → fullscreen overlay with prev/next
- **Bell / Discord webhook** — hardcoded webhook URL, fires on bell click with visitor info

### Assets (all flat in project root)
- `Icon-vibely.svg`, `Icon-fluff.svg`, `Icon-ForeignAdmits.svg`, `Icon-Smartcue.svg`, `Icon-APMM.svg` — project card icons
- `donutready.png`, `Studio1.png`, `face.png`, `racer.png`, `envi1.png` — gallery images
- `Dheeraj_M.jpeg`, `Reet Rai.jpeg`, `sourav_mohanty.png` — testimonial avatars
- `favicon - 256.png`, `favicon - 256 - Glasses.png` — navbar logo (hover swaps to glasses version)
- `Avish_Shetty_Resume.pdf` — linked from navbar Resume item
- `FUNGIS Regular.ttf`, `FUNGIS Bold.ttf`, `FUNGIS Heavy.ttf` — custom font (loaded via `@font-face`, currently backup to Space Grotesk for headings)
- `preview-image.png` — OG/Twitter social preview image (1200×630)

## Typography
- **Headings** (`h1`, `.section-title`, `.project-name`, `.contact-email`): `Space Grotesk`, uppercase, `letter-spacing: -0.11rem`
- **Hero h1**: `font-size: 6rem`, `letter-spacing: -0.14rem`
- **Body / UI**: `Inter`, inherited from `:root`

## Notifications
Discord webhook is hardcoded in the JS. When updating, search for `DISCORD_WEBHOOK` constant near the bottom of the `<script>` block.

## OG / Social Preview
Both `og:image` and `twitter:image` must use **absolute URLs** (`https://avish-shetty.vercel.app/preview-image.png`), not relative paths — social crawlers don't resolve relative URLs.
