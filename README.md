# Developer Notes

Personal reference notes for setting up a web development environment, scaffolding websites with **Astro, Vite + React, and Next.js**, and working with Git/GitHub. The classes, tags, colors, and fonts used in the examples below are illustrative — swap them for any generic CSS classes, framework, or design system.

## Index

- [1. Required Programs](#1-required-programs)
- [2. VS Code Extensions](#2-vs-code-extensions)
- [3. VS Code Keyboard Shortcuts](#3-vs-code-keyboard-shortcuts)
  - [3.1 General](#31-general)
  - [3.2 Editing](#32-editing)
  - [3.3 Navigation](#33-navigation)
- [4. Shared Website Setup](#4-shared-website-setup)
  - [4.1 Tailwind CSS Setup](#41-tailwind-css-setup)
  - [4.2 Tailwind Theme & Custom Fonts](#42-tailwind-theme--custom-fonts)
  - [4.3 Open Graph & Metadata](#43-open-graph--metadata)
  - [4.4 `robots.txt`](#44-robotstxt)
  - [4.5 Sitemap Integration](#45-sitemap-integration)
  - [4.6 404 / Not Found Page](#46-404--not-found-page)
  - [4.7 Prettier Setup](#47-prettier-setup)
  - [4.8 Windows PowerShell Execution Policy / npm Recovery](#48-windows-powershell-execution-policy--npm-recovery)
  - [4.9 Development Server](#49-development-server)
  - [4.10 `.env` Example](#410-env-example)
  - [4.11 `.gitignore` Example](#411-gitignore-example)
- [5. Astro](#5-astro)
  - [5.1 Project Setup](#51-project-setup)
  - [5.2 Install Dependencies](#52-install-dependencies)
  - [5.3 Routing & Client-Side Navigation](#53-routing--client-side-navigation)
  - [5.4 Main Layout Example](#54-main-layout-example)
  - [5.5 Project Structure & Architecture](#55-project-structure--architecture)
- [6. Vite](#6-vite)
  - [6.1 Scaffolding a New Project](#61-scaffolding-a-new-project)
  - [6.2 Install Dependencies](#62-install-dependencies)
  - [6.3 `vite.config.ts` Reference](#63-viteconfigts-reference)
  - [6.4 Routing & Layouts (React Router DOM)](#64-routing--layouts-react-router-dom)
  - [6.5 Layout Route with `Outlet`](#65-layout-route-with-outlet)
  - [6.6 Project Structure & Architecture](#66-project-structure--architecture)
- [7. Next.js](#7-nextjs)
  - [7.1 Create a New Project](#71-create-a-new-project)
  - [7.2 Install Dependencies](#72-install-dependencies)
  - [7.3 `next.config.ts` Reference](#73-nextconfigts-reference)
  - [7.4 Routing & Layouts (App Router)](#74-routing--layouts-app-router)
  - [7.5 Root Layout](#75-root-layout)
  - [7.6 Server and Client Components](#76-server-and-client-components)
  - [7.7 Production Build](#77-production-build)
  - [7.8 Project Structure & Architecture](#78-project-structure--architecture)
- [8. Linux Server & Docker Deployment](#8-linux-server--docker-deployment)
  - [8.1 Connect with Bitvise SSH Client](#81-connect-with-bitvise-ssh-client)
  - [8.2 Basic Linux Setup](#82-basic-linux-setup)
  - [8.3 Install Only the Basic Utilities Needed Here](#83-install-only-the-basic-utilities-needed-here)
  - [8.4 Node.js: Required by the Projects](#84-nodejs-required-by-the-projects)
  - [8.5 Install Docker and Docker Compose](#85-install-docker-and-docker-compose)
  - [8.6 Allow Your User to Run Docker Without `sudo`](#86-allow-your-user-to-run-docker-without-sudo)
  - [8.7 First Docker Test](#87-first-docker-test)
  - [8.8 Basic Linux Commands for Deployments](#88-basic-linux-commands-for-deployments)
  - [8.9 Firewall Basics with UFW](#89-firewall-basics-with-ufw)
  - [8.10 Create the Server Structure](#810-create-the-server-structure)
  - [8.11 Vite + React Dockerfile](#811-vite--react-dockerfile)
  - [8.12 Next.js Dockerfile](#812-nextjs-dockerfile)
  - [8.13 `.dockerignore`](#813-dockerignore)
  - [8.14 Traefik + Cloudflare Origin Certificate + Three Websites](#814-traefik--cloudflare-origin-certificate--three-websites)
  - [8.15 Understand the Important Traefik Lines](#815-understand-the-important-traefik-lines)
  - [8.16 Why the Three Websites Are Different](#816-why-the-three-websites-are-different)
  - [8.17 DNS Setup](#817-dns-setup)
  - [8.18 First Deployment](#818-first-deployment)
  - [8.19 Useful Deployment Commands](#819-useful-deployment-commands)
  - [8.20 Update Only One Website](#820-update-only-one-website)
  - [8.21 Docker Disk Cleanup](#821-docker-disk-cleanup)
  - [8.22 Fail2ban Basic Configuration](#822-fail2ban-basic-configuration)
  - [8.23 Basic SSH Hardening](#823-basic-ssh-hardening)
  - [8.24 Troubleshooting](#824-troubleshooting)
  - [8.25 Final Production Checklist](#825-final-production-checklist)
- [9. Deployment](#9-deployment)
  - [9.1 Google Search Console](#91-google-search-console)
  - [9.2 Cloudflare Pages](#92-cloudflare-pages)
  - [9.3 Cloudflare Domains & Rules](#93-cloudflare-domains--rules)
  - [9.4 Vite + Next.js + Cloudflare Protection & Free SSL](#94-vite--nextjs--cloudflare-protection--free-ssl)
  - [9.5 Pointing the Client's Domain (Astro)](#95-pointing-the-clients-domain-astro)
  - [9.6 Pointing the Client's Domain (Vite + Next.js)](#96-pointing-the-clients-domain-vite--nextjs)
- [10. Git and GitHub](#10-git-and-github)
  - [10.1 Initial Setup (First-Time Project)](#101-initial-setup-first-time-project)
  - [10.2 Daily Workflow](#102-daily-workflow)
  - [10.3 Branching](#103-branching)
  - [10.4 Other Useful Commands](#104-other-useful-commands)
  - [10.5 Undoing Things: `reset`, `restore`, `revert`](#105-undoing-things-reset-restore-revert)
  - [10.6 `rebase` vs `merge`](#106-rebase-vs-merge)
  - [10.7 Force Push and Other Dangerous Commands](#107-force-push-and-other-dangerous-commands)
  - [10.8 Real Branching Flow: Feature Branch → Main](#108-real-branching-flow-feature-branch--main)
- [11. Common HTTP Status Codes](#11-common-http-status-codes)
## 1. Required Programs

| Program | Purpose | Link |
|---|---|---|
| Node.js | Required JavaScript runtime for local development, builds, Astro, Vite and Next.js | [nodejs.org/en/download](https://nodejs.org/en/download) |
| pnpm | Fast, disk-efficient package manager | [pnpm.io/installation](https://pnpm.io/installation) |

Install Node.js first, then install pnpm. Node.js is required for this development setup.

---

## 2. VS Code Extensions

| Extension | Purpose |
|---|---|
| Container Tools | Manage and inspect containers from VS Code |
| Dev Containers | Develop inside a containerized environment |
| Error Lens | Inline error/warning highlighting |
| ESLint | JavaScript/TypeScript linting |
| Gemini Code Assistant | AI coding assistance |
| GitLens | Enhanced Git history and blame info |
| HTML CSS Support | Autocomplete for class/id names in HTML/CSS |
| HTML Play | Quick HTML preview/playground |
| Icons - Maintained | File icon theme |
| Live Preview | Preview HTML pages inside VS Code |
| Live Server | Local dev server with live reload |
| Prettier - Code Formatter | Automatic code formatting |
| Pretty TypeScript Errors | Easier to read TypeScript error messages |
| Prisma | Language support for Prisma schema files |
| Python | Python language support |
| RapidAPI | Test and explore APIs from VS Code |
| Supabase | Supabase integration and helpers |
| Tailwind CSS IntelliSense | Autocomplete and linting for Tailwind classes |
| XML | XML language support |

---

## 3. VS Code Keyboard Shortcuts

### 3.1 General

| Shortcut (Win/Linux) | Shortcut (Mac) | Action |
|---|---|---|
| `Ctrl+P` | `Cmd+P` | Quick open file |
| `Ctrl+Shift+P` | `Cmd+Shift+P` | Command palette |
| `Ctrl+,` | `Cmd+,` | Open settings |
| `Ctrl+\`` | `Cmd+\`` | Toggle terminal |
| `Ctrl+B` | `Cmd+B` | Toggle sidebar |
| `Ctrl+Shift+E` | `Cmd+Shift+E` | Focus Explorer |
| `Ctrl+Shift+X` | `Cmd+Shift+X` | Open Extensions panel |
| `Ctrl+Shift+G` | `Cmd+Shift+G` | Open Source Control panel |
| `Ctrl+K Ctrl+S` | `Cmd+K Cmd+S` | Open Keyboard Shortcuts |

### 3.2 Editing

| Shortcut (Win/Linux) | Shortcut (Mac) | Action |
|---|---|---|
| `Ctrl+D` | `Cmd+D` | Select next occurrence of current word |
| `Ctrl+Shift+L` | `Cmd+Shift+L` | Select all occurrences of current word |
| `Alt+Click` | `Option+Click` | Add cursor |
| `Ctrl+Alt+Down/Up` | `Cmd+Option+Down/Up` | Add cursor below/above |
| `Shift+Alt+Down/Up` | `Shift+Option+Down/Up` | Copy line down/up |
| `Alt+Down/Up` | `Option+Down/Up` | Move line down/up |
| `Ctrl+/` | `Cmd+/` | Toggle line comment |
| `Shift+Alt+F` | `Shift+Option+F` | Format document |
| `Ctrl+Space` | `Ctrl+Space` | Trigger suggestion/autocomplete |
| `F2` | `F2` | Rename symbol |
| `Ctrl+.` | `Cmd+.` | Quick fix |

### 3.3 Navigation

| Shortcut (Win/Linux) | Shortcut (Mac) | Action |
|---|---|---|
| `Ctrl+Tab` | `Cmd+Tab` | Switch between open tabs |
| `Ctrl+G` | `Cmd+G` | Go to line |
| `F12` | `F12` | Go to definition |
| `Alt+F12` | `Option+F12` | Peek definition |
| `Ctrl+-` | `Cmd+-` | Go back |
| `Ctrl+Shift+-` | `Cmd+Shift+-` | Go forward |
| `Ctrl+Shift+O` | `Cmd+Shift+O` | Go to symbol in file |

---

## 4. Shared Website Setup

These steps are identical in spirit across **Astro**, **Vite** and **Next.js** — Tailwind, Open Graph, `robots.txt`, sitemaps, the 404 page, Prettier, and the Windows/npm recovery steps. Each subsection gives the shared idea once and then a short **Astro / Vite / Next.js** breakdown for whatever changes between them. Framework-specific scaffolding, routing and project structure live in their own sections: [5. Astro](#5-astro), [6. Vite](#6-vite), [7. Next.js](#7-nextjs).

### 4.1 Tailwind CSS Setup

All three projects use Tailwind CSS v4. The idea is the same everywhere: install the package, register it as a build plugin, and import it once from a global stylesheet.

```bash
pnpm add tailwindcss @tailwindcss/vite
```

```css
@import "tailwindcss";
```

**Astro** — register the plugin inside the Vite section of `astro.config.mjs`:

```js
import { defineConfig } from 'astro/config';
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  vite: {
    plugins: [tailwindcss()],
  },
});
```

**Vite** — register the plugin directly in `vite.config.ts` (see [6.3](#63-viteconfigts-reference) for the full file):

```typescript
import { defineConfig } from 'vite';
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [tailwindcss()],
});
```

**Next.js** — `pnpm create next-app@latest` asks `Tailwind CSS: Yes` and wires everything (PostCSS config included) automatically. Nothing else to install; just start writing Tailwind classes and import the global stylesheet from `app/layout.tsx`.

### 4.2 Tailwind Theme & Custom Fonts

The same `@theme` pattern works in all three projects to register custom fonts as Tailwind utilities:

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
@import "tailwindcss";

@theme {
  --font-sans: 'Poppins', system-ui, sans-serif;
  --font-display: 'Space Grotesk', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', monospace;
}
```

This exposes `font-sans`, `font-display` and `font-mono` as Tailwind class names, usable directly in markup in any of the three frameworks.

**Astro** — additionally ships smooth page-crossfade CSS tied to its built-in client-side router (see [5.3](#53-routing--client-side-navigation)):

```css
::view-transition-old(root) {
  animation: fade-out 0.25s ease forwards;
}
::view-transition-new(root) {
  animation: fade-in 0.25s ease forwards;
}
@keyframes fade-out { from { opacity: 1; } to { opacity: 0; } }
@keyframes fade-in { from { opacity: 0; } to { opacity: 1; } }
```

**Vite / Next.js** — the same crossfade can be added with the browser-native View Transitions API (`document.startViewTransition(...)`) around a route change; it's optional and not wired in by default the way Astro's `ClientRouter` wires it in.

### 4.3 Open Graph & Metadata

Open Graph controls how a page looks when shared on social media, WhatsApp, Slack, etc.

| Meta tag | Purpose |
|---|---|
| `og:title` | Title of the preview card |
| `og:description` | Short description (~155 characters max) |
| `og:image` | Preview image — minimum 1200×630px, publicly accessible via an absolute URL |
| `og:url` | Canonical URL of the page |
| `og:type` | `website` for regular pages, `article` for blog posts |

Preview tools: [opengraph.xyz](https://www.opengraph.xyz/) and Meta's official sharing debugger.

**Astro / Vite** — tags are written by hand as plain `<meta>` elements:

```html
<meta name="description" content="Business description" />
<meta property="og:title" content="Business title" />
<meta property="og:description" content="Business description" />
<meta property="og:image" content="https://mysite.com/banner.png" />
<meta property="og:url" content="https://mysite.com" />
<meta property="og:type" content="website" />
```

In Astro this lives in the `<head>` of `src/layouts/Layout.astro` (see [5.4](#54-main-layout-example)); in Vite it lives in `index.html`.

**Next.js** — use the Metadata API instead of hand-written tags (see [7.5](#75-root-layout) for the full example):

```tsx
export const metadata = {
  title: 'Business title',
  description: 'Business description',
  openGraph: {
    title: 'Business title',
    description: 'Business description',
    url: 'https://mysite.com',
    images: [{ url: 'https://mysite.com/banner.png', width: 1200, height: 630 }],
    type: 'website',
  },
}
```

### 4.4 `robots.txt`

`robots.txt` is framework-independent — it's a static file tells search engine crawlers what they can access and points them to the sitemap. The final URL is always `https://mysite.com/robots.txt`.

**Normal production site:**

```text
User-agent: *
Allow: /

Sitemap: https://mysite.com/sitemap.xml
```

**Staging / private site:**

```text
User-agent: *
Disallow: /
```

**Astro / Vite / Next.js** — all three place the same static file at:

```text
public/robots.txt
```

Next.js can alternatively generate it dynamically from `app/robots.ts` instead of a static file, if the rules need to depend on environment variables.

### 4.5 Sitemap Integration

A sitemap is useful for SEO and should be submitted to Google Search Console (see [9.1](#91-google-search-console)). The mechanism differs per framework:

**Astro:**

```bash
pnpm astro add sitemap
```

```js
// astro.config.mjs
import { defineConfig } from 'astro/config';
import sitemap from '@astrojs/sitemap';

export default defineConfig({
  site: 'https://mysite.com', // real client URL
  integrations: [sitemap()],
});
```

**Vite:**

```bash
pnpm add -D vite-plugin-sitemap
```

```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import Sitemap from 'vite-plugin-sitemap';

export default defineConfig({
  plugins: [
    react(),
    Sitemap({ hostname: 'https://mysite.com' }),
  ],
});
```

**Next.js** — create `app/sitemap.ts`:

```typescript
import type { MetadataRoute } from 'next'

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    { url: 'https://mysite.com', lastModified: new Date() },
  ]
}
```

### 4.6 404 / Not Found Page

Every project needs a not-found page; the implementation differs per framework.

**Astro** — file-based, drop a page at `src/pages/404.astro`:

```astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout title="Page not found">
  <section class="flex flex-col items-center justify-center min-h-[60vh] gap-4">
    <h1 class="text-6xl font-bold">404</h1>
    <p class="text-xl">Page not found</p>
    <a href="/" class="underline">Back to home</a>
  </section>
</Layout>
```

**Vite** — with React Router, a catch-all route is enough (see [6.4](#64-routing--layouts-react-router-dom)):

```tsx
<Route path="*" element={<NotFound />} />
```

**Next.js** — file-based, drop a file at `app/not-found.tsx`:

```tsx
export default function NotFound() {
  return (
    <main className="flex min-h-[60vh] flex-col items-center justify-center gap-4 text-center">
      <h1 className="text-6xl font-bold">404</h1>
      <p className="text-xl">Page not found</p>
      <a href="/" className="underline">Back to home</a>
    </main>
  )
}
```

> The `class`/`className` names and layout structure above are just an example — swap them for any generic CSS classes or framework.

### 4.7 Prettier Setup

Install Prettier and add the standard scripts to `package.json`:

```bash
pnpm add -D prettier
```

```json
"format": "prettier --write .",
"format:check": "prettier --check ."
```

```bash
pnpm install
```

**Astro** — needs one extra plugin so Prettier understands `.astro` files:

```bash
pnpm add -D prettier-plugin-astro
```

**Vite / Next.js** — no extra plugin needed for plain `.tsx`/`.ts` files.

### 4.8 Windows PowerShell Execution Policy / npm Recovery

This applies the same way regardless of framework.

If PowerShell blocks package scripts (`pnpm create astro@latest`, `pnpm create vite@latest`, `pnpm create next-app@latest`, `pnpm install`, etc.), open a new terminal in VS Code and run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

Confirm with `Y` and re-run the command.

> During project setup, the CLI may ask about ESLint or other tools — press Enter to confirm the default selection and continue.

If a project was accidentally installed with `npm` and needs to be reset back to `pnpm`:

```bash
rm -rf node_modules package-lock.json
pnpm install
```

### 4.9 Development Server

The command is the same in all three projects:

```bash
pnpm dev
```

Default local URLs differ per framework — always trust whatever the terminal actually prints:

```text
Astro    → http://localhost:4321
Vite     → http://localhost:5173
Next.js  → http://localhost:3000
```

### 4.10 `.env` Example

Environment variables keep secrets (API keys, database URLs, tokens) out of the codebase. The `.env` file is never committed — it's excluded via [`.gitignore`](#411-gitignore-example) — only `.env.example` (with placeholder values, no real secrets) gets committed as a reference for other developers.

**Astro** — variables must be prefixed with `PUBLIC_` to be exposed to client-side code; anything without that prefix is only available server-side:

```bash
# .env
PUBLIC_SITE_URL=https://mysite.com
PUBLIC_GA_ID=G-XXXXXXXXXX

# Server-only (not exposed to the browser)
DATABASE_URL=postgresql://user:password@localhost:5432/mydb
RESEND_API_KEY=re_xxxxxxxxxxxxxxxxxxxx
```

Accessed via `import.meta.env.PUBLIC_SITE_URL` (or `import.meta.env.DATABASE_URL` server-side, e.g. inside an API route or `.astro` frontmatter).

**Vite** — same `PUBLIC`-style convention but with the `VITE_` prefix; anything without it is stripped from the client bundle entirely for security:

```bash
# .env
VITE_API_URL=https://api.mysite.com
VITE_GA_ID=G-XXXXXXXXXX
```

Accessed via `import.meta.env.VITE_API_URL`. Since Vite/React apps are fully client-side, never put real secrets (DB passwords, private API keys) here — anything with the `VITE_` prefix ends up in the shipped JS bundle and is visible to anyone.

**Next.js** — the `NEXT_PUBLIC_` prefix exposes a variable to the browser; without it, the variable only works in Server Components, API routes, and `next.config.ts`:

```bash
# .env.local
NEXT_PUBLIC_SITE_URL=https://mysite.com
NEXT_PUBLIC_GA_ID=G-XXXXXXXXXX

# Server-only (not exposed to the browser)
DATABASE_URL=postgresql://user:password@localhost:5432/mydb
NEXTAUTH_SECRET=replace-with-a-random-string
RESEND_API_KEY=re_xxxxxxxxxxxxxxxxxxxx
```

Accessed via `process.env.NEXT_PUBLIC_SITE_URL` (client or server) or `process.env.DATABASE_URL` (server-only). Next.js conventionally uses `.env.local` for local secrets — it's ignored by Git by default in the standard Next.js `.gitignore`, on top of `.env*`.

> These variable names, prefixes and values are illustrative — swap them for whatever real services and keys the project actually needs.

### 4.11 `.gitignore` Example

A single generic `.gitignore` covers Astro, Vite and Next.js, since the underlying tooling (Node.js, pnpm, TypeScript, editors, OS files) is the same across all three:

```gitignore
# Dependencies
node_modules/
.pnpm-store/

# Build output
dist/
build/
.output/
.next/
out/

# Environment variables
.env
.env.local
.env.*.local

# Framework-specific caches
.astro/
.vite/
.turbo/

# Logs
npm-debug.log*
pnpm-debug.log*
yarn-debug.log*
yarn-error.log*
*.log

# Editor / IDE
.vscode/*
!.vscode/extensions.json
.idea/

# OS files
.DS_Store
Thumbs.db

# TypeScript
*.tsbuildinfo

# Testing / coverage
coverage/

# Misc
*.local
```

> `.env` is deliberately ignored while `.env.example` is not — commit `.env.example` with placeholder values so the pattern from [4.10](#410-env-example) is documented for anyone who clones the repo. `!.vscode/extensions.json` is a negation pattern: it re-includes that one file even though `.vscode/*` ignores the folder, which is handy for sharing the extension list from [2. VS Code Extensions](#2-vs-code-extensions) with the team.

---

## 5. Astro

> **Deployment note:** Astro is included as a development reference, but it is not part of the Docker/server setup in section 8. Astro sites are deployed directly to Cloudflare Pages (see [9.2](#92-cloudflare-pages)).

### 5.1 Project Setup

```bash
pnpm create astro@latest
```

The Tailwind CSS setup that follows scaffolding is covered in [4.1](#41-tailwind-css-setup); sitemap in [4.5](#45-sitemap-integration).

### 5.2 Install Dependencies

The Astro CLI installs dependencies as part of scaffolding. If they ever need reinstalling (e.g. after cloning the repo):

```bash
pnpm install
```

### 5.3 Routing & Client-Side Navigation

Astro uses **file-based routing**: every file in `src/pages/` becomes a route (see [5.5](#55-project-structure--architecture) for the full mapping).

Astro's built-in `ClientRouter` enables View Transitions for smooth navigation between pages without full reloads — no router library needed. It's imported once in the shared layout (see [5.4](#54-main-layout-example)) and paired with the CSS crossfade from [4.2](#42-tailwind-theme--custom-fonts).

```astro
---
import { ClientRouter } from "astro:transitions";
---
<head>
  <ClientRouter />
</head>
```

### 5.4 Main Layout Example

`src/layouts/Layout.astro` is the shared HTML shell: head, meta tags, Open Graph (see [4.3](#43-open-graph--metadata)), `<Navbar />` / `<Footer />`, and `<slot />` for page content — the Astro equivalent of Vite's layout route ([6.5](#65-layout-route-with-outlet)) or Next.js's root layout ([7.5](#75-root-layout)).

```astro
---
import "../styles/global.css";
import { ClientRouter } from "astro:transitions";
import Navbar from "../components/Navbar.astro";
import Footer from "../components/Footer.astro";
---

<!doctype html>
<html lang="en" class="scroll-smooth">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <title>Business title</title>
    <meta name="description" content="Business description" />

    <!-- Open Graph -->
    <meta property="og:title" content="Business title" />
    <meta property="og:description" content="Business description" />
    <meta property="og:image" content="https://mysite.com/banner.png" />
    <meta property="og:url" content="https://mysite.com" />
    <meta property="og:type" content="website" />

    <ClientRouter />
  </head>
  <body class="min-h-screen flex flex-col bg-white text-gray-900 font-sans">
    <Navbar />
    <main class="flex-1">
      <slot />
    </main>
    <Footer />
  </body>
</html>
```

### 5.5 Project Structure & Architecture

```
/
├── public/
│   ├── favicon.svg
│   ├── icon.png
│   ├── images/
│   └── robots.txt
├── src/
│   ├── components/
│   │   ├── Hero.astro
│   │   ├── Navbar.astro
│   │   └── Footer.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   ├── index.astro
│   │   ├── terms-of-service.astro
│   │   ├── privacy-policy.astro
│   │   ├── contact.astro
│   │   └── 404.astro
│   └── styles/
│       └── global.css
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

**`public/`** — Static assets served as-is, without processing. Anything here is copied directly to the final build output at the same path (favicon, images, `robots.txt` — see [4.4](#44-robotstxt)).

**`src/components/`** — Reusable UI pieces used across multiple pages (e.g. `Hero.astro`, `Navbar.astro`, `Footer.astro`). Each component encapsulates its own markup, styles, and logic.

**`src/layouts/`** — Page wrappers that define the shared HTML shell (see [5.4](#54-main-layout-example)). Most projects only need one `Layout.astro`, but additional layouts can be added for different page types (e.g. a blog post layout).

**`src/pages/`** — File-based routing: each file becomes a route.

- `index.astro` → homepage (`/`)
- `terms-of-service.astro` → `/terms-of-service`
- `privacy-policy.astro` → `/privacy-policy`
- `contact.astro` → `/contact`
- `404.astro` → custom not-found page (see [4.6](#46-404--not-found-page))

**`src/styles/`** — Global stylesheets. `global.css` is where Tailwind is imported (see [4.1](#41-tailwind-css-setup)) and where fonts/theme tokens live (see [4.2](#42-tailwind-theme--custom-fonts)).

---

## 6. Vite

### 6.1 Scaffolding a New Project

```bash
pnpm create vite@latest project-name --template react-ts
cd project-name
```

### 6.2 Install Dependencies

```bash
pnpm install
```

The Tailwind CSS setup that follows is covered in [4.1](#41-tailwind-css-setup); sitemap in [4.5](#45-sitemap-integration).

### 6.3 `vite.config.ts` Reference

Basic version (React + Tailwind):

```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [
    react(),
    tailwindcss()
  ]
});
```

Extended version, adding the [React Compiler](https://react.dev/learn/react-compiler) via a Babel plugin:

```typescript
import { defineConfig } from 'vite'
import react, { reactCompilerPreset } from '@vitejs/plugin-react'
import babel from '@rolldown/plugin-babel'
import tailwindcss from '@tailwindcss/vite'

// https://vite.dev/config/
export default defineConfig({
  plugins: [
    react(),
    babel({ presets: [reactCompilerPreset()] }),
    tailwindcss()
  ],
})
```

### 6.4 Routing & Layouts (React Router DOM)

Unlike Astro or Next.js, Vite has no built-in router — routes are declared explicitly with `react-router-dom`.

```bash
pnpm add react-router-dom
```

**Two-file setup (recommended default)** — `main.tsx` only handles bootstrapping (mounting React to the DOM, wrapping global providers like `<BrowserRouter>`), and `App.tsx` owns the routes with `<Routes>` / `<Route>`.

`src/main.tsx`:

```typescript
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import { BrowserRouter } from 'react-router-dom';
import App from './App.tsx';
import './index.css';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </StrictMode>
);
```

`src/App.tsx`:

```typescript
import { Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import NotFound from './pages/NotFound';

export default function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="*" element={<NotFound />} />
    </Routes>
  );
}
```

**Single-file alternative** — for a very small project (just a couple of routes, no plans to grow), the two files above can be merged into one `main.tsx`, dropping `App.tsx` entirely:

```typescript
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import NotFound from './pages/NotFound';
import './index.css';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  </StrictMode>
);
```

The two-file split is still the more common convention once routes multiply or `App.tsx` starts holding shared state/providers, since it keeps the DOM-mounting boilerplate separate from anything route- or app-logic related — but for a two-route project, either works.

### 6.5 Layout Route with `Outlet`

For a shared shell (navbar + footer on every page — the Vite equivalent of Astro's `Layout.astro` or Next.js's root layout), use a layout route with React Router's `<Outlet />`, which renders whichever child route matched:

`src/layouts/MainLayout.tsx`:

```typescriptreact
import { Outlet } from 'react-router-dom'
import Navbar from '../components/Navbar'
import Footer from '../components/Footer'

export default function MainLayout() {
  return (
    <div className="min-h-screen flex flex-col bg-white text-gray-900 font-sans">
      <Navbar />
      <main className="flex-1">
        <Outlet />
      </main>
      <Footer />
    </div>
  )
}
```

`src/App.tsx`, nesting page routes inside the layout route so every page gets the shared shell:

```typescriptreact
import { Routes, Route } from 'react-router-dom'
import MainLayout from './layouts/MainLayout'
import Home from './pages/Home'
import About from './pages/About'
import Contact from './pages/Contact'
import NotFound from './pages/NotFound'

export default function App() {
  return (
    <Routes>
      <Route element={<MainLayout />}>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
        <Route path="*" element={<NotFound />} />
      </Route>
    </Routes>
  )
}
```

`src/main.tsx` when routing lives inside `App.tsx` (as above) rather than wrapping `<App />` directly — `BrowserRouter` still wraps the app, only the route declarations move:

```typescriptreact
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './global.css'
import App from './App.tsx'

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

> If `<BrowserRouter>` isn't wrapped around `<App />` in `main.tsx` (as in this last example), make sure it's added inside `App.tsx` itself, or swap to `createBrowserRouter` + `<RouterProvider />` for data-loading features (loaders, actions) — see the [React Router docs](https://reactrouter.com/en/main).

### 6.6 Project Structure & Architecture

```
/
├── public/
│   ├── favicon.svg
│   ├── icon.png
│   ├── images/
│   └── robots.txt
├── src/
│   ├── components/
│   │   ├── Hero.tsx
│   │   ├── Navbar.tsx
│   │   └── Footer.tsx
│   ├── layouts/
│   │   └── MainLayout.tsx
│   ├── pages/
│   │   ├── Home.tsx
│   │   ├── About.tsx
│   │   ├── Contact.tsx
│   │   ├── TermsOfService.tsx
│   │   ├── PrivacyPolicy.tsx
│   │   └── NotFound.tsx
│   ├── App.tsx
│   ├── main.tsx
│   └── global.css
├── index.html
├── vite.config.ts
├── package.json
└── tsconfig.json
```

**`public/`** — Static assets served as-is; same role as described in [4.4 `robots.txt`](#44-robotstxt).

**`src/components/`** — Reusable UI pieces (`Hero.tsx`, `Navbar.tsx`, `Footer.tsx`) shared across pages.

**`src/layouts/`** — Shared page shells rendered via a layout route with `<Outlet />` (see [6.5](#65-layout-route-with-outlet)), equivalent to Astro's `Layout.astro` or Next.js's root layout.

**`src/pages/`** — One component per route, registered manually in `App.tsx` when using React Router:

- `Home.tsx` → `/`
- `About.tsx` → `/about`
- `Contact.tsx` → `/contact`
- `TermsOfService.tsx` → `/terms-of-service`
- `PrivacyPolicy.tsx` → `/privacy-policy`
- `NotFound.tsx` → catch-all `*` route

**`src/global.css`** (or `index.css`) — Where Tailwind is imported and font/theme tokens are defined (see [4.2](#42-tailwind-theme--custom-fonts)).

**`index.html`** — The single HTML entry point; holds the `<head>` meta tags and Open Graph tags (see [4.3](#43-open-graph--metadata)), and the `#root` mount point for React.

---

## 7. Next.js

Next.js is the third framework covered here. Unlike a static Astro or Vite build, a standard Next.js application runs a Node.js server in production (see [7.7](#77-production-build)).

### 7.1 Create a New Project

```bash
pnpm create next-app@latest my-next-site
cd my-next-site
```

A typical setup for this README is:

- TypeScript: `Yes`
- ESLint: `Yes`
- Tailwind CSS: `Yes`
- App Router: `Yes`

### 7.2 Install Dependencies

`create-next-app` installs dependencies as part of scaffolding. If they ever need reinstalling (e.g. after cloning the repo):

```bash
pnpm install
```

### 7.3 `next.config.ts` Reference

Basic version — an empty config is valid since Tailwind is already wired in through PostCSS by `create-next-app` (see [4.1](#41-tailwind-css-setup)):

```typescript
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {}

export default nextConfig
```

Extended version, enabling the [React Compiler](https://react.dev/learn/react-compiler) and typed routes — the Next.js equivalent of Vite's extended `vite.config.ts` in [6.3](#63-viteconfigts-reference):

```typescript
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
  experimental: {
    reactCompiler: true,
    typedRoutes: true,
  },
}

export default nextConfig
```

### 7.4 Routing & Layouts (App Router)

Like Astro, Next.js uses **file-based routing** — no router library needed, unlike Vite's `react-router-dom` ([6.4](#64-routing--layouts-react-router-dom)). Every folder under `app/` maps to a URL segment, and a `page.tsx` inside it is what actually renders:

```text
app/page.tsx            → /
app/about/page.tsx      → /about
app/contact/page.tsx    → /contact
app/not-found.tsx       → custom 404 (see 4.6)
```

Layouts nest automatically: any `layout.tsx` wraps every route below it, so the shared shell (navbar + footer) only needs to be defined once at the root — see [7.5](#75-root-layout) for the equivalent of Astro's `<slot />` or Vite's `<Outlet />`. Nested folders can add their own `layout.tsx` to wrap just that subsection of the site (e.g. a `blog/layout.tsx` shared by every post).

### 7.5 Root Layout

`app/layout.tsx` is the shared HTML shell — the Next.js equivalent of Astro's `Layout.astro` ([5.4](#54-main-layout-example)) or Vite's `MainLayout.tsx` + `<Outlet />` ([6.5](#65-layout-route-with-outlet)). Instead of `<slot />` or `<Outlet />`, it receives page content as the `children` prop:

```tsx
import type { Metadata } from 'next'
import Navbar from '../components/Navbar'
import Footer from '../components/Footer'
import './globals.css'

export const metadata: Metadata = {
  title: 'Business title',
  description: 'Business description',
  openGraph: {
    title: 'Business title',
    description: 'Business description',
    url: 'https://mysite.com',
    images: [{ url: 'https://mysite.com/banner.png', width: 1200, height: 630 }],
    type: 'website',
  },
}

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body className="min-h-screen flex flex-col bg-white text-gray-900 font-sans">
        <Navbar />
        <main className="flex-1">{children}</main>
        <Footer />
      </body>
    </html>
  )
}
```

The Metadata API above is the Next.js equivalent of the hand-written Open Graph `<meta>` tags used in Astro/Vite (see [4.3](#43-open-graph--metadata)).

### 7.6 Server and Client Components

App Router components are Server Components by default — this has no direct equivalent in Vite, and is closer in spirit to Astro components (which are also server-rendered by default, with interactive "islands" opted into separately).

Add `'use client'` only when a component needs browser-side state, event handlers, effects or other client-only behavior:

```tsx
'use client'

import { useState } from 'react'

export default function Counter() {
  const [count, setCount] = useState(0)

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  )
}
```

This is important for deployment: server-side code stays inside the Node.js container, while client components are sent to the browser.

### 7.7 Production Build

```bash
pnpm build
pnpm start
```

`pnpm build` creates the optimized production output. `pnpm start` runs the production Next.js server, normally on port `3000`.

For the Docker deployment in [section 8](#8-linux-server--docker-deployment):

- A normal Next.js application should run `next start`.
- Do not treat a normal Next.js application as a `dist/` static site.
- The Next.js container listens internally on port `3000`.
- Traefik forwards HTTPS traffic to that internal port.

> Next.js can also be configured for static export, but that is a different deployment model. This README treats Next.js as a normal Node.js application running in Docker.

### 7.8 Project Structure & Architecture

```
/
├── public/
│   ├── favicon.ico
│   ├── images/
│   └── robots.txt
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   ├── not-found.tsx
│   ├── sitemap.ts
│   ├── about/
│   │   └── page.tsx
│   └── contact/
│       └── page.tsx
├── components/
│   ├── Navbar.tsx
│   └── Footer.tsx
├── lib/
├── package.json
├── next.config.ts
└── tsconfig.json
```

**`public/`** — Static assets served as-is; same role as described in [4.4 `robots.txt`](#44-robotstxt).

**`app/`** — File-based routing (see [7.4](#74-routing--layouts-app-router)). `app/page.tsx` is the homepage, `app/layout.tsx` is the root layout (see [7.5](#75-root-layout)), `app/not-found.tsx` handles 404 pages (see [4.6](#46-404--not-found-page)) and `app/sitemap.ts` generates the sitemap (see [4.5](#45-sitemap-integration)). Each subfolder with its own `page.tsx` becomes a route, equivalent to a file under Astro's `src/pages/` or a route entry in Vite's `App.tsx`.

**`components/`** — Reusable UI pieces (`Navbar.tsx`, `Footer.tsx`) shared across pages, equivalent to `src/components/` in Astro or Vite.

**`lib/`** — Shared utilities, helpers, and non-component logic (data fetching, formatting, etc.).

## 8. Linux Server & Docker Deployment

This section is the complete server setup for **Vite + React and Next.js websites running with Docker and Traefik**.

There is **no Nginx** and no other reverse proxy in this setup. **Traefik is the only public entrypoint** and the only container that publishes ports `80` and `443`.

The architecture is:

```text
Internet
   │
   ├── HTTP :80
   └── HTTPS :443
          │
          ▼
       Traefik
          │
          │ private Docker network
          ├───────────────┐
          ▼               ▼
       Vite app         Next.js app
       internal :80     internal :3000
```

The key rule is:

> **Only Traefik gets public host ports. Website containers stay on the private Docker network.**

This keeps the setup simple. You do not need one reverse proxy per website.

### 8.1 Connect with Bitvise SSH Client

On Windows, [Bitvise SSH Client](https://www.bitvise.com/ssh-client) can be used for both terminal access and SFTP file transfer.

Use:

| Field | What to enter |
|---|---|
| Host | Server public IP or hostname |
| Port | Usually `22` |
| Username | Your Linux user |
| Authentication | Password or SSH private key |

After connecting:

1. Open **New terminal console** to get a Linux terminal.
2. Use the **SFTP** panel to upload ZIP files or project files.
3. Use the terminal to extract and deploy them.

You do not need a separate FTP server just to upload a project.

### 8.2 Basic Linux Setup

Start with the package list:

```bash
sudo apt update
```

This refreshes the list of available packages.

Then upgrade installed packages:

```bash
sudo apt upgrade -y
```

This installs available updates. The `-y` automatically confirms the normal prompts.

After an important system update, you can reboot:

```bash
sudo reboot
```

Your Bitvise session will disconnect. Reconnect after the server comes back.

Useful checks:

```bash
cat /etc/os-release
df -h
free -h
```

They show the operating system, disk usage and RAM usage.

### 8.3 Install Only the Basic Utilities Needed Here

```bash
sudo apt install -y unzip curl git nano htop ufw fail2ban
```

What each package does:

| Package | Purpose |
|---|---|
| `unzip` | Extract ZIP deployment packages |
| `curl` | Test websites and HTTP/HTTPS connections |
| `git` | Clone or update repositories |
| `nano` | Simple terminal text editor |
| `htop` | View CPU, RAM and processes |
| `ufw` | Manage the server firewall |
| `fail2ban` | Temporarily block IPs that repeatedly fail authentication |

For this Docker-only setup, that is enough. There is no need to install a separate web server.

### 8.4 Node.js: Required by the Projects

**Node.js is required for this development stack.** Vite, Next.js and pnpm all use Node.js.

There are two different places where Node.js can exist:

```text
Development machine
    └── Node.js + pnpm

Production server
    └── Docker
         └── node:latest
              └── your application
```

For production, the Linux host does **not** need a separate Node.js installation because the Docker image already contains Node.js.

So:

- Node.js is **not optional for the projects**.
- Node.js is **inside the Docker image**.
- You do not need to install Node twice on the production host.

If you intentionally want Node directly on the server, you can install the Ubuntu package:

```bash
sudo apt install -y nodejs npm
```

Check it:

```bash
node -v
npm -v
```

For the Docker deployment in this README, you can skip those host commands.

### 8.5 Install Docker and Docker Compose

We will keep the installation direct and simple.

First:

```bash
sudo apt update
```

Install Docker and Compose v2:

```bash
sudo apt install -y docker.io docker-compose-v2
```

Ubuntu provides `docker-compose-v2` for the modern `docker compose` command.

Start Docker now and also enable it at boot:

```bash
sudo systemctl enable --now docker
```

Check Docker:

```bash
docker --version
```

Check Compose:

```bash
docker compose version
```

Check the service:

```bash
sudo systemctl status docker
```

The important command is:

```bash
docker compose
```

Do not use the old standalone `docker-compose` command in this README.

### 8.6 Allow Your User to Run Docker Without `sudo`

Add your current Linux user to the Docker group:

```bash
sudo usermod -aG docker $USER
```

Why?

Docker normally requires elevated permissions. Adding your account to the Docker group lets you run:

```bash
docker ps
docker compose up -d
```

without typing `sudo` every time.

**Disconnect and reconnect with Bitvise** after running the command so the new group membership is applied.

Test:

```bash
docker ps
```

If the command works without `sudo`, the setup is ready.

> Docker access is powerful enough to control the host system. Only give trusted users access to it.

### 8.7 First Docker Test

Before creating any website container, test Docker itself:

```bash
docker run --rm hello-world
```

What happens:

1. Docker checks for the `hello-world` image.
2. If necessary, Docker downloads it.
3. Docker creates a container.
4. The container prints a success message.
5. `--rm` removes the stopped container automatically.

This is the fastest way to know whether Docker is working.

### 8.8 Basic Linux Commands for Deployments

You will use these commands constantly:

```bash
pwd
ls
ls -lah
cd /path/to/folder
cd ..
mkdir -p /opt/web
cp source destination
mv old-name new-name
rm file.zip
rm -rf folder
```

Meaning:

- `pwd` — show the current directory.
- `ls` — list files.
- `ls -lah` — detailed listing, including hidden files and readable sizes.
- `cd` — change directory.
- `mkdir -p` — create a directory and missing parent directories.
- `cp` — copy.
- `mv` — move or rename.
- `rm file.zip` — delete one file.
- `rm -rf folder` — permanently delete a directory and everything inside it.

**Warning:** `rm -rf` is destructive. Linux does not send those files to a recycle bin.

Typical ZIP workflow:

```bash
cd /opt
unzip file.zip
rm file.zip
```

You remove the ZIP after extraction to avoid storing two copies of the same deployment.

### 8.9 Firewall Basics with UFW

The server needs SSH, HTTP and HTTPS. Since every domain will always sit behind Cloudflare (see [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl)), it's worth restricting `80`/`443` to Cloudflare's own IP ranges instead of the whole Internet — that way nobody can bypass Cloudflare's protection by hitting the server's IP directly.

First allow SSH:

```bash
sudo ufw allow OpenSSH
```

Then allow HTTP and HTTPS **only from Cloudflare's IP ranges**:

```bash
for ip in $(curl -s https://www.cloudflare.com/ips-v4); do
  sudo ufw allow from "$ip" to any port 80 proto tcp
  sudo ufw allow from "$ip" to any port 443 proto tcp
done

for ip in $(curl -s https://www.cloudflare.com/ips-v6); do
  sudo ufw allow from "$ip" to any port 80 proto tcp
  sudo ufw allow from "$ip" to any port 443 proto tcp
done
```

Enable the firewall:

```bash
sudo ufw enable
```

Check it:

```bash
sudo ufw status verbose
```

**Important:** allow SSH before enabling UFW. Otherwise you can lock yourself out.

Do not open application ports such as `3000` to the Internet. Traefik reaches the websites through Docker networking.

> If a site is ever used without Cloudflare in front of it, allow `80/tcp` and `443/tcp` from anywhere instead (`sudo ufw allow 80/tcp` / `sudo ufw allow 443/tcp`) — but that also means the Origin Certificate from [8.14](#814-traefik--cloudflare-origin-certificate--three-websites) won't be trusted by regular browsers, since it's only trusted by Cloudflare.

### 8.10 Create the Server Structure

Create the main folder:

```bash
sudo mkdir -p /opt/web
cd /opt/web
```

Create the folder for the Cloudflare Origin Certificate (generated in [8.14](#814-traefik--cloudflare-origin-certificate--three-websites)):

```bash
sudo mkdir -p /opt/web/certs
sudo chmod 700 /opt/web/certs
```

Unlike Let's Encrypt, this certificate isn't renewed automatically — it's a file you generate once in the Cloudflare dashboard and it stays valid for up to 15 years, so there's no ACME account or challenge state to persist here.

Create the website folders:

```bash
sudo mkdir -p /opt/web/web1
sudo mkdir -p /opt/web/web2
sudo mkdir -p /opt/web/web3
```

Create the shared Docker network:

```bash
docker network create web
```

Check it:

```bash
docker network ls
```

Final structure:

```text
/opt/web/
├── docker-compose.yml
├── certs/
│   ├── cert.pem
│   └── key.pem
├── dynamic/
│   └── tls.yml
├── web1/
│   ├── Dockerfile
│   └── ...Vite project...
├── web2/
│   ├── Dockerfile
│   └── ...Next.js project...
└── web3/
    ├── Dockerfile
    └── ...Vite project...
```

### 8.11 Vite + React Dockerfile

A normal Vite production build creates a static `dist/` directory.

That means the container can:

1. Start from Node.
2. Install dependencies.
3. Build the website.
4. Serve `dist/`.

`web1/Dockerfile`:

```dockerfile
FROM node:latest

WORKDIR /app

RUN corepack enable

COPY package.json pnpm-lock.yaml ./
RUN pnpm install --frozen-lockfile

COPY . .

RUN pnpm build

RUN npm install -g serve

EXPOSE 80

CMD ["serve", "-s", "dist", "-l", "80"]
```

Why each part exists:

- `FROM node:latest` — gives the image Node.js.
- `WORKDIR /app` — puts the project in `/app`.
- `corepack enable` — makes package-manager tooling such as pnpm available when supported by the Node release.
- `COPY package.json pnpm-lock.yaml ./` — copies dependency metadata first.
- `pnpm install --frozen-lockfile` — installs the exact locked dependencies.
- `COPY . .` — copies the source code.
- `pnpm build` — creates `dist/`.
- `npm install -g serve` — installs a simple Node-based static server.
- `EXPOSE 80` — documents the container port used by the website.
- `CMD ...` — starts the website when the container launches.

The public server still does **not** expose port 80 for this container. Traefik will connect to it internally.

### 8.12 Next.js Dockerfile

A normal Next.js production application is different from a Vite static site.

Next.js normally keeps a Node server running, so the container listens on port `3000`.

`web2/Dockerfile`:

```dockerfile
FROM node:latest

WORKDIR /app

RUN corepack enable

COPY package.json pnpm-lock.yaml ./
RUN pnpm install --frozen-lockfile

COPY . .

RUN pnpm build

EXPOSE 3000

CMD ["pnpm", "start"]
```

Your `package.json` should contain a production start script:

```json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start"
}
```

The important difference is:

```text
Vite + React → internal container port 80
Next.js      → internal container port 3000
```

Both remain private behind Traefik.

### 8.13 `.dockerignore`

Use a `.dockerignore` in every project:

```text
node_modules
dist
.next
.git
.github
.env
.env.*
README.md
npm-debug.log*
pnpm-debug.log*
```

This keeps unnecessary files out of the Docker build context.

In particular:

- `node_modules` should be installed inside the Linux image.
- `dist` and `.next` are generated build output.
- `.env` files should not automatically be baked into images.

### 8.14 Traefik + Cloudflare Origin Certificate + Three Websites

Traefik is the only reverse proxy in this architecture.

It will:

1. Listen on server ports `80` and `443`.
2. Detect the Docker containers that have Traefik labels.
3. Match each domain to the correct container.
4. Redirect HTTP to HTTPS.
5. Present a TLS certificate to whoever connects on `443`.

Traefik's Docker provider reads container labels. Using `exposedbydefault=false` means containers are ignored unless they explicitly opt in with `traefik.enable=true`.

Since every domain here is always proxied through Cloudflare (see [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl)), Cloudflare's free Universal SSL already handles the certificate that public visitors see — Traefik doesn't need to request or renew a Let's Encrypt certificate for that. What Traefik still needs is a certificate for the **Cloudflare → origin** leg of the connection, so that "Full (strict)" mode can verify it. That's what a free **Cloudflare Origin Certificate** is for: generate it once in the Cloudflare dashboard (**SSL/TLS → Origin Server → Create Certificate**), list all three hostnames as SANs (`site1.example.com`, `site2.example.com`, `site3.example.com`), and it stays valid for up to 15 years — no ACME challenge, no renewal automation needed.

Save the two files it gives you:

```bash
sudo nano /opt/web/certs/cert.pem   # paste the "Origin Certificate"
sudo nano /opt/web/certs/key.pem    # paste the "Private Key"
sudo chmod 600 /opt/web/certs/cert.pem /opt/web/certs/key.pem
```

Then tell Traefik to use them via a small dynamic config file:

`/opt/web/dynamic/tls.yml`:

```yaml
tls:
  certificates:
    - certFile: /certs/cert.pem
      keyFile: /certs/key.pem
```

Create `/opt/web/docker-compose.yml`:

```yaml
services:
  traefik:
    image: traefik:v3.7
    container_name: traefik
    restart: unless-stopped
    security_opt:
      - no-new-privileges:true

    command:
      - --providers.docker=true
      - --providers.docker.network=web
      - --providers.docker.exposedbydefault=false
      - --providers.file.directory=/dynamic
      - --providers.file.watch=true

      - --entrypoints.web.address=:80
      - --entrypoints.websecure.address=:443

      - --entrypoints.web.http.redirections.entrypoint.to=websecure
      - --entrypoints.web.http.redirections.entrypoint.scheme=https

      - --log.level=INFO

    ports:
      - "80:80"
      - "443:443"

    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - ./certs:/certs:ro
      - ./dynamic:/dynamic:ro

    networks:
      - web

  web1:
    build:
      context: ./web1
      dockerfile: Dockerfile
    container_name: web1
    restart: unless-stopped
    networks:
      - web
    labels:
      - traefik.enable=true
      - traefik.docker.network=web
      - traefik.http.routers.web1.rule=Host(`site1.example.com`)
      - traefik.http.routers.web1.entrypoints=websecure
      - traefik.http.routers.web1.tls=true
      - traefik.http.services.web1.loadbalancer.server.port=80

  web2:
    build:
      context: ./web2
      dockerfile: Dockerfile
    container_name: web2
    restart: unless-stopped
    networks:
      - web
    labels:
      - traefik.enable=true
      - traefik.docker.network=web
      - traefik.http.routers.web2.rule=Host(`site2.example.com`)
      - traefik.http.routers.web2.entrypoints=websecure
      - traefik.http.routers.web2.tls=true
      - traefik.http.services.web2.loadbalancer.server.port=3000

  web3:
    build:
      context: ./web3
      dockerfile: Dockerfile
    container_name: web3
    restart: unless-stopped
    networks:
      - web
    labels:
      - traefik.enable=true
      - traefik.docker.network=web
      - traefik.http.routers.web3.rule=Host(`site3.example.com`)
      - traefik.http.routers.web3.entrypoints=websecure
      - traefik.http.routers.web3.tls=true
      - traefik.http.services.web3.loadbalancer.server.port=80

networks:
  web:
    external: true
```

> The `tls.certresolver` label from the old Let's Encrypt setup is gone — with a single certificate loaded through the file provider, Traefik just serves it by default, so `traefik.http.routers.webX.tls=true` is all each router needs.

### 8.15 Understand the Important Traefik Lines

**Docker provider**

```text
--providers.docker=true
```

Traefik watches Docker and uses container metadata and labels.

**Do not expose containers automatically**

```text
--providers.docker.exposedbydefault=false
```

This is important because a new container is not automatically published.

**HTTP**

```text
--entrypoints.web.address=:80
```

Traefik listens for HTTP.

**HTTPS**

```text
--entrypoints.websecure.address=:443
```

Traefik listens for HTTPS.

**HTTP → HTTPS**

```text
--entrypoints.web.http.redirections.entrypoint.to=websecure
--entrypoints.web.http.redirections.entrypoint.scheme=https
```

This changes:

```text
http://site1.example.com
```

into:

```text
https://site1.example.com
```

**Origin certificate**

```text
./certs:/certs:ro
./dynamic:/dynamic:ro
```

These mount the Cloudflare Origin Certificate and the file-provider config that loads it (see [8.14](#814-traefik--cloudflare-origin-certificate--three-websites)). No ACME resolver, no HTTP-01 challenge, and nothing to renew — the certificate is generated once in the Cloudflare dashboard and is valid for up to 15 years.

**Docker socket**

```text
/var/run/docker.sock:/var/run/docker.sock:ro
```

Traefik needs Docker metadata to discover the labeled containers. `ro` makes the socket mount read-only at the Docker volume level.

**Domain routing**

```text
traefik.http.routers.web1.rule=Host(`site1.example.com`)
```

This is the rule that decides which website receives a request.

**Internal application port**

```text
traefik.http.services.web1.loadbalancer.server.port=80
```

This is the port inside the Docker network, not a public host port.

### 8.16 Why the Three Websites Are Different

The Compose structure is intentionally repetitive. Only a few values change.

| Website | Framework | Folder | Domain | Internal port |
|---|---|---|---|---:|
| Web 1 | Vite + React | `web1` | `site1.example.com` | `80` |
| Web 2 | Next.js | `web2` | `site2.example.com` | `3000` |
| Web 3 | Vite + React | `web3` | `site3.example.com` | `80` |

When you add `web4`, copy the service that matches the framework.

For another Vite site, change:

```text
context: ./web4
container_name: web4
router/service name: web4
Host(`site4.example.com`)
loadbalancer.server.port=80
```

For another Next.js site:

```text
context: ./web4
container_name: web4
router/service name: web4
Host(`site4.example.com`)
loadbalancer.server.port=3000
```

Everything else stays almost identical.

### 8.17 DNS Setup

Before HTTPS can work, the domains must point to the server through Cloudflare.

In the Cloudflare dashboard, under **DNS → Records**, create:

```text
site1.example.com → A → SERVER_PUBLIC_IP → Proxied (orange cloud)
site2.example.com → A → SERVER_PUBLIC_IP → Proxied (orange cloud)
site3.example.com → A → SERVER_PUBLIC_IP → Proxied (orange cloud)
```

Use `A` records for IPv4 addresses, and keep the proxy status **Proxied** (orange cloud), not **DNS only** (grey cloud). Proxied is what actually puts Cloudflare in front of the site — it hides the server's real IP, applies the free protection described in [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl), and terminates the public-facing SSL. A grey-cloud record just points visitors straight at the server, bypassing all of that.

The important rule is:

```text
Domain → Cloudflare (proxy + SSL) → server running Traefik → ports 80/443
```

Because the record is proxied, a plain `nslookup` or `curl` from your computer now resolves to a Cloudflare IP, not the server's — that's expected and confirms the proxy is active:

```bash
nslookup site1.example.com
```

To check that the server itself is reachable and Traefik is answering, run this from the server:

```bash
curl -I http://localhost
```

Do not move on to HTTPS troubleshooting until the record shows as proxied in Cloudflare and the server responds locally.

### 8.18 First Deployment

Upload your ZIP with Bitvise SFTP.

For example:

```text
/opt/web-deploy.zip
```

Extract it:

```bash
cd /opt
unzip web-deploy.zip
rm web-deploy.zip
```

Enter the project directory:

```bash
cd /opt/web
```

Check the files:

```bash
ls -lah
```

Before starting everything, validate the Compose file:

```bash
docker compose config
```

If this command succeeds, Compose can parse the configuration.

Start the stack:

```bash
docker compose up --build -d
```

Meaning:

- `up` — create and start the services.
- `--build` — build the application images.
- `-d` — keep them running in the background.

Check containers:

```bash
docker compose ps
```

Check all Docker containers:

```bash
docker ps
```

Check Traefik logs:

```bash
docker compose logs -f traefik
```

### 8.19 Useful Deployment Commands

These are the commands you will use most often:

```bash
# Build images and start everything
docker compose up --build -d

# Start without rebuilding
docker compose up -d

# Stop the Compose stack
docker compose down

# Stop and remove orphan containers
docker compose down --remove-orphans

# Rebuild and deploy one website
docker compose up --build -d web1

# Follow all logs
docker compose logs -f

# Follow Traefik logs
docker compose logs -f traefik

# Follow one website's logs
docker compose logs -f web1

# Restart one website
docker compose restart web1

# Show running containers
docker ps

# Show all containers
docker ps -a

# Show Docker images
docker images
```

Basic ZIP deployment commands:

```bash
unzip file.zip
rm file.zip
# rm -rf <folder>   # WARNING: permanently deletes everything inside
```

### 8.20 Update Only One Website

Suppose only `web2` changed. `docker-compose.yml` and `certs/` live one level above `web2/`, so none of this touches them.

Back up anything that only exists on the server and isn't in your new zip (usually the `Dockerfile`, if you created it directly on the server instead of keeping it in your project — see [8.11](#811-vite--react-dockerfile)/[8.12](#812-nextjs-dockerfile) — and any `.env` file):

```bash
cp web2/Dockerfile /opt/web2-Dockerfile.bak
cp web2/.env /opt/web2-env.bak   # only if it exists
```

Upload the new zip via Bitvise SFTP, then replace the project folder:

```bash
cd /opt/web
rm -rf web2
unzip /opt/web2-update.zip -d web2
rm /opt/web2-update.zip
```

Restore whatever you backed up (skip this if your zip already included it):

```bash
cp /opt/web2-Dockerfile.bak web2/Dockerfile
cp /opt/web2-env.bak web2/.env
```

Rebuild and restart just that container:

```bash
docker compose up --build -d web2
```

Only `web2` is rebuilt/recreated. Traefik and the other websites keep running without interruption.

Check it started cleanly:

```bash
docker compose logs -f web2
```

This is the normal workflow once several websites share the same server.

### 8.21 Docker Disk Cleanup

Check Docker's disk usage:

```bash
docker system df
```

Remove unused containers, networks and images:

```bash
docker system prune
```

For a more aggressive cleanup:

```bash
docker system prune -a
```

Use `-a` carefully because it can delete unused images that you might want for faster future deployments.

Also check the server disk:

```bash
df -h
```

### 8.22 Fail2ban Basic Configuration

Fail2ban is mainly useful here for protecting SSH from repeated login attempts.

Enable it:

```bash
sudo systemctl enable --now fail2ban
```

Check the service:

```bash
sudo systemctl status fail2ban
```

Create the local jail configuration:

```bash
sudo nano /etc/fail2ban/jail.local
```

Basic SSH configuration:

```ini
[DEFAULT]
bantime = 1h
findtime = 10m
maxretry = 5

[sshd]
enabled = true
```

What those values mean:

- `bantime = 1h` — ban an IP for one hour.
- `findtime = 10m` — evaluate failures inside a ten-minute window.
- `maxretry = 5` — five matching failures can trigger a ban.
- `[sshd]` — enable the SSH jail.

Restart Fail2ban:

```bash
sudo systemctl restart fail2ban
```

Check active jails:

```bash
sudo fail2ban-client status
```

Check SSH specifically:

```bash
sudo fail2ban-client status sshd
```

Fail2ban is an additional layer. It does not replace updates, firewall rules or SSH keys. It's only needed here for SSH — SSH isn't proxied through Cloudflare, so Cloudflare's DDoS/bot protection never sees it. The websites themselves don't need a `[traefik]`/HTTP jail: that surface already sits behind Cloudflare's free protection (see [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl)), and UFW ([8.9](#89-firewall-basics-with-ufw)) already blocks anyone trying to hit ports `80`/`443` directly instead of through Cloudflare.

### 8.23 Basic SSH Hardening

SSH is the main administrative door to the server.

First make sure your Bitvise SSH key login works.

Then edit:

```bash
sudo nano /etc/ssh/sshd_config
```

A common baseline is:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
```

Meaning:

- `PermitRootLogin no` — do not allow direct root login.
- `PasswordAuthentication no` — disable password authentication once key login is confirmed.
- `PubkeyAuthentication yes` — keep SSH key login enabled.

**Important:** do not disable password authentication until you have successfully tested your SSH key in a second Bitvise session.

Validate the configuration before restarting SSH:

```bash
sudo sshd -t
```

If there is no error, restart SSH:

```bash
sudo systemctl restart ssh
```

### 8.24 Troubleshooting

**Website does not open**

Check:

```bash
docker compose ps
```

Then:

```bash
docker compose logs -f traefik
```

And check the application:

```bash
docker compose logs -f web1
docker compose logs -f web2
docker compose logs -f web3
```

**Browser shows a Cloudflare SSL error (521/526) or "not secure"**

Check in this order:

1. The DNS record is **Proxied** (orange cloud), not DNS only — see [8.17](#817-dns-setup).
2. SSL/TLS mode in Cloudflare is set to **Full (strict)**, not Flexible ([9.4](#94-vite--nextjs--cloudflare-protection--free-ssl)).
3. `/opt/web/certs/cert.pem` and `key.pem` exist and hold the Origin Certificate/Key generated in [8.14](#814-traefik--cloudflare-origin-certificate--three-websites), not placeholders.
4. The Origin Certificate's SANs include the exact domain being requested.
5. UFW allows `80`/`443` from Cloudflare's IP ranges ([8.9](#89-firewall-basics-with-ufw)).
6. The `Host(...)` rule exactly matches the domain.
7. Traefik logs show the certificate being loaded from the file provider, with no errors reading `/certs`.

**Next.js connection error**

Make sure:

```text
traefik.http.services.webX.loadbalancer.server.port=3000
```

and that the Next.js container is actually running `next start`.

**Vite connection error**

Make sure:

```text
traefik.http.services.webX.loadbalancer.server.port=80
```

and that the container is running:

```text
serve -s dist -l 80
```

**HTTPS works for one site but not another**

Usually the problem is one of:

- DNS for the second domain.
- Wrong `Host(...)` label.
- Wrong router/service name.
- The second container is not running.
- The internal port is wrong.

### 8.25 Final Production Checklist

```text
[ ] Server packages updated
[ ] Bitvise SSH works
[ ] Docker installed
[ ] docker compose works
[ ] User can run Docker
[ ] UFW allows SSH, HTTP and HTTPS
[ ] Traefik is the only public entrypoint
[ ] Docker network "web" exists
[ ] Cloudflare Origin Certificate generated and saved to certs/cert.pem + key.pem
[ ] DNS records point to the server and are set to Proxied (orange cloud)
[ ] SSL/TLS mode in Cloudflare is Full (strict)
[ ] Vite Dockerfile builds correctly
[ ] Next.js Dockerfile builds correctly
[ ] Traefik routes use the correct domains
[ ] Fail2ban is running (SSH jail)
[ ] SSH key login has been tested
[ ] Root SSH login is disabled
[ ] Password SSH login is disabled after key verification
[ ] No website container publishes a public host port
```

---
## 9. Deployment

### 9.1 Google Search Console

1. Go to [Google Search Console](https://search.google.com/search-console) and add a new property using the site's domain or URL prefix.
2. Verify ownership — via DNS TXT record (domain property) or an HTML file/meta tag (URL-prefix property), depending on the method chosen.
3. Once verified, submit the sitemap under **Sitemaps** using the sitemap URL generated by the project (e.g. `https://mysite.com/sitemap-index.xml` for Vite + React, or the sitemap URL generated by the project).
4. Use the **URL Inspection** tool to request indexing for key pages after the first deploy.

### 9.2 Cloudflare Pages

1. In the [Cloudflare dashboard](https://dash.cloudflare.com/), go to **Workers & Pages → Create → Pages**, and connect the GitHub repository.
2. Configure the build settings:
   - **Framework preset**: Vite + React (Cloudflare has presets for both).
   - **Build command**: `pnpm build` (or `npm run build`).
   - **Build output directory**: `dist` (default for Vite + React).
3. Add any required environment variables under **Settings → Environment variables**.
4. Every push to the connected branch (e.g. `main`) triggers an automatic deploy; other branches get preview deployments.
5. Under **Custom domains**, attach the production domain once it's ready.

Astro sites always live in your own Cloudflare Pages account, but the domain itself usually belongs to the client — see [9.5](#95-pointing-the-clients-domain-astro) for how to point it there.

### 9.3 Cloudflare Domains & Rules

- **DNS**: if the domain is registered with Cloudflare (or just uses Cloudflare as DNS), add/verify the records under **DNS → Records**. Pages projects usually just need a `CNAME` pointing to the `*.pages.dev` deployment, added automatically when attaching a custom domain.
- **SSL/TLS**: keep the encryption mode set to **Full** or **Full (strict)** for Pages projects.
- **Redirect rules**: under **Rules → Redirect Rules**, common basics are forcing `www` → apex (or the reverse) and forcing `https`.
- **Page Rules / Cache Rules**: useful for basics like always redirecting `http://` to `https://`, or setting cache behavior for static assets under `/images/*` or `/assets/*`.

### 9.4 Vite + Next.js + Cloudflare Protection & Free SSL

This section applies to the self-hosted Vite/Next.js sites from [8. Linux Server & Docker Deployment](#8-linux-server--docker-deployment) — the Docker + Traefik setup running on your own VPS, as opposed to [9.2](#92-cloudflare-pages) which is for Cloudflare Pages. On the free plan, Cloudflare in front of that server gives you both protection and SSL with nothing extra to buy or renew.

**1. Add the site and proxy the DNS record**

In the Cloudflare dashboard, add the domain and create the `A` record described in [8.17](#817-dns-setup), keeping it **Proxied** (orange cloud). This is what actually routes traffic through Cloudflare instead of straight to the server, and it's a prerequisite for everything below.

**2. Set the SSL/TLS encryption mode to Full (strict)**

Under **SSL/TLS → Overview**, choose **Full (strict)**. This encrypts both legs of the connection: browser → Cloudflare (Cloudflare's free Universal SSL certificate, issued and renewed automatically) and Cloudflare → your server (the Cloudflare Origin Certificate from [8.14](#814-traefik--cloudflare-origin-certificate--three-websites)). Avoid **Flexible** — it only encrypts the first leg, leaving Cloudflare-to-server traffic in plain HTTP.

**3. Turn on "Always Use HTTPS"**

Under **SSL/TLS → Edge Certificates**, enable **Always Use HTTPS** so any `http://` request gets redirected. This is redundant with Traefik's own HTTP→HTTPS redirect ([8.15](#815-understand-the-important-traefik-lines)), but costs nothing to leave on and catches requests before they even reach the server.

**4. Protection that's on by default (nothing to configure)**

The free plan already includes, automatically, for any proxied domain:

- Unmetered DDoS protection at the network edge.
- The server's real IP is hidden — only Cloudflare's IPs are ever visible to visitors, which is what [8.9](#89-firewall-basics-with-ufw)'s UFW rule (allowing `80`/`443` only from Cloudflare's ranges) is there to enforce.
- A CDN cache for static assets, reducing load on the server.

**5. Optional extra protection (free plan)**

- **Bot Fight Mode** (**Security → Bots**) — challenges known bad bots.
- **Under Attack Mode** (**Security → Settings**) — puts up a JS challenge page for every visitor; use temporarily during an active attack, not by default, since it adds friction for real visitors.
- Up to 5 free custom **WAF rules** (**Security → WAF**) if you want to block or challenge specific patterns (e.g. a known bad path or country).

**What this replaces**

Because Cloudflare handles the above automatically, this setup intentionally drops what a non-Cloudflare deployment would otherwise need: no Let's Encrypt/ACME renewal loop on the server ([8.14](#814-traefik--cloudflare-origin-certificate--three-websites)), no open port `80`/`443` to the whole Internet ([8.9](#89-firewall-basics-with-ufw)), and no separate HTTP-layer fail2ban jail ([8.22](#822-fail2ban-basic-configuration)) — Fail2ban stays, but only for SSH.

Everything above assumes the domain's DNS is already a zone inside your own Cloudflare account. When the domain actually belongs to a client, see [9.6](#96-pointing-the-clients-domain-vite--nextjs) for how to get it pointed at the server.

### 9.5 Pointing the Client's Domain (Astro)

This applies to Astro sites deployed on [9.2](#92-cloudflare-pages): the Pages project always lives in **your** Cloudflare account, but the domain (e.g. `clientsite.com`) belongs to the client. There are two ways to connect them, depending on how much access the client is willing to give you.

**Option A — The client moves their nameservers into your Cloudflare account (best integration)**

1. In your Cloudflare dashboard, go to **Add a site** and enter the client's domain. Choose the **Free** plan.
2. Cloudflare scans existing DNS records and shows you two nameservers (e.g. `xxx.ns.cloudflare.com`).
3. Send those nameservers to the client and have them update them at their domain registrar (GoDaddy, Namecheap, etc.).
4. Once the nameserver change propagates (can take a few hours), the domain shows as **Active** in your Cloudflare account.
5. Go to the Astro **Pages** project → **Custom domains** → **Set up a custom domain**, enter the client's domain, and Cloudflare attaches it automatically (it's already in your account, so no manual CNAME/TXT verification is needed).
6. SSL is issued automatically by Cloudflare for the new custom domain.

This option gives you full control (redirect rules, caching, WAF) but requires the client to hand over DNS management, which not every client wants to do.

**Option B — The client keeps their own DNS (their registrar or their own Cloudflare account)**

1. Go to the Astro **Pages** project → **Custom domains** → **Set up a custom domain**, and enter the client's domain (e.g. `www.clientsite.com` or the apex domain).
2. Cloudflare shows the exact DNS record to create — normally a `CNAME` pointing to `<project-name>.pages.dev`. For an apex/root domain (`clientsite.com` with no `www`), Cloudflare Pages supports CNAME flattening, so a `CNAME` at the root also works if the client's DNS provider allows it.
3. Send that record to the client (or whoever manages their DNS) and ask them to add it.
4. If the client's domain is **not** on Cloudflare at all, verification is via the DNS record itself — no Cloudflare account needed on their side, and Cloudflare Pages still issues a free SSL certificate for the custom domain once the record resolves.
5. If the client's domain **is** on their own separate Cloudflare account, they add the same `CNAME` record there; whether it's Proxied or DNS-only doesn't matter for Pages custom domains — Pages issues its own certificate either way.
6. Wait for the **Custom domains** tab in your Pages project to show the domain as **Active**.

Option B is the usual choice for client work: it needs no access to their registrar or Cloudflare account beyond asking them to paste in one DNS record.

### 9.6 Pointing the Client's Domain (Vite + Next.js)

This applies to the self-hosted Vite/Next.js sites from [8. Linux Server & Docker Deployment](#8-linux-server--docker-deployment), using the free SSL setup from [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl). Unlike Astro on Pages, this setup needs the domain to actually be **proxied through Cloudflare** (orange cloud) for the free Universal SSL and DDoS/bot protection to apply — a plain DNS-only record pointed at the server bypasses Cloudflare entirely.

**Option A — The client moves their nameservers into your Cloudflare account**

1. Add the domain to your Cloudflare account the same way as in [9.5](#95-pointing-the-clients-domain-astro), Option A (steps 1–4).
2. Once the domain is **Active** in your account, follow [8.17](#817-dns-setup) exactly: create the `A` record pointing to the server's public IP, kept **Proxied** (orange cloud).
3. Generate/reuse the Cloudflare **Origin Certificate** for that domain ([8.14](#814-traefik--cloudflare-origin-certificate--three-websites)) and add it to Traefik's `dynamic` config alongside the existing sites.
4. Set **SSL/TLS → Overview** to **Full (strict)** for the zone, as in [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl).

**Option B — The client keeps their own Cloudflare account**

Use this when the client already has the domain on Cloudflare themselves and doesn't want to change nameservers.

1. Give the client the server's public IP and ask them to create an `A` record (e.g. `app.clientsite.com` → your server IP) in **their** Cloudflare dashboard, kept **Proxied** (orange cloud). Without Proxied, they get no free SSL or protection from Cloudflare — traffic goes straight to the server over plain HTTP unless you handle certificates yourself.
2. Ask the client to set their zone's **SSL/TLS → Overview** to **Full (strict)** — same reasoning as [9.4](#94-vite--nextjs--cloudflare-protection--free-ssl): Flexible would leave the Cloudflare→server leg unencrypted.
3. You still need a **Cloudflare Origin Certificate** on the server for that domain so the Cloudflare→server leg is encrypted. Since the zone lives in the client's account, either:
   - Ask the client to generate the Origin Certificate themselves (**SSL/TLS → Origin Server → Create Certificate**, covering the subdomain you need) and send you the cert/key pair, which you drop into `certs/` and reference in Traefik's `dynamic` config exactly like the other sites in [8.14](#814-traefik--cloudflare-origin-certificate--three-websites); or
   - Ask them to add you as a member on their Cloudflare account (**Manage Account → Members**) with access scoped to that zone, so you can generate the certificate yourself without them needing to know what it is.
4. Add a new router/service block in `docker-compose.yml` for the client's domain, following the pattern in [8.16](#816-why-the-three-websites-are-different) — same idea, just with the client's domain in the `Host(...)` rule instead of one of your own.
5. Firewall-wise, nothing changes: UFW ([8.9](#89-firewall-basics-with-ufw)) already only allows `80`/`443` from Cloudflare's IP ranges regardless of which Cloudflare account is proxying the request.

**Option A vs Option B**

| | Option A (your account) | Option B (client's account) |
|---|---|---|
| Who manages DNS | You | The client |
| Nameserver change needed | Yes | No |
| Origin Certificate generated by | You | You or the client, depending on access |
| Best for | Long-term/ongoing clients | Clients who want to keep control of their domain |

---
## 10. Git and GitHub

### 10.1 Initial Setup (First-Time Project)

Use these commands when starting a brand-new project locally and connecting it to a GitHub repository.

```bash
git init
```
Initializes a new, empty Git repository in the local project folder.

```bash
git add .
```
Stages all modified and new files, preparing them to be saved.

```bash
git commit -m "initial commit"
```
Saves staged changes locally with a descriptive message.

```bash
git branch -M main
```
Renames the default local branch to `main`.

```bash
git remote add origin <repository-URL>
```
Links the local repository to the remote repository on GitHub.

```bash
git push -u origin main
```
Uploads local commits to the `main` branch on GitHub for the first time.

### 10.2 Daily Workflow

Use these steps every time files are edited and need to be pushed to GitHub.

```bash
git status
```
Shows which files have been modified or added (safe to run anytime).

```bash
git add .
```
Stages the latest changes.

```bash
git commit -m "describe your changes here"
```
Saves changes locally with a message explaining what was done.

```bash
git push
```
Uploads newly saved local commits to GitHub.

### 10.3 Branching

Branches allow working on new features safely without breaking the live site.

```bash
git branch
```
Lists all local branches and shows the current one.

```bash
git branch <branch-name>
```
Creates a new branch.

```bash
git checkout <branch-name>
```
Switches to the specified branch (or `git switch <branch-name>`).

```bash
git checkout -b <branch-name>
```
Creates a new branch and switches to it immediately (or `git switch -c <branch-name>`).

```bash
git merge <branch-name>
```
Merges changes from the specified branch into the current branch.

### 10.4 Other Useful Commands

```bash
git pull
```
Downloads and integrates the latest changes from GitHub into the local project (essential when working with others).

```bash
git clone <repository-URL>
```
Downloads an existing GitHub repository onto the local machine.

```bash
git log
```
Displays the history of all commits made in the repository.

### 10.5 Undoing Things: `reset`, `restore`, `revert`

These three commands all "undo" something, but they act on different things and at different levels of danger.

```bash
git restore <file>
```
Discards uncommitted local changes to a file, reverting it back to the last committed version. Safe for the file itself, but **the discarded changes are gone**.

```bash
git restore --staged <file>
```
Unstages a file (removes it from the staging area) without touching its actual content — the opposite of `git add <file>`.

```bash
git reset --soft <commit>
```
Moves the current branch pointer back to `<commit>`, keeping all changes staged. Useful for squashing the last few commits into one before committing again.

```bash
git reset --mixed <commit>
```
Same as `--soft`, but also unstages the changes (they stay in the working directory as uncommitted edits). This is the **default mode** if no flag is passed.

```bash
git reset --hard <commit>
```
Moves the branch pointer back to `<commit>` **and discards all changes** (staged and unstaged) to match that commit exactly. Destructive — anything not committed elsewhere (e.g. pushed, or on another branch) is lost permanently.

```bash
git revert <commit>
```
Creates a **new commit** that undoes the changes from `<commit>`, without rewriting history. Safe to use on commits that have already been pushed/shared, since `reset --hard` on shared history causes conflicts for collaborators.

> Rule of thumb: use `revert` on commits that are already pushed and shared with others; use `reset` freely on local commits nobody else has pulled yet.

### 10.6 `rebase` vs `merge`

Both combine work from one branch into another, but they produce different history.

```bash
git merge <branch-name>
```
Combines `<branch-name>` into the current branch by creating a new **merge commit** with two parents. Preserves the exact history of both branches — nothing is rewritten — but the log ends up with extra merge commits and parallel-looking history.

```bash
git rebase <branch-name>
```
Replays the current branch's commits **on top of** `<branch-name>`, rewriting them with new commit hashes. Produces a clean, linear history with no merge commits — but because it rewrites commits, it should only be done on local/unpushed commits, or on a feature branch nobody else is also working on.

```bash
git rebase --continue
```
After manually resolving a conflict during a rebase (editing the conflicted file and running `git add <file>`), continues replaying the remaining commits.

```bash
git rebase --abort
```
Cancels an in-progress rebase and returns the branch to the state it was in before the rebase started.

| | `merge` | `rebase` |
|---|---|---|
| History | Preserves branch history, adds a merge commit | Linear, rewrites commit hashes |
| Safe on shared/pushed branches | Yes | No (unless nobody else has pulled those commits) |
| Typical use | Merging a finished feature branch into `main` | Cleaning up / updating a feature branch before opening a PR |

### 10.7 Force Push and Other Dangerous Commands

```bash
git push --force
```
Overwrites the remote branch's history with the local branch's history, discarding any remote commits that aren't in the local branch. Dangerous on shared branches (like `main`) since it can permanently erase a teammate's pushed work.

```bash
git push --force-with-lease
```
Same idea, but refuses to overwrite the remote branch if someone else has pushed new commits since the last fetch. This is the **safer default** for force-pushing a personal feature branch (e.g. after a rebase) — prefer this over plain `--force`.

```bash
git stash
```
Temporarily shelves uncommitted changes (staged and unstaged) so the working directory is clean, e.g. to switch branches without committing half-finished work.

```bash
git stash pop
```
Re-applies the most recently stashed changes and removes them from the stash list.

```bash
git cherry-pick <commit>
```
Applies a single specific commit from another branch onto the current branch, without merging the whole branch.

> As a general rule: never force-push to `main` or any branch other people are actively pulling from. Force-push is for cleaning up **your own** feature branch before it's merged.

### 10.8 Real Branching Flow: Feature Branch → Main

A realistic day-to-day flow for working on a feature without breaking `main`, including the forks in the road that commonly come up.

**Step 1 — Start from an up-to-date `main`:**

```bash
git checkout main
git pull
```

**Step 2 — Create the feature branch:**

```bash
git checkout -b feature/login-form
```

**Step 3 — Work normally, committing as you go:**

```bash
git add .
git commit -m "add login form UI"
# ...more edits...
git add .
git commit -m "wire up form validation"
```

**Step 4 — Before opening a PR, update the branch with the latest `main`.** Two options here, depending on whether the branch is still private (only local, or on a fork nobody else pulled from) or already shared with someone else:

- **If nobody else has pulled your branch** → rebase for a clean, linear history:

  ```bash
  git checkout main
  git pull
  git checkout feature/login-form
  git rebase main
  ```

  - **If a conflict appears** → Git pauses and marks the conflicted file(s). Open them, resolve the `<<<<<<<` / `=======` / `>>>>>>>` markers by hand, then:

    ```bash
    git add <resolved-file>
    git rebase --continue
    ```

    Repeat for each conflicting commit until the rebase finishes. If it gets too messy, back out entirely with `git rebase --abort` and try `merge` instead (next bullet).

  - **If no conflict appears** → the rebase finishes immediately, and the branch now sits cleanly on top of the latest `main`.

  Since rebase rewrote the branch's commit hashes, pushing it again requires:

  ```bash
  git push --force-with-lease
  ```

- **If someone else is also working on that branch** → merge `main` into it instead, since rebasing would rewrite commits they may have already pulled:

  ```bash
  git checkout feature/login-form
  git merge main
  ```

  - **If a conflict appears** → resolve the marked files by hand, then:

    ```bash
    git add <resolved-file>
    git commit
    ```

    (a merge conflict is resolved with a normal commit, not `--continue`).

  - **If no conflict appears** → Git creates the merge commit automatically, no extra step needed.

  A regular push works fine here, no `--force` needed:

  ```bash
  git push
  ```

**Step 5 — Merge the feature branch into `main`.** Again, two common paths:

- **Merging locally** (small personal projects, no PR review process):

  ```bash
  git checkout main
  git pull
  git merge feature/login-form
  git push
  ```

- **Merging via a Pull Request** (team projects, GitHub) — push the feature branch, open a PR on GitHub from `feature/login-form` into `main`, get it reviewed, then merge using GitHub's UI (Merge commit, Squash and merge, or Rebase and merge — pick whichever the team's convention is). Afterwards, sync locally:

  ```bash
  git checkout main
  git pull
  ```

**Step 6 — Clean up the finished branch:**

```bash
git branch -d feature/login-form          # delete local branch (only works if fully merged)
git push origin --delete feature/login-form  # delete remote branch
```

> If `git branch -d` refuses because the branch isn't fully merged (e.g. it was squash-merged on GitHub, so Git doesn't recognize the commits as merged), force the local delete with `git branch -D feature/login-form` once the PR is confirmed merged on GitHub.

---

## 11. Common HTTP Status Codes

Useful when debugging API requests (fetch calls, form submissions, backend responses) across any of the three frameworks.

| Code | Name | Meaning |
|---|---|---|
| `200` | OK | Request succeeded |
| `201` | Created | Request succeeded and a new resource was created |
| `204` | No Content | Request succeeded, no content is returned (common for DELETE) |
| `400` | Bad Request | The request is malformed or missing required data |
| `401` | Unauthorized | Authentication is missing or invalid |
| `403` | Forbidden | Authenticated, but not allowed to access this resource |
| `404` | Not Found | The requested resource doesn't exist |
| `409` | Conflict | The request conflicts with the current state of the resource (e.g. duplicate entry) |
| `422` | Unprocessable Entity | The request is well-formed but fails validation |
| `429` | Too Many Requests | Rate limit exceeded — slow down and retry later |
| `500` | Internal Server Error | Generic server-side failure |
| `502` | Bad Gateway | An upstream server (e.g. reverse proxy, Traefik) got an invalid response |
| `503` | Service Unavailable | The server is temporarily overloaded or down for maintenance |
