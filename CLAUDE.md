# CLAUDE.md

The marketing website for a mobile app — an Astro site whose real job is the
pages the app stores REQUIRE at submission: a support URL, a privacy policy and
a data-deletion page. The landing page is the bonus. See `README.md` for the
file-by-file map and the scripts.

## Production is not a place you run things

This site is static and touches no database of its own, but the app it belongs to has one. You may read production in a limited sense (a deployment's status, whether a secret exists) and set a secret when explicitly asked; you must NEVER run scripts, commands or SQL against the app's production database or API from here. Schema changes reach production only as migration files in the API repo, shipped by a release. If a task seems to need production data, stop and ask.

## Where things live

- `site.config.json` — the app's name, tagline, production URL, contact email,
  store links and SEO meta. Change it here, never in the pages.
- `src/styles/global.css` — ALL styling; the brand is the `--brand*` tokens at
  the top. Re-brand by changing those, not by adding colours in pages.
- `src/pages/index.astro` — the landing page. `privacy`, `terms`, `support`,
  `contact`, `data-deletion` — the store-facing pages. `404.astro` sends a
  visitor to the right store.
- `src/layouts/BaseLayout.astro` — the HTML shell and `astro-seo` wiring; it
  reads `site.config.json`'s `meta`.

## The rules

- **Every claim on the store pages must be true of the app.** Read the mobile
  app and the API next door before writing privacy, terms or data-deletion
  copy: what is collected, where it is stored, which sign-in providers exist,
  which third parties are involved, how an account is deleted (an in-app
  flow if the code has one, otherwise a request to the contact email — never a
  flow the app doesn't have). Never invent features or data collection.
- Where the code doesn't settle a claim, take the conservative option and
  mark the spot with `<!-- CHECK: what to confirm -->` so the owner can.
- Keep the existing components and structure; rewrite copy, don't rebuild
  pages. Leave the phone mockups and the store links as placeholders until the
  owner has screenshots and listings.
- No new packages, no new integrations in `astro.config.mjs`, valid frontmatter
  on every page — the build has to pass.
- Never copy a secret, a key or a connection string into the site.

## Shipping

The site deploys from its own GitHub repository through Cloudflare Pages:
pushing `main` deploys it (the repo is connected once in the Cloudflare
dashboard). Never deploy from this machine. `npm run build` must pass before
you push — it is exactly what Pages runs. A custom domain is attached to the
Pages project, also in the dashboard.
