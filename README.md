# Mobile App Marketing Website Template (Astro)

A clean, generic marketing site for a mobile app. Its real job is the pages the
app stores require — privacy policy, terms, support, and data deletion — with a
polished landing page thrown in.

It includes:

- A landing page with hero, features, how-it-works, showcase, testimonials, FAQ, and download CTA sections
- Legal page templates (`/privacy`, `/terms`)
- Email-based contact pages (no form backend needed):
  - `/contact`
  - `/support`
  - `/data-deletion`
- A 404 page that smart-redirects visitors to the right app store
- SEO metadata wiring via `astro-seo`
- Centralized site settings in `site.config.json`

## Making it yours

**1. Update `site.config.json`:**

- `app.name` and `app.tagline` — used throughout the site
- `url` — your production URL (used for canonical links and the sitemap)
- `contact.email` — where contact, support, and data deletion emails go
- `links.appStoreUrl` / `links.playStoreUrl` — your store listings
- `meta.*` — SEO title, description, and social preview image

**2. Change the brand colour.** Edit `--brand` (and `--brand-strong`) at the
top of `src/styles/global.css`. Everything else follows.

**3. Rewrite the placeholder copy.** All landing page copy in
`src/pages/index.astro` is generic on purpose — describe your actual app, or
hand the file to an AI assistant and ask it to. Swap the phone mockups in
`public/assets/` for screenshots of your app.

**4. Replace the legal placeholders.** `/privacy` and `/terms` are structured
skeletons, not legal advice. Fill in everything in `[brackets]` and make sure
each section accurately describes what your app does before publishing.

## Project structure

```text
├── site.config.json            # Site/app metadata + contact + store links
├── public/
│   ├── favicon.svg             # Replace with your own mark
│   └── assets/                 # Phone mockup images
└── src/
    ├── components/
    │   ├── SiteNav.astro       # Shared sticky navigation
    │   ├── SiteFooter.astro    # Shared footer
    │   └── StoreButtons.astro  # App Store / Google Play badges
    ├── layouts/
    │   └── BaseLayout.astro    # Global HTML shell + SEO setup
    ├── pages/
    │   ├── index.astro         # Marketing landing page
    │   ├── contact.astro       # Contact page (email-based)
    │   ├── support.astro       # Support page (email-based)
    │   ├── data-deletion.astro # Data deletion instructions (app store compliance)
    │   ├── privacy.astro       # Privacy policy skeleton
    │   ├── terms.astro         # Terms and conditions skeleton
    │   └── 404.astro           # Smart store redirect
    └── styles/
        └── global.css          # All styling — brand tokens at the top
```

## Scripts

| Command | Action |
| :-- | :-- |
| `npm install` | Install dependencies |
| `npm run dev` | Run local dev server |
| `npm run build` | Build static output to `dist/` |
| `npm run preview` | Preview the production build locally |
