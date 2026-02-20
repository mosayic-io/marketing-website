# Mobile App Marketing Website Template (Astro)

This repository is an Astro template for a mobile app website, not a deep-link redirect project.

It includes:
- A landing page with hero, features, product showcase, and app store CTA sections
- Legal page templates (`/privacy`, `/terms`)
- Support and compliance form templates:
  - `/contact`
  - `/support`
  - `/data-deletion`
- SEO metadata wiring via `astro-seo`
- Centralized site settings in `site.config.json`

## What is configurable

Update `site.config.json`:

- `app.name` and `app.tagline` for on-page branding
- `meta.title`, `meta.description`, `meta.ogImagePath` for SEO/social previews
- `forms.botpoisonPublicKey`, `forms.endpoint`, and `forms.redirectUrl` for form handling

Note: this template ships with placeholder copy and example form endpoints. Replace all placeholder legal content and form destination settings before publishing.

## Project structure

```text
├── site.config.json            # Site/app metadata + form config
├── public/
│   └── assets/                 # Images/backgrounds used by the template
└── src/
    ├── layouts/
    │   └── BaseLayout.astro    # Global HTML shell + SEO setup
    ├── pages/
    │   ├── index.astro         # Marketing landing page
    │   ├── contact.astro       # Contact form template
    │   ├── support.astro       # Support request form template
    │   ├── data-deletion.astro # Data deletion request template
    │   ├── privacy.astro       # Privacy policy template
    │   ├── terms.astro         # Terms template
    │   └── 404.astro
    └── styles/
        └── global.css
```

## Scripts

| Command | Action |
| :-- | :-- |
| `npm install` | Install dependencies |
| `npm run dev` | Run local dev server |
| `npm run build` | Build static output to `dist/` |
| `npm run preview` | Preview the production build locally |
