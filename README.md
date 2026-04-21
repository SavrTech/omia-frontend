# Omia Studio Website

Marketing, documentation, blog, support, and download site for Omia Studio.

This repository contains the public-facing static website for Omia Studio, including:

- the main product landing page
- desktop download and FAQ pages
- pricing and support pages
- the Ginni documentation site
- blog posts and migration/release guides
- HTML and text email templates used for product and build communications
- bundled desktop release assets referenced from the website

## Stack

- Static HTML pages
- Tailwind CSS via CDN
- Vanilla JavaScript for small interactions
- Google Fonts
- Google Analytics / Google Tag (`AW-17749969277`)

There is no application build pipeline in this repo. Pages are authored directly as static files.

## Site Purpose

The site positions Omia Studio as a desktop-first application builder that supports macOS, Windows, mobile, and web from a single project. It also includes migration messaging for users moving away from the retired web app experience.

Key user journeys in this repo:

- discover Omia Studio on the homepage
- download the macOS or Windows desktop app
- read Ginni API documentation
- read migration and release guides
- review pricing, support, privacy, and terms
- receive product/build lifecycle emails

## Repository Layout

### Core pages

- `index.html`: homepage and primary product messaging
- `downloads.html`: desktop download page and install FAQ
- `docs.html`: documentation entry page
- `blog.html`: blog index page
- `pricing.html`: pricing page
- `support.html`: support and FAQ page
- `privacy.html`, `terms.html`, `enterprise-pricing.html`, `enterprise-pricing-sheet.html`: policy and pricing-supporting pages

### Documentation

- `docs.html`: top-level docs page
- `docs/index.html`: duplicate docs entry for `/docs/` style routing

### Blog content

- `blog/`: canonical blog article copies plus article-specific images
- root-level article files such as `migrating-from-omia-web-to-local-omia-ide.html` and `builds-app-store-release-guide.html`: duplicated article copies with adjusted relative paths

Important convention:

- Blog articles are duplicated at the repo root and inside `blog/`.
- When editing a duplicated article, update both copies and keep relative asset paths correct.

### Assets

- `images/`: shared site images used across marketing pages and blog cards
- `blog/article_imgs/`: article-specific blog images, including cover art and tutorial screenshots
- `omialogo.png`: shared site logo kept at the repo root

### Desktop release assets

- `apps/OMIA.dmg`: macOS distributable stored in-repo
- `apps/WindowsRelease/`: Windows release bundle and extracted runtime contents

### Email templates

- `build-success-email.html` / `build-success-email.txt`
- `product-upgrade-email.html` / `product-upgrade-email.txt`
- `thank-you-email.html`

These templates are static and are meant to be filled by an external sending workflow.

## Local Development

Because the site is static, the easiest way to preview it locally is with a simple HTTP server.

### Option 1: Python

```bash
cd /path/to/omia_web
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

### Option 2: VS Code Live Server

If you use VS Code, Live Server works well for quick iteration on HTML files.

## Editing Guidelines

### Keep duplicated pages in sync

Some content exists in multiple locations for routing and static hosting convenience.

- Blog posts often exist both at the repo root and in `blog/`
- Documentation exists both as `docs.html` and `docs/index.html`

If you update one of these pages, check whether the duplicate should also be updated.

### Preserve relative paths

Path handling differs depending on where the file lives.

- root-level pages use paths like `images/foo.png` or `blog/article_imgs/bar.png`
- files inside `blog/` use paths like `../images/foo.png` or `article_imgs/bar.png`

### Shared images

All shared non-logo images should live in `images/`.

- keep `omialogo.png` at the repo root
- keep article-specific screenshots and covers in `blog/article_imgs/`

### Date-sensitive messaging

The site currently contains coordinated messaging around the Omia web app retirement on April 21, 2026.

If this messaging changes, review it across:

- homepage
- downloads
- support
- blog index
- migration and release guide articles
- email templates

## Content Areas Worth Checking Before Shipping Changes

- `index.html` for product positioning and CTA consistency
- `downloads.html` for release sizes, platform notes, and install warnings
- `docs.html` and `docs/index.html` for API accuracy
- `blog.html` for card titles, excerpts, and preview images
- duplicated blog articles for path and content parity
- email templates for tone and operational instructions

## Deployment Notes

This repository is structured like a static hosting target.

There is no framework-specific output directory, no bundler config, and no package manifest in the current repo. Changes are made directly in source HTML files, so correctness depends on careful manual updates to links, images, and duplicated pages.

## Recommended Pre-Deploy Checks

- open the edited pages in a browser
- verify relative asset paths resolve correctly
- click primary navigation and CTA links
- confirm duplicated pages stayed in sync
- confirm image references for root pages and `blog/` pages use the right relative paths
- confirm release sizes, dates, and platform notes are accurate on `downloads.html`

## License / Notices

Third-party notice information is included in `THIRD_PARTY_NOTICES.html`.