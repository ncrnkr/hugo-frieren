# Hugo Frieren

A vibrant, anime-inspired Hugo theme dedicated to *Frieren: Beyond Journey's End* (葬送のフリーレン). Designed as a colorful personal homepage with portfolio, blog, gallery, and contact sections — all wrapped in the magical aesthetic of the beloved anime series.

![Hugo](https://img.shields.io/badge/Hugo-%3E%3D0.146.0-ff4088?style=flat-square&logo=hugo)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

![Hugo Frieren Theme Screenshot](screenshot.png)

---

## Features

- **Anime-first design** — Floating sparkles, magic circles, character decorations, pastel gradients, and animated elements throughout every page
- **Bilingual (DE/EN)** — Full German and English support with a language switcher in the header. German is the default language
- **6 content sections** — Home, About, Blog, Portfolio, Gallery, Contact
- **Gallery with lightbox** — Click-to-expand image viewer with keyboard (Escape) and click-outside-to-close support
- **Responsive** — Mobile-friendly with a hamburger menu and scaled-down decorations on smaller screens
- **Scroll animations** — Intersection Observer-powered fade-in effects on cards, gallery items, and skill badges
- **Hugo asset pipeline** — CSS and JS processed through Hugo Pipes with minification, fingerprinting, and SRI hashes in production
- **Taxonomy support** — Tags and categories with dedicated listing pages
- **Pagination** — Configurable page size for blog listings
- **No external dependencies** — No frameworks, no CDNs, no build tools beyond Hugo itself

---

## Quick Start

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) v0.146.0 or later

### Installation

1. Create a new Hugo site (or use an existing one):

```bash
hugo new site my-site
cd my-site
```

2. Add the theme:

```bash
git clone https://github.com/your-username/hugo-frieren.git themes/hugo-frieren
```

3. Copy the example configuration:

```bash
cp themes/hugo-frieren/hugo.toml hugo.toml
```

