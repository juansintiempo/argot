# ARGOT — Static Website (Astro + Tailwind)

This project is a static website built with **Astro** and **Tailwind CSS**, intentionally designed with **minimal JavaScript usage** so it can be deployed as a fully static site.

The goal is to keep the runtime simple, predictable, and compatible with static hosting environments.

---

## Tech Stack

- **Astro** – static site framework  
- **Tailwind CSS** – styling  
- Minimal JavaScript (only where strictly needed)  
- Local static assets (fonts, images, video)

---

## Project Structure

```text
/
├── public/
│   ├── fonts/
│   ├── sky.webp
│   ├── sky.mp4
│   └── favicon.svg
├── src/
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   └── index.astro
│   ├── styles/
│   │   └── global.css
│   └── model/
│       └── labels.ts
├── dist/               # generated after build
├── package.json
└── astro.config.mjs
```

---

## Development

Install dependencies:

```bash
npm install
```

Run the local development server:

```bash
npm run dev
```

The site will be available at:

```
http://localhost:4321
```

---

## Build (generate static files)

Generate the production-ready static output:

```bash
npm run build
```

This command creates a `dist/` directory containing only static files.

To preview the production build locally:

```bash
npm run preview
```

---

## Static deployment notes (important)

If you deploy the `dist/` folder manually (for example via FTP, SCP, or a basic static host), follow the steps below.

### 1. Move CSS files out of `_astro/`

After running the build, Astro generates CSS inside:

```
dist/_astro/index.[hash].css
```

Move the file to:

```
dist/index.[hash].css
```

Then update all references in the generated HTML from:

```html
/_astro/index.xxxxx.css
```

to:

```html
index.xxxxx.css
```

---

### 2. Use relative paths for static assets

When deploying statically, asset paths should be **relative**, not absolute.

Update references like:

```text
/fonts/FontName.woff2
/favicon.svg
/sky.webp
/sky.mp4
```

to:

```text
fonts/FontName.woff2
favicon.svg
sky.webp
sky.mp4
```

This applies to:
- fonts
- images
- videos
- icons
- any static media

This ensures the site works correctly regardless of domain or subfolder.

---

## Notes

- JavaScript usage is intentionally minimal to keep rendering predictable and portable.
- Video backgrounds rely on native HTML and CSS only.
- No runtime framework or hydration is required.
- Suitable for:
  - static hosting
  - CDN deployment
  - shared hosting
  - manual uploads
  - CI/CD pipelines

---

## Scripts

```json
{
  "dev": "astro dev",
  "build": "astro build",
  "preview": "astro preview",
  "astro": "astro"
}
```
