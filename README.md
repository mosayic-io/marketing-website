# Kealy Studio Community Website Template

A website template for the Kealy Studio Community built with Astro. This template provides a marketing homepage, deep link handling for mobile apps, and automatic app store redirects.

## Features

- **Marketing Homepage** - A customizable landing page for your app
- **Deep Link Support** - Configuration files for iOS Universal Links and Android App Links
- **Smart Redirects** - Automatically redirects users to your app or the appropriate app store if the app isn't installed
- **Platform Detection** - Detects iOS, Android, or desktop and handles each appropriately

## Project Structure

```
├── public/
│   ├── .well-known/
│   │   ├── apple-app-site-association    # iOS Universal Links config
│   │   └── assetlinks.json               # Android App Links config
│   └── assets/
├── src/
│   ├── pages/
│   │   ├── index.astro                   # Marketing homepage
│   │   ├── link/index.astro              # Deep link redirect handler
│   │   └── 404.astro
│   ├── components/
│   ├── layouts/
│   └── styles/
```

## Configuration

### Deep Link Redirect Page

Update the configuration in `src/pages/link/index.astro`:

```javascript
const config = {
  appName: "Your App Name",
  appTagline: "Your App Tagline",
  description: "Your app description",
  appScheme: "yourappscheme",              // Deep link scheme (e.g., "myapp")
  androidPackage: "com.yourcompany.yourapp",
  appStoreUrl: "https://apps.apple.com/...",
  playStoreUrl: "https://play.google.com/...",
  websiteUrl: "https://yourapp.com",
};
```

### iOS Universal Links

Update `public/.well-known/apple-app-site-association` with your Apple Team ID and Bundle ID.

### Android App Links

Update `public/.well-known/assetlinks.json` with your package name and SHA256 certificate fingerprint.

## Commands

| Command           | Action                                      |
| :---------------- | :------------------------------------------ |
| `npm install`     | Install dependencies                        |
| `npm run dev`     | Start local dev server at `localhost:4321`  |
| `npm run build`   | Build production site to `./dist/`          |
| `npm run preview` | Preview build locally before deploying      |