4. Add your content (see [Content Structure](#content-structure) below) and start the dev server:

```bash
hugo server
```

---

## Configuration

All configuration lives in `hugo.toml`. Here are the theme-specific parameters:

```toml
baseURL = 'https://example.org/'
title = 'Frieren'
theme = 'hugo-frieren'

defaultContentLanguage = 'de'
defaultContentLanguageInSubdir = false

[params]
  author = 'Frieren'
  heroTitle = 'Frieren: Nach dem Ende der Reise'
  heroSubtitle = 'An elven mage searching for the meaning of the memories she shared with her companions.'
  frierenQuote = '"I have lived a thousand years and yet understood so little. Perhaps I am only now beginning to truly see things."'

[markup]
  [markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true  # Required for HTML entities in frontmatter

[pagination]
  pagerSize = 6

[taxonomies]
  tag = 'tags'
  category = 'categories'

[module]
  [module.hugoVersion]
    extended = true
    min = '0.146.0'
```

### Multilingual Setup

The theme supports two languages out of the box. Define menus for each language under `[languages.de.menus]` and `[languages.en.menus]`:

```toml
[languages]
  [languages.de]
    languageCode = 'de-DE'
    languageName = 'Deutsch'
    weight = 1

  [languages.en]
    languageCode = 'en-US'
    languageName = 'English'
    weight = 2
```

Each menu supports the following pages: Home (`/`), About (`/about`), Portfolio (`/portfolio`), Blog (`/blog`), Gallery (`/gallery`), Contact (`/contact`).

---

## Content Structure

```
content/
├── _index.md              # Homepage (DE)
├── _index.en.md           # Homepage (EN)
├── about/
│   ├── index.md           # About page (DE)
│   └── index.en.md        # About page (EN)
├── blog/
│   ├── _index.md          # Blog listing (DE)
│   ├── _index.en.md       # Blog listing (EN)
│   ├── my-post.md         # Blog post (DE)
│   └── my-post.en.md      # Blog post (EN)
├── portfolio/
│   ├── _index.md          # Portfolio listing (DE)
│   ├── _index.en.md       # Portfolio listing (EN)
│   ├── my-project.md      # Project (DE)
│   └── my-project.en.md   # Project (EN)
├── gallery/
│   ├── _index.md          # Gallery listing (DE)
│   ├── _index.en.md       # Gallery listing (EN)
│   ├── my-image.md        # Gallery item (DE)
│   └── my-image.en.md     # Gallery item (EN)
└── contact/
    ├── index.md           # Contact page (DE)
    └── index.en.md        # Contact page (EN)
```

Translation files use Hugo's filename-based approach: `file.md` for the default language (German), `file.en.md` for English.

### Blog Post Frontmatter

```yaml
---
title: "The Hero Party – Frieren's Companions"
date: 2026-01-15
tags: ["Characters", "Hero Party", "Friendship"]
categories: ["Anime"]
description: "A look at the legendary hero party and what makes them special."
---
```

### Portfolio Item Frontmatter

```yaml
---
title: "The Journey to the Demon King"
date: 2025-12-01
tech: ["Magic", "Swordsmanship", "Healing", "Strategy"]
description: "The epic ten-year journey of the hero party."
---
```

The `tech` array renders as colored badges on portfolio cards.

### Gallery Item Frontmatter

```yaml
---
title: "The Crystal Cave"
description: "A hidden cave filled with glowing crystals."
image: "images/gallery/crystal-cave.webp"
---
```

The `image` path is relative to the `static/` directory. Supported formats: JPG, PNG, WebP.

### About Page Frontmatter

```yaml
---
title: "About Frieren"
type: "about"
role: "Elven Mage & Hero Party Member"
skills:
  - name: "Offensive Magic"
    icon: "★"
  - name: "Defensive Magic"
    icon: "◆"
  - name: "Folk Magic"
    icon: "⚛"
social:
  - name: "Himmel"
    url: "#"
    icon: "☆"
  - name: "Fern"
    url: "#"
    icon: "F"
---
```

Skills are displayed as a grid of badges. Social links appear below the avatar in the sidebar.

### Contact Page Frontmatter

```yaml
---
title: "Contact"
type: "contact"
details:
  - icon: "✉"
    label: "Email"
    value: "frieren@example.com"
  - icon: "☎"
    label: "Phone"
    value: "Crystal #42"
  - icon: "⚑"
    label: "Location"
    value: "Somewhere on the way to Ende"
---
```

The contact form submits via standard HTML form action. To connect it to a backend, configure the form's `action` attribute in `layouts/contact/single.html`.

---

## Images

Place your images in the `static/images/` directory. The theme references the following image slots:

| Image | Used In | Purpose |
|-------|---------|---------|
| `frieren-fullbody-staff.png` | Homepage hero | Main character illustration |
| `frieren-halfbody-smile.png` | Homepage quote banner, Portfolio header | Half-body character art |
| `frieren-upperbody-staff.png` | Blog header, Homepage blog section | Upper body with staff |
| `frieren-peeking-scarf.png` | Footer, Gallery header, Section decorations | Peeking character element |
| `frieren-portrait.png` | About page avatar, Homepage gallery section | Portrait/headshot |
| `frieren-closeup.png` | 404 page, Homepage quote banner | Close-up face |
| `frieren-bottle-smile.png` | Contact page, Homepage portfolio section | Character with bottle |

Gallery images go in `static/images/gallery/` and are referenced from gallery content frontmatter.

---

## Theme Structure

```
themes/hugo-frieren/
├── archetypes/
│   └── default.md
├── assets/
│   ├── css/
│   │   └── main.css          # All theme styles (~1900 lines)
│   ├── js/
│   │   └── main.js           # Lightbox, animations, mobile menu
│   └── images/
│       └── *.svg              # Decorative SVG assets
├── i18n/
│   ├── de.toml                # German translations (22 keys)
│   └── en.toml                # English translations (22 keys)
├── layouts/
│   ├── baseof.html            # Base template
│   ├── home.html              # Homepage with all sections
│   ├── 404.html               # Error page
│   ├── page.html              # Generic page
│   ├── section.html           # Section listing
│   ├── taxonomy.html          # Tag/category listing
│   ├── term.html              # Single tag/category
│   ├── about/
│   │   └── single.html        # About page layout
│   ├── blog/
│   │   ├── list.html          # Blog listing with pagination
│   │   └── single.html        # Blog post
│   ├── portfolio/
│   │   ├── list.html          # Portfolio grid
│   │   └── single.html        # Project detail
│   ├── gallery/
│   │   └── list.html          # Gallery grid with lightbox
│   ├── contact/
│   │   └── single.html        # Contact form + info
│   └── _partials/
│       ├── head.html           # <head> meta tags
│       ├── head/
│       │   ├── css.html        # CSS pipeline
│       │   └── js.html         # JS pipeline
│       ├── header.html         # Site header + nav + lang switcher
│       ├── footer.html         # Site footer
│       ├── menu.html           # Navigation menu
│       └── scripts.html        # Script loading
└── static/
    └── favicon.ico
```

---

## Customization

### Colors

The theme uses a Frieren-inspired color palette defined as CSS custom properties in `assets/css/main.css`:

| Color | Hex | Usage |
|-------|-----|-------|
| Lavender | `#8B6BAE` | Primary, headings, accents |
| Teal | `#7EC8B0` | Secondary, buttons, highlights |
| Warm White | `#FFF9F5` | Background |
| Pink | `#E8A0B4` | Accent, hover states |
| Gold | `#FFD700` | Sparkles, decorations |
| Sky Blue | `#87CEEB` | Gradients, backgrounds |

### i18n Keys

To add or modify translations, edit the files in the site-level `i18n/` directory. Available keys include `latestPosts`, `featuredProjects`, `galleryPreview`, `viewAll`, `readMore`, `sendMessage`, `contactSubtitle`, `aboutSubtitle`, `portfolioSubtitle`, `blogSubtitle`, `gallerySubtitle`, and more.

### Decorative Elements

The homepage includes several anime-style decorations that can be customized or removed:

- **Sparkles** — Floating star characters in the hero section
- **Magic circle** — Rotating gradient circle behind the hero image
- **Quote banners** — Full-width gradient strips with Frieren quotes
- **Peeking characters** — Frieren images that peek in from section edges
- **Wave/star dividers** — Decorative section separators
- **Floating characters** — Subtly animated Frieren images at section corners

---

## Browser Support

The theme uses modern CSS and JavaScript features:

- CSS Grid and Flexbox
- CSS custom properties
- `conic-gradient` (for magic circle)
- Intersection Observer API
- ES6 `querySelectorAll`, `forEach`, arrow-free syntax for broad compatibility

Works in all modern browsers (Chrome, Firefox, Safari, Edge).

---

## Credits

- Theme inspired by [Frieren: Beyond Journey's End](https://frieren-anime.jp/) (葬送のフリーレン)
- Built with [Hugo](https://gohugo.io/)
- Character artwork belongs to their respective copyright holders

---

## License

MIT License. See [LICENSE](LICENSE) for details.
