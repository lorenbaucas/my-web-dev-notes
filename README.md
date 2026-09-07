# Developer Notes

Personal reference notes for setting up a web development environment, scaffolding websites with **Astro, Vite + React, and Next.js**, and working with Git/GitHub.

## Index

- [1. Required Programs](#1-required-programs)
- [2. VS Code](#2-vs-code)
  - [2.1 Extensions](#21-extensions)
  - [2.2 Keyboard Shortcuts](#22-keyboard-shortcuts)
- [3. Shared Website Setup](#3-shared-website-setup)
  - [3.1 Tailwind CSS Setup](#31-tailwind-css-setup)
  - [3.2 Tailwind Theme & Custom Fonts](#32-tailwind-theme--custom-fonts)
  - [3.3 Open Graph & Metadata](#33-open-graph--metadata)
  - [3.4 JSON-LD Structured Data (schema.org)](#34-json-ld-structured-data-schemaorg)
  - [3.5 Progressive Web App (PWA) Setup](#35-progressive-web-app-pwa-setup)
  - [3.6 `robots.txt`](#36-robotstxt)
  - [3.7 Sitemap Integration](#37-sitemap-integration)
  - [3.8 404 / Not Found Page](#38-404--not-found-page)
  - [3.9 Prettier Setup](#39-prettier-setup)
  - [3.10 ESLint Setup](#310-eslint-setup)
  - [3.11 Windows PowerShell Execution Policy / npm Recovery](#311-windows-powershell-execution-policy--npm-recovery)
  - [3.12 Development Server](#312-development-server)
  - [3.13 `.env` Example](#313-env-example)
  - [3.14 `.gitignore` Example](#314-gitignore-example)
- [4. Astro](#4-astro)
  - [4.1 Project Setup](#41-project-setup)
  - [4.2 Install Dependencies](#42-install-dependencies)
  - [4.3 Routing & Client-Side Navigation](#43-routing--client-side-navigation)
  - [4.4 Main Layout Example](#44-main-layout-example)
  - [4.5 Project Structure & Architecture](#45-project-structure--architecture)
- [5. Vite](#5-vite)
  - [5.1 Scaffolding a New Project](#51-scaffolding-a-new-project)
  - [5.2 Install Dependencies](#52-install-dependencies)
  - [5.3 `vite.config.ts` Reference](#53-viteconfigts-reference)
  - [5.4 Routing & Layouts (React Router DOM)](#54-routing--layouts-react-router-dom)
  - [5.5 Layout Route with `Outlet`](#55-layout-route-with-outlet)
  - [5.6 Project Structure & Architecture](#56-project-structure--architecture)
- [6. Next.js](#6-nextjs)
  - [6.1 Create a New Project](#61-create-a-new-project)
  - [6.2 Install Dependencies](#62-install-dependencies)
  - [6.3 `next.config.ts` Reference](#63-nextconfigts-reference)
  - [6.4 Routing & Layouts (App Router)](#64-routing--layouts-app-router)
  - [6.5 Root Layout](#65-root-layout)
  - [6.6 Server and Client Components](#66-server-and-client-components)
  - [6.7 Production Build](#67-production-build)
  - [6.8 Project Structure & Architecture](#68-project-structure--architecture)
- [7. Database & Backend: Prisma + PostgreSQL](#7-database--backend-prisma--postgresql)
  - [7.1 Overview: Which Framework Needs a Separate Backend](#71-overview-which-framework-needs-a-separate-backend)
  - [7.2 Backend Project Structure](#72-backend-project-structure)
  - [7.3 Install Dependencies](#73-install-dependencies)
  - [7.4 `.env` Example](#74-env-example)
  - [7.5 Configuration Files: `tsconfig.json`, `prisma.config.ts` and `pnpm-workspace.yaml`](#75-configuration-files-tsconfigjson-prismaconfigts-and-pnpm-workspaceyaml)
  - [7.6 PostgreSQL: Starting the Database](#76-postgresql-starting-the-database)
  - [7.7 Prisma From Scratch: Default `schema.prisma`](#77-prisma-from-scratch-default-schemaprisma)
  - [7.8 Add a Simple `User` Model](#78-add-a-simple-user-model)
  - [7.9 Create and Apply the First Migration](#79-create-and-apply-the-first-migration)
  - [7.10 Modifying an Existing Schema: Update `User` and Add a New Table](#710-modifying-an-existing-schema-update-user-and-add-a-new-table)
  - [7.11 Simple Backend Entry Point (`src/index.ts`): Login Example](#711-simple-backend-entry-point-srcindexts-login-example)
  - [7.12 Seed Example](#712-seed-example)
  - [7.13 Prisma Studio](#713-prisma-studio)
  - [7.14 Day-to-Day Workflow and Reference Commands](#714-day-to-day-workflow-and-reference-commands)
  - [7.15 Common Prisma and PostgreSQL Errors](#715-common-prisma-and-postgresql-errors)
- [8. Full Separation: Independent Backend, Frontend(s) and Deployment](#8-full-separation-independent-backend-frontends-and-deployment)
  - [8.1 Why Full Separation Instead of a Monorepo](#81-why-full-separation-instead-of-a-monorepo)
  - [8.2 Backend Repo: `docker-compose.yml` (Postgres and API)](#82-backend-repo-docker-composeyml-postgres-and-api)
  - [8.3 Backend `Dockerfile` (pnpm, Node 24, Multi-Stage)](#83-backend-dockerfile-pnpm-node-24-multi-stage)
  - [8.4 `pnpm-workspace.yaml`: Allowing Build Scripts (pnpm 10 or Newer)](#84-pnpm-workspaceyaml-allowing-build-scripts-pnpm-10-or-newer)
  - [8.5 CORS and Cookies Across Different Domains](#85-cors-and-cookies-across-different-domains)
  - [8.6 Each Frontend as Its Own Repo (Cloudflare Pages)](#86-each-frontend-as-its-own-repo-cloudflare-pages)
  - [8.7 HTTPS in Front of the Backend (Caddy)](#87-https-in-front-of-the-backend-caddy)
  - [8.8 Local Development Without Docker for the Backend](#88-local-development-without-docker-for-the-backend)
  - [8.9 Final Project Structure (Three Independent Repos)](#89-final-project-structure-three-independent-repos)
  - [8.10 Continuous Deployment on Push (GitHub Actions)](#810-continuous-deployment-on-push-github-actions)
- [9. Linux Server & Docker Deployment](#9-linux-server--docker-deployment)
  - [9.1 Connect with Bitvise SSH Client](#91-connect-with-bitvise-ssh-client)
  - [9.2 Basic Linux Setup](#92-basic-linux-setup)
  - [9.3 Install Only the Basic Utilities Needed Here](#93-install-only-the-basic-utilities-needed-here)
  - [9.4 Node.js: Required by the Projects](#94-nodejs-required-by-the-projects)
  - [9.5 Install Docker and Docker Compose](#95-install-docker-and-docker-compose)
  - [9.6 Allow Your User to Run Docker Without `sudo`](#96-allow-your-user-to-run-docker-without-sudo)
  - [9.7 First Docker Test](#97-first-docker-test)
  - [9.8 Basic Linux Commands for Deployments](#98-basic-linux-commands-for-deployments)
  - [9.9 Firewall Basics with UFW](#99-firewall-basics-with-ufw)
  - [9.10 Create the Server Structure](#910-create-the-server-structure)
  - [9.11 Vite + React Dockerfile](#911-vite--react-dockerfile)
  - [9.12 Next.js Dockerfile](#912-nextjs-dockerfile)
  - [9.13 `.dockerignore`](#913-dockerignore)
  - [9.14 Traefik + Cloudflare Origin Certificate + Three Websites](#914-traefik--cloudflare-origin-certificate--three-websites)
  - [9.15 Understand the Important Traefik Lines](#915-understand-the-important-traefik-lines)
  - [9.16 Why the Three Websites Are Different](#916-why-the-three-websites-are-different)
  - [9.17 DNS Setup](#917-dns-setup)
  - [9.18 First Deployment](#918-first-deployment)
  - [9.19 Useful Deployment Commands](#919-useful-deployment-commands)
  - [9.20 Update Only One Website](#920-update-only-one-website)
  - [9.21 Docker Disk Cleanup](#921-docker-disk-cleanup)
  - [9.22 Fail2ban Basic Configuration](#922-fail2ban-basic-configuration)
  - [9.23 Basic SSH Hardening](#923-basic-ssh-hardening)
  - [9.24 Troubleshooting](#924-troubleshooting)
  - [9.25 Final Production Checklist](#925-final-production-checklist)
- [10. Deployment](#10-deployment)
  - [10.1 Google Search Console](#101-google-search-console)
  - [10.2 Cloudflare Pages](#102-cloudflare-pages)
  - [10.3 Cloudflare Domains & Rules](#103-cloudflare-domains--rules)
  - [10.4 Vite + Next.js + Cloudflare Protection & Free SSL](#104-vite--nextjs--cloudflare-protection--free-ssl)
  - [10.5 Pointing the Client's Domain (Astro)](#105-pointing-the-clients-domain-astro)
  - [10.6 Pointing the Client's Domain (Vite + Next.js)](#106-pointing-the-clients-domain-vite--nextjs)
- [11. Git and GitHub](#11-git-and-github)
  - [11.1 Initial Setup (First-Time Project)](#111-initial-setup-first-time-project)
  - [11.2 Daily Workflow](#112-daily-workflow)
  - [11.3 Branching](#113-branching)
  - [11.4 Other Useful Commands](#114-other-useful-commands)
  - [11.5 Undoing Things: `reset`, `restore`, `revert`](#115-undoing-things-reset-restore-revert)
  - [11.6 `rebase` vs `merge`](#116-rebase-vs-merge)
  - [11.7 Force Push and Other Dangerous Commands](#117-force-push-and-other-dangerous-commands)
  - [11.8 Real Branching Flow: Feature Branch → Main](#118-real-branching-flow-feature-branch--main)
  - [11.9 GitHub Actions: CI/CD Workflows](#119-github-actions-cicd-workflows)
- [12. Common HTTP Status Codes](#12-common-http-status-codes)
## 1. Required Programs

| Program | Purpose | Link |
|---|---|---|
| Node.js | Required JavaScript runtime for local development, builds, Astro, Vite and Next.js | [nodejs.org/en/download](https://nodejs.org/en/download) |
| pnpm | Fast, disk-efficient package manager | [pnpm.io/installation](https://pnpm.io/installation) |

Install Node.js first, then pnpm.

---

## 2. VS Code

### 2.1 Extensions

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

### 2.2 Keyboard Shortcuts

**General**

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

**Editing**

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

**Navigation**

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

## 3. Shared Website Setup

These steps are identical in spirit across **Astro**, **Vite** and **Next.js** — Tailwind, Open Graph, `robots.txt`, sitemaps, the 404 page, Prettier, ESLint, and the Windows/npm recovery steps. Each subsection gives the shared idea once, then a short **Astro / Vite / Next.js** breakdown for what changes between them. Framework-specific scaffolding, routing and project structure live in their own sections: [4. Astro](#4-astro), [5. Vite](#5-vite), [6. Next.js](#6-nextjs).

### 3.1 Tailwind CSS Setup

All three projects use Tailwind CSS v4:

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

**Vite** — register the plugin directly in `vite.config.ts` (see [5.3](#53-viteconfigts-reference) for the full file):

```typescript
import { defineConfig } from 'vite';
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [tailwindcss()],
});
```

**Next.js** — `pnpm create next-app@latest` asks `Tailwind CSS: Yes` and wires everything (PostCSS config included) automatically. Nothing else to install; just start writing Tailwind classes and import the global stylesheet from `app/layout.tsx`.

### 3.2 Tailwind Theme & Custom Fonts

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

**Astro** — additionally ships smooth page-crossfade CSS tied to its built-in client-side router (see [4.3](#43-routing--client-side-navigation)):

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

### 3.3 Open Graph & Metadata

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

In Astro this lives in the `<head>` of `src/layouts/Layout.astro` (see [4.4](#44-main-layout-example)); in Vite it lives in `index.html`.

**Next.js** — use the Metadata API instead of hand-written tags (see [6.5](#65-root-layout) for the full example):

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

### 3.4 JSON-LD Structured Data (schema.org)

A `<script type="application/ld+json">` block describing the page as machine-readable data — search engines use it for rich results (sitelinks, knowledge panels) without changing anything visible on the page. Keep the object minimal and truthful; Google ignores or penalizes structured data that doesn't match the visible content. The simplest, safest `@type` for a homepage is `WebSite`.

**Astro** — build it in the frontmatter of the shared layout, next to the Open Graph tags from [3.3](#33-open-graph--metadata):

```astro
---
// src/layouts/Layout.astro
const structuredData = {
  "@context": "https://schema.org",
  "@type": "WebSite",
  name: "My Site",
  url: "https://mysite.com",
  description: "A short description of what this site does.",
};
---
<head>
  <!-- ...other tags... -->
  <script type="application/ld+json" set:html={JSON.stringify(structuredData)} />
</head>
```

**Vite + React** — there's no per-request template to inject into, so it goes straight into the static `index.html`:

```html
<!-- index.html -->
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "WebSite",
    "name": "My Site",
    "url": "https://mysite.com",
    "description": "A short description of what this site does."
  }
</script>
```

**Next.js** — in the root layout, using `dangerouslySetInnerHTML` (the same escape hatch `next/script` itself uses internally for inline JSON):

```tsx
// app/layout.tsx
export default function RootLayout({ children }: { children: React.ReactNode }) {
  const structuredData = {
    "@context": "https://schema.org",
    "@type": "WebSite",
    name: "My Site",
    url: "https://mysite.com",
    description: "A short description of what this site does.",
  };

  return (
    <html lang="en">
      <head>
        <script
          type="application/ld+json"
          dangerouslySetInnerHTML={{ __html: JSON.stringify(structuredData) }}
        />
      </head>
      <body>{children}</body>
    </html>
  );
}
```

Common `@type` values beyond a plain website:

| `@type` | Use case |
|---|---|
| `WebSite` | Generic website or homepage — the default, safest choice |
| `Organization` | The company/brand itself (logo, social links, contact info) |
| `SoftwareApplication` | An installable app (web app, mobile app store listing) |
| `Article` / `BlogPosting` | An individual blog post or news article |
| `Product` | A product page (price, availability, reviews) |
| `LocalBusiness` | A physical business with an address and opening hours |
| `BreadcrumbList` | The breadcrumb trail shown on a page |
| `FAQPage` | A page laid out as question/answer pairs |

Properties worth adding to the `WebSite` object above, beyond the four shown:

| Property | Description |
|---|---|
| `inLanguage` | BCP 47 language tag, e.g. `"en"` or `"es-ES"` |
| `publisher` | Nested `Organization` object naming who publishes the site |
| `sameAs` | Array of URLs to the same entity's social profiles (LinkedIn, X, GitHub…) |
| `potentialAction` | A nested `SearchAction` — enables Google's sitelinks search box if the site has an internal search page |

Validate with Google's [Rich Results Test](https://search.google.com/test/rich-results) — paste the live URL and confirm the `WebSite` type is detected with no errors.

### 3.5 Progressive Web App (PWA) Setup

A PWA needs three things: a **Web App Manifest** (JSON describing the app's name, icons, and colors so it can be installed), a **service worker** (enables offline support and caching), and **HTTPS** in production (required for service workers to register at all).

Astro and Vite each have an official-adjacent, actively-maintained plugin that generates both the manifest and the service worker (via [Workbox](https://developer.chrome.com/docs/workbox) under the hood) from one config block. **Next.js has no equivalent plugin** — not even a de-facto standard one: the long-popular `next-pwa` is unmaintained, and its actively-maintained fork `@ducanh2912/next-pwa` now recommends migrating away from itself. Next.js's own official guide ([nextjs.org/docs/app/guides/progressive-web-apps](https://nextjs.org/docs/app/guides/progressive-web-apps)) instead documents a manual approach: the manifest through Next's built-in Manifest API (no plugin needed for that part), and a hand-written service worker for anything beyond basic installability. If full offline caching is worth the extra dependency, that same official guide points to [Serwist](https://github.com/serwist/serwist) as the maintained option, with first-party examples for both Turbopack and webpack.

| Framework | Approach | Generates |
|---|---|---|
| Astro | Plugin: [`@vite-pwa/astro`](https://vite-pwa-org.netlify.app/frameworks/astro) | manifest + service worker + auto `<link rel="manifest">` |
| Vite + React | Plugin: [`vite-plugin-pwa`](https://vite-pwa-org.netlify.app/) | manifest + service worker + auto `<link rel="manifest">` |
| Next.js | Official, manual (per Next's own guide) | manifest via `app/manifest.ts` (built-in); service worker hand-written |

```bash
# Astro
pnpm add -D @vite-pwa/astro

# Vite + React
pnpm add -D vite-plugin-pwa

# Next.js — no plugin needed for the manifest (built-in); see below for the
# service worker, or `pnpm add @serwist/next serwist` if you want full offline caching
```

**Astro** (`astro.config.mjs`):

```javascript
import { defineConfig } from "astro/config";
import AstroPWA from "@vite-pwa/astro";

export default defineConfig({
  integrations: [
    AstroPWA({
      registerType: "autoUpdate",
      manifest: {
        name: "My Site",
        short_name: "MySite",
        description: "A short description of what this site does.",
        theme_color: "#0f172a",
        background_color: "#0f172a",
        display: "standalone",
        icons: [
          { src: "/pwa-192x192.png", sizes: "192x192", type: "image/png" },
          { src: "/pwa-512x512.png", sizes: "512x512", type: "image/png" },
        ],
      },
    }),
  ],
});
```

**Vite + React** (`vite.config.ts`) — same `manifest` shape, added to the existing plugins array:

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import { VitePWA } from "vite-plugin-pwa";

export default defineConfig({
  plugins: [
    react(),
    VitePWA({
      registerType: "autoUpdate",
      manifest: {
        name: "My Site",
        short_name: "MySite",
        description: "A short description of what this site does.",
        theme_color: "#0f172a",
        background_color: "#0f172a",
        display: "standalone",
        icons: [
          { src: "/pwa-192x192.png", sizes: "192x192", type: "image/png" },
          { src: "/pwa-512x512.png", sizes: "512x512", type: "image/png" },
        ],
      },
    }),
  ],
});
```

**Next.js** — the manifest uses Next's built-in, typed Manifest API (this part genuinely is official, no plugin involved):

```typescript
// app/manifest.ts
import type { MetadataRoute } from "next";

export default function manifest(): MetadataRoute.Manifest {
  return {
    name: "My Site",
    short_name: "MySite",
    description: "A short description of what this site does.",
    start_url: "/",
    theme_color: "#0f172a",
    background_color: "#0f172a",
    display: "standalone",
    icons: [
      { src: "/pwa-192x192.png", sizes: "192x192", type: "image/png" },
      { src: "/pwa-512x512.png", sizes: "512x512", type: "image/png" },
    ],
  };
}
```

For the service worker, Next's official guide has you write a small one by hand and register it yourself — there's no build step generating it:

```javascript
// public/sw.js
self.addEventListener("install", () => self.skipWaiting());
self.addEventListener("activate", () => self.clients.claim());
// Add fetch/cache-strategy or push-notification handlers here as needed.
```

```tsx
// app/register-sw.tsx
"use client";
import { useEffect } from "react";

export function RegisterServiceWorker() {
  useEffect(() => {
    if ("serviceWorker" in navigator) {
      navigator.serviceWorker.register("/sw.js");
    }
  }, []);
  return null;
}
```

```tsx
// app/layout.tsx
import { RegisterServiceWorker } from "./register-sw";

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body>
        <RegisterServiceWorker />
        {children}
      </body>
    </html>
  );
}
```

A manifest plus HTTPS is already enough for the browser's install prompt to show up — the service worker above only starts to matter once you want offline caching or push notifications. If that's the goal, swap the hand-written `sw.js` for [Serwist](https://github.com/serwist/serwist) instead of maintaining Workbox-equivalent caching logic by hand.

Manifest properties worth knowing:

| Property | Description |
|---|---|
| `name` | Full app name, shown on the install prompt |
| `short_name` | Short name shown under the icon once installed |
| `start_url` | Page opened when launched from the home screen (defaults to `/`) |
| `display` | `standalone` hides the browser UI (most common); also `fullscreen`, `minimal-ui`, `browser` |
| `theme_color` | Color of the OS status bar / title bar |
| `background_color` | Splash screen background shown while the app loads |
| `icons` | Icon files at multiple sizes — at minimum, 192×192 and 512×512 PNGs |

Both icon files (`pwa-192x192.png`, `pwa-512x512.png`) live in `public/` for Astro and Vite, referenced by path in the `manifest` object above — see the updated project structures in [4.5](#45-project-structure--architecture), [5.6](#56-project-structure--architecture) and [6.8](#68-project-structure--architecture).

Service workers generally aren't worth testing against the dev server — test against the production build instead:

```bash
pnpm build
pnpm preview
```

Then check **Chrome DevTools → Application tab** (Manifest / Service Workers sections) and run a Lighthouse PWA audit — both confirm the manifest is valid and the service worker is controlling the page.

### 3.6 `robots.txt`

`robots.txt` is framework-independent — a static file that tells search engine crawlers what they can access and points them to the sitemap. The final URL is always `https://mysite.com/robots.txt`.

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

### 3.7 Sitemap Integration

A sitemap is useful for SEO and should be submitted to Google Search Console (see [10.1](#101-google-search-console)). The mechanism differs per framework:

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

### 3.8 404 / Not Found Page

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

**Vite** — with React Router, a catch-all route is enough (see [5.4](#54-routing--layouts-react-router-dom)):

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

### 3.9 Prettier Setup

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

### 3.10 ESLint Setup

Install ESLint and add the `lint` script to `package.json`:

```json
"lint": "eslint ."
```

**Vite / React** — install the full set (TypeScript rules + React-specific plugins):

```bash
pnpm add -D eslint @eslint/js typescript-eslint globals eslint-plugin-react-hooks eslint-plugin-react-refresh
```

`eslint.config.mjs`:

```javascript
import js from "@eslint/js";
import globals from "globals";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";
import tseslint from "typescript-eslint";
import { defineConfig, globalIgnores } from "eslint/config";

export default defineConfig([
  globalIgnores(["dist", "node_modules/**"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      js.configs.recommended,
      tseslint.configs.recommended,
      reactHooks.configs.flat.recommended,
      reactRefresh.configs.vite,
    ],
    languageOptions: {
      globals: globals.browser,
    },
    rules: {
      "@typescript-eslint/no-namespace": "off",
      "@typescript-eslint/no-explicit-any": "error",
      "@typescript-eslint/no-unused-vars": [
        "error",
        {
          argsIgnorePattern: "^_",
          caughtErrorsIgnorePattern: "^_",
          varsIgnorePattern: "^_",
        },
      ],
    },
  },
]);
```

`reactHooks.configs.flat.recommended` catches invalid Hook usage (calling a Hook conditionally, outside a component, etc. — see [React's Rules of Hooks](https://react.dev/reference/rules/rules-of-hooks)); `reactRefresh.configs.vite` warns when a file mixes component and non-component exports in a way that breaks Vite's Fast Refresh ([5](#5-vite)). `no-explicit-any` and `no-unused-vars` (with an `_`-prefix escape hatch for intentionally unused args/vars) apply across every framework in this section — they're the two rules most worth keeping as errors rather than warnings.

**Node.js backend** (Express + Prisma, [7](#7-database--backend-prisma--postgresql)) — same TypeScript rules, without the React-specific plugins:

```bash
pnpm add -D eslint @eslint/js typescript-eslint
```

`eslint.config.mjs`:

```javascript
import js from "@eslint/js";
import tseslint from "typescript-eslint";
import { defineConfig, globalIgnores } from "eslint/config";

export default defineConfig([
  globalIgnores(["dist/**", "node_modules/**"]),
  {
    files: ["**/*.ts"],
    extends: [js.configs.recommended, tseslint.configs.recommended],
    rules: {
      "@typescript-eslint/no-namespace": "off",
      "@typescript-eslint/no-explicit-any": "error",
      "@typescript-eslint/no-unused-vars": [
        "error",
        {
          argsIgnorePattern: "^_",
          caughtErrorsIgnorePattern: "^_",
          varsIgnorePattern: "^_",
        },
      ],
    },
  },
]);
```

No `languageOptions.globals` here — there's no browser code to account for, and Node's own globals (`process`, `__dirname`, etc.) are already covered by `@types/node` at the TypeScript level, not by ESLint's global-variable checking.

**Astro** — adds `eslint-plugin-astro` on top of the base TypeScript config, to lint the script portions of `.astro` files:

```bash
pnpm add -D eslint @eslint/js typescript-eslint globals eslint-plugin-astro
```

`eslint.config.mjs`:

```javascript
import js from "@eslint/js";
import globals from "globals";
import tseslint from "typescript-eslint";
import eslintPluginAstro from "eslint-plugin-astro";
import { defineConfig, globalIgnores } from "eslint/config";

export default defineConfig([
  globalIgnores(["dist/**", ".astro/**", "node_modules/**"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [js.configs.recommended, tseslint.configs.recommended],
    languageOptions: {
      globals: globals.browser,
    },
    rules: {
      "@typescript-eslint/no-namespace": "off",
      "@typescript-eslint/no-explicit-any": "error",
      "@typescript-eslint/no-unused-vars": [
        "error",
        {
          argsIgnorePattern: "^_",
          caughtErrorsIgnorePattern: "^_",
          varsIgnorePattern: "^_",
        },
      ],
    },
  },
  ...eslintPluginAstro.configs.recommended,
]);
```

`eslintPluginAstro.configs.recommended` is spread at the end (rather than listed inside one object's `extends`) because it's an array of several config objects — Astro's own flat-config plugin ships it this way so it can attach its parser specifically to `**/*.astro` files without interfering with the plain `.ts`/`.tsx` block above it.

Across all three: `pnpm run lint` reports the errors, `pnpm run lint --fix` auto-fixes what it safely can (mainly formatting-adjacent issues — most real style formatting is Prettier's job, [3.9](#39-prettier-setup), not ESLint's).

### 3.11 Windows PowerShell Execution Policy / npm Recovery

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

### 3.12 Development Server

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

### 3.13 `.env` Example

Environment variables keep secrets (API keys, database URLs, tokens) out of the codebase. The `.env` file is never committed — it's excluded via [`.gitignore`](#314-gitignore-example) — only `.env.example` (with placeholder values, no real secrets) gets committed as a reference for other developers.

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

### 3.14 `.gitignore` Example

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

> `.env` is deliberately ignored while `.env.example` is not — commit `.env.example` with placeholder values so the pattern from [3.13](#313-env-example) is documented for anyone who clones the repo. `!.vscode/extensions.json` is a negation pattern: it re-includes that one file even though `.vscode/*` ignores the folder, which is handy for sharing the extension list from [2.1 Extensions](#21-extensions) with the team.

---

## 4. Astro

> **Deployment note:** Astro is included as a development reference, but it is not part of the Docker/server setup in section 9. Astro sites are deployed directly to Cloudflare Pages (see [10.2](#102-cloudflare-pages)).

### 4.1 Project Setup

```bash
pnpm create astro@latest
```

The Tailwind CSS setup that follows scaffolding is covered in [3.1](#31-tailwind-css-setup); sitemap in [3.7](#37-sitemap-integration).

### 4.2 Install Dependencies

The Astro CLI installs dependencies as part of scaffolding. If they ever need reinstalling (e.g. after cloning the repo):

```bash
pnpm install
```

### 4.3 Routing & Client-Side Navigation

Astro uses **file-based routing**: every file in `src/pages/` becomes a route (see [4.5](#45-project-structure--architecture) for the full mapping).

Astro's built-in `ClientRouter` enables View Transitions for smooth navigation between pages without full reloads — no router library needed. It's imported once in the shared layout (see [4.4](#44-main-layout-example)) and paired with the CSS crossfade from [3.2](#32-tailwind-theme--custom-fonts).

```astro
---
import { ClientRouter } from "astro:transitions";
---
<head>
  <ClientRouter />
</head>
```

### 4.4 Main Layout Example

`src/layouts/Layout.astro` is the shared HTML shell: head, meta tags, Open Graph (see [3.3](#33-open-graph--metadata)), `<Navbar />` / `<Footer />`, and `<slot />` for page content — the Astro equivalent of Vite's layout route ([5.5](#55-layout-route-with-outlet)) or Next.js's root layout ([6.5](#65-root-layout)).

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

### 4.5 Project Structure & Architecture

```
/
├── .github/
│   └── workflows/
│       ├── audit.yml
│       └── prettier.yml
├── public/
│   ├── favicon.svg
│   ├── icon.png
│   ├── pwa-192x192.png
│   ├── pwa-512x512.png
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

**`.github/workflows/`** — CI checks that run on every push ([11.9](#119-github-actions-cicd-workflows)): `audit.yml` and `prettier.yml`. No `deploy.yml` here — this site deploys via Cloudflare Pages ([8.6](#86-each-frontend-as-its-own-repo-cloudflare-pages)), which redeploys automatically on push; `deploy.yml` only applies to the backend repo ([8.9](#89-final-project-structure-three-independent-repos)).

**`public/`** — Static assets served as-is, without processing. Anything here is copied directly to the final build output at the same path (favicon, images, `robots.txt` — see [3.6](#36-robotstxt) — and the PWA icons from [3.5](#35-progressive-web-app-pwa-setup)).

**`src/components/`** — Reusable UI pieces used across multiple pages (e.g. `Hero.astro`, `Navbar.astro`, `Footer.astro`). Each component encapsulates its own markup, styles, and logic.

**`src/layouts/`** — Page wrappers that define the shared HTML shell (see [4.4](#44-main-layout-example)). Most projects only need one `Layout.astro`, but additional layouts can be added for different page types (e.g. a blog post layout).

**`src/pages/`** — File-based routing: each file becomes a route.

- `index.astro` → homepage (`/`)
- `terms-of-service.astro` → `/terms-of-service`
- `privacy-policy.astro` → `/privacy-policy`
- `contact.astro` → `/contact`
- `404.astro` → custom not-found page (see [3.8](#38-404--not-found-page))

**`src/styles/`** — Global stylesheets. `global.css` is where Tailwind is imported (see [3.1](#31-tailwind-css-setup)) and where fonts/theme tokens live (see [3.2](#32-tailwind-theme--custom-fonts)).

---

## 5. Vite

### 5.1 Scaffolding a New Project

```bash
pnpm create vite@latest project-name --template react-ts
cd project-name
```

### 5.2 Install Dependencies

```bash
pnpm install
```

The Tailwind CSS setup that follows is covered in [3.1](#31-tailwind-css-setup); sitemap in [3.7](#37-sitemap-integration).

### 5.3 `vite.config.ts` Reference

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

### 5.4 Routing & Layouts (React Router DOM)

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

### 5.5 Layout Route with `Outlet`

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

### 5.6 Project Structure & Architecture

```
/
├── .github/
│   └── workflows/
│       ├── audit.yml
│       └── prettier.yml
├── public/
│   ├── favicon.svg
│   ├── icon.png
│   ├── pwa-192x192.png
│   ├── pwa-512x512.png
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

**`.github/workflows/`** — Same as Astro's ([4.5](#45-project-structure--architecture)): `audit.yml` and `prettier.yml`, no `deploy.yml` (Cloudflare Pages autodeploys this site — [8.6](#86-each-frontend-as-its-own-repo-cloudflare-pages)).

**`public/`** — Static assets served as-is; same role as described in [3.6 `robots.txt`](#36-robotstxt), plus the PWA icons from [3.5](#35-progressive-web-app-pwa-setup).

**`src/components/`** — Reusable UI pieces (`Hero.tsx`, `Navbar.tsx`, `Footer.tsx`) shared across pages.

**`src/layouts/`** — Shared page shells rendered via a layout route with `<Outlet />` (see [5.5](#55-layout-route-with-outlet)), equivalent to Astro's `Layout.astro` or Next.js's root layout.

**`src/pages/`** — One component per route, registered manually in `App.tsx` when using React Router:

- `Home.tsx` → `/`
- `About.tsx` → `/about`
- `Contact.tsx` → `/contact`
- `TermsOfService.tsx` → `/terms-of-service`
- `PrivacyPolicy.tsx` → `/privacy-policy`
- `NotFound.tsx` → catch-all `*` route

**`src/global.css`** (or `index.css`) — Where Tailwind is imported and font/theme tokens are defined (see [3.2](#32-tailwind-theme--custom-fonts)).

**`index.html`** — The single HTML entry point; holds the `<head>` meta tags and Open Graph tags (see [3.3](#33-open-graph--metadata)), and the `#root` mount point for React.

---

## 6. Next.js

Next.js is the third framework covered here. Unlike a static Astro or Vite build, a standard Next.js application runs a Node.js server in production (see [6.7](#67-production-build)).

### 6.1 Create a New Project

```bash
pnpm create next-app@latest my-next-site
cd my-next-site
```

A typical setup for this README is:

- TypeScript: `Yes`
- ESLint: `Yes`
- Tailwind CSS: `Yes`
- App Router: `Yes`

### 6.2 Install Dependencies

`create-next-app` installs dependencies as part of scaffolding. If they ever need reinstalling (e.g. after cloning the repo):

```bash
pnpm install
```

### 6.3 `next.config.ts` Reference

Basic version — an empty config is valid since Tailwind is already wired in through PostCSS by `create-next-app` (see [3.1](#31-tailwind-css-setup)):

```typescript
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {}

export default nextConfig
```

Extended version, enabling the [React Compiler](https://react.dev/learn/react-compiler) and typed routes — the Next.js equivalent of Vite's extended `vite.config.ts` in [5.3](#53-viteconfigts-reference):

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

### 6.4 Routing & Layouts (App Router)

Like Astro, Next.js uses **file-based routing** — no router library needed, unlike Vite's `react-router-dom` ([5.4](#54-routing--layouts-react-router-dom)). Every folder under `app/` maps to a URL segment, and a `page.tsx` inside it is what actually renders:

```text
app/page.tsx            → /
app/about/page.tsx      → /about
app/contact/page.tsx    → /contact
app/not-found.tsx       → custom 404 (see 3.8)
```

Layouts nest automatically: any `layout.tsx` wraps every route below it, so the shared shell (navbar + footer) only needs to be defined once at the root — see [6.5](#65-root-layout) for the equivalent of Astro's `<slot />` or Vite's `<Outlet />`. Nested folders can add their own `layout.tsx` to wrap just that subsection of the site (e.g. a `blog/layout.tsx` shared by every post).

### 6.5 Root Layout

`app/layout.tsx` is the shared HTML shell — the Next.js equivalent of Astro's `Layout.astro` ([4.4](#44-main-layout-example)) or Vite's `MainLayout.tsx` + `<Outlet />` ([5.5](#55-layout-route-with-outlet)). Instead of `<slot />` or `<Outlet />`, it receives page content as the `children` prop:

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

The Metadata API above is the Next.js equivalent of the hand-written Open Graph `<meta>` tags used in Astro/Vite (see [3.3](#33-open-graph--metadata)).

### 6.6 Server and Client Components

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

### 6.7 Production Build

```bash
pnpm build
pnpm start
```

`pnpm build` creates the optimized production output. `pnpm start` runs the production Next.js server, normally on port `3000`.

For the Docker deployment in [section 9](#9-linux-server--docker-deployment):

- A normal Next.js application should run `next start`.
- Do not treat a normal Next.js application as a `dist/` static site.
- The Next.js container listens internally on port `3000`.
- Traefik forwards HTTPS traffic to that internal port.

> Next.js can also be configured for static export, but that is a different deployment model. This README treats Next.js as a normal Node.js application running in Docker.

### 6.8 Project Structure & Architecture

```
/
├── .github/
│   └── workflows/
│       ├── audit.yml
│       └── prettier.yml
├── public/
│   ├── favicon.ico
│   ├── pwa-192x192.png
│   ├── pwa-512x512.png
│   ├── images/
│   └── robots.txt
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   ├── not-found.tsx
│   ├── sitemap.ts
│   ├── manifest.ts
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

**`.github/workflows/`** — Same as Astro's ([4.5](#45-project-structure--architecture)): `audit.yml` and `prettier.yml`, no `deploy.yml` (Cloudflare Pages autodeploys this site — [8.6](#86-each-frontend-as-its-own-repo-cloudflare-pages)).

**`public/`** — Static assets served as-is; same role as described in [3.6 `robots.txt`](#36-robotstxt). Next.js's PWA manifest is `app/manifest.ts`, not a static file here — see [3.5](#35-progressive-web-app-pwa-setup).

**`app/`** — File-based routing (see [6.4](#64-routing--layouts-app-router)). `app/page.tsx` is the homepage, `app/layout.tsx` is the root layout (see [6.5](#65-root-layout)), `app/not-found.tsx` handles 404 pages (see [3.8](#38-404--not-found-page)), `app/sitemap.ts` generates the sitemap (see [3.7](#37-sitemap-integration)), and `app/manifest.ts` generates the PWA manifest (see [3.5](#35-progressive-web-app-pwa-setup)). Each subfolder with its own `page.tsx` becomes a route, equivalent to a file under Astro's `src/pages/` or a route entry in Vite's `App.tsx`.

**`components/`** — Reusable UI pieces (`Navbar.tsx`, `Footer.tsx`) shared across pages, equivalent to `src/components/` in Astro or Vite.

**`lib/`** — Shared utilities, helpers, and non-component logic (data fetching, formatting, etc.).

---

## 7. Database & Backend: Prisma + PostgreSQL

Stack: **Express + TypeScript + Prisma + PostgreSQL (Docker)**. This section covers setting up that backend from zero — schema, migrations, `.env`, a minimal login endpoint, and a seed script.

### 7.1 Overview: Which Framework Needs a Separate Backend

Between the frameworks in this README, only **Vite + React** and **Next.js** ever talk to a database.

| Framework | Where the backend lives | Needs a separate backend? |
|---|---|---|
| **Next.js** | Directly inside API Routes / Route Handlers / Server Actions | No — Next.js *is* the backend |
| **Vite + React** | Never in the frontend bundle | **Yes** — Vite is a pure client-side SPA, so it needs a standalone Node/Express API server that the React app calls over `fetch` |

Everything below builds that standalone Express + Prisma backend, called over `fetch` by one or more Vite frontends (or adapted into a Next.js project's own Route Handlers). See [8. Full Separation: Independent Backend, Frontend(s) and Deployment](#8-full-separation-independent-backend-frontends-and-deployment) for deploying it fully on its own, with each frontend in its own repo.

### 7.2 Backend Project Structure

```
backend/
├── .github/
│   └── workflows/
│       ├── audit.yml
│       ├── deploy.yml
│       └── prettier.yml
├── prisma/
│   ├── migrations/
│   ├── schema.prisma
│   └── seed.ts
├── src/
│   └── index.ts
├── .dockerignore
├── .env               (never committed)
├── .gitignore
├── docker-compose.yml
├── Dockerfile
├── package.json
├── pnpm-workspace.yaml
├── prisma.config.ts
└── tsconfig.json
```

`deploy.yml` only makes sense here — it's the only repo that deploys by SSH to a VPS ([8.3](#83-backend-dockerfile-pnpm-node-24-multi-stage)); `audit.yml` and `prettier.yml` are the same generic checks used in the frontends ([11.9](#119-github-actions-cicd-workflows)).

This backend is its own repository, not a monorepo package — `docker-compose.yml` and `Dockerfile` ship with it, since it deploys on its own to a VPS (see [8](#8-full-separation-independent-backend-frontends-and-deployment)).

### 7.3 Install Dependencies

```bash
pnpm install
```

**Production dependencies:**

- `@prisma/client` — the generated Prisma client
- `@prisma/adapter-pg` — Prisma's driver adapter for PostgreSQL, used together with `pg` instead of connecting through the older built-in engine
- `pg` — the actual PostgreSQL driver
- `express`, `cors`, `dotenv` — HTTP server, cross-origin requests, environment variables
- `bcrypt` — password hashing
- `cookie-parser` — reads the session cookie on incoming requests

**Development dependencies:**

- `prisma` — the Prisma CLI (`pnpm exec prisma ...`)
- `tsx` — runs TypeScript directly, with `--watch` for hot reload in dev
- `typescript` and the matching `@types/*` packages — **must be listed explicitly** here; a monorepo can hide this behind one root-level `typescript`, but a standalone repo without it fails with `tsc: not found` on build.

```json
{
  "name": "backend",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "docker compose up -d postgres && prisma generate && prisma db push && tsx watch src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js",
    "db:seed": "prisma db seed"
  },
  "dependencies": {
    "@prisma/adapter-pg": "^7.10.0",
    "@prisma/client": "^7.10.0",
    "bcrypt": "^6.0.0",
    "cookie-parser": "^1.4.7",
    "cors": "^2.8.6",
    "dotenv": "^17.4.2",
    "express": "^5.2.1",
    "pg": "^8.23.0"
  },
  "devDependencies": {
    "@types/bcrypt": "^6.0.0",
    "@types/cookie-parser": "^1.4.10",
    "@types/cors": "^2.8.19",
    "@types/express": "^5.0.6",
    "@types/node": "^25.9.5",
    "@types/pg": "^8.23.1",
    "prisma": "^7.10.0",
    "tsx": "^4.23.13",
    "typescript": "^6.0.3"
  }
}
```

`dev` starts the local Postgres container ([8.2](#82-backend-repo-docker-composeyml-postgres-and-api)), regenerates the client, pushes the schema, and starts the server watching for changes — one command instead of four.

### 7.4 `.env` Example

```env
# .env — never commit this file

DB_PASSWORD=change-this

# Only used if you run the backend outside docker-compose (e.g. local pnpm dev);
# must match DB_PASSWORD above.
DATABASE_URL="postgresql://postgres:change-this@localhost:5432/mydb?schema=public"

PORT=3001
NODE_ENV=development

ADMIN_USERNAME=admin
ADMIN_PASSWORD=change-this-too

# Comma-separated, no spaces, exact frontend origins (with https://, no trailing slash).
ALLOWED_ORIGINS=http://localhost:5173
```

> Add `.env` to `.gitignore` ([3.14](#314-gitignore-example)) — never commit it.

### 7.5 Configuration Files: `tsconfig.json`, `prisma.config.ts` and `pnpm-workspace.yaml`

```json
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2025",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src/**/*"]
}
```

`target` controls which JS syntax is emitted; `module`/`moduleResolution` set to `NodeNext` follow Node's own rules for CommonJS vs ESM based on whether `package.json` has `"type": "module"` — since this `package.json` doesn't, `tsc` compiles to CommonJS, matching `node dist/index.js` in the `start` script.

```typescript
// prisma.config.ts
import "dotenv/config";
import { defineConfig, env } from "prisma/config";

export default defineConfig({
  schema: "prisma/schema.prisma",
  migrations: {
    path: "prisma/migrations",
    seed: "tsx prisma/seed.ts",
  },
  datasource: {
    url: env("DATABASE_URL"),
  },
});
```

`prisma.config.ts` is the Prisma CLI's config file: it tells `prisma migrate`/`studio`/`db seed` where the schema and migrations live, which seed script to run ([7.12](#712-seed-example)), and which connection string to use. Since it reads `DATABASE_URL` from the environment, **any command touching this file — `prisma generate` included — needs `DATABASE_URL` set**, even just to generate the client with no real database yet. This matters most inside a Docker build stage, where `.env` isn't loaded automatically ([8.3](#83-backend-dockerfile-pnpm-node-24-multi-stage)):

```bash
DATABASE_URL="postgresql://user:pass@localhost:5432/db" pnpm exec prisma generate
```

Any placeholder connection string works here — `generate` only reads the schema, it never actually connects.

```yaml
# pnpm-workspace.yaml
allowBuilds:
  '@prisma/engines': true
  bcrypt: true
  esbuild: true
  prisma: true
```

Since pnpm 10, `pnpm install` **ignores lifecycle/build scripts by default** for supply-chain safety — packages that ship native binaries or run `postinstall` (Prisma's engines, `bcrypt`'s native bindings, `esbuild`) silently fail to finish setting up, and pnpm prints `[ERR_PNPM_IGNORED_BUILDS]`. `allowBuilds` explicitly trusts these packages to run their install scripts. It's required even for a single, non-monorepo package — `pnpm-workspace.yaml` is just where pnpm looks for this setting either way.

### 7.6 PostgreSQL: Starting the Database

For working on the backend in isolation, without even a `docker-compose.yml` yet:

```bash
docker run --name backend-postgres \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=root \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  -v postgres_data:/var/lib/postgresql \
  -d postgres:18
```

In practice this is quickly replaced by the backend's own `docker-compose.yml` ([8.2](#82-backend-repo-docker-composeyml-postgres-and-api)): `docker compose up -d postgres` (used by the `dev` script in [7.3](#73-install-dependencies)) or `docker compose up -d --build` (full stack, production) replace the manual `docker run` above.

### 7.7 Prisma From Scratch: Default `schema.prisma`

```bash
pnpm dlx prisma init
```

This scaffolds `prisma/schema.prisma` with nothing but the two required blocks — no models yet:

```prisma
// This is your Prisma schema file,
// learn more about it in the docs: https://pris.ly/d/prisma-schema

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

It also creates a placeholder `.env` — replace its `DATABASE_URL` with the real one from [7.4](#74-env-example).

### 7.8 Add a Simple `User` Model

```prisma
model User {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  password  String
  createdAt DateTime @default(now())
}
```

`password` here always means the **hash**, never the plain text — see the `bcrypt.hash()` call in [7.11](#711-simple-backend-entry-point-srcindexts-login-example).

### 7.9 Create and Apply the First Migration

Two different ways to push a schema change to the database, depending on the stage of the work:

```bash
pnpm exec prisma db push
```

Pushes the current `schema.prisma` straight to the database **without creating a migration file**. Fast to iterate with while a model is still changing shape often — this is what the `dev` script in [7.3](#73-install-dependencies) uses. Trade-off: no history, so it's for local development only, and switching to `migrate dev`/`migrate deploy` later requires the schema and database to already be in sync.

```bash
pnpm exec prisma migrate dev --name init
```

The versioned alternative. This:

1. Compares the schema against the current database
2. Generates the SQL in `prisma/migrations/`
3. Applies the migration
4. Regenerates the Prisma Client

Use this once a model is stable enough to commit a real migration history for it — every teammate and every environment then replays the exact same SQL.

```bash
pnpm exec prisma generate
```

Regenerates the client without migrating — needed after pulling someone else's migration, or after editing the schema without creating one.

```bash
pnpm exec prisma migrate deploy
```

Used in production/CI: applies any pending migrations from `prisma/migrations/` without prompting and without generating new ones — this is the command that belongs in a deployment script (or a Docker container's startup command, see [8.3](#83-backend-dockerfile-pnpm-node-24-multi-stage)), never `migrate dev` and never `db push`.

```bash
pnpm exec prisma migrate reset
```

⚠️ **Destructive — local/dev only, never run this in production.** Drops the entire database, recreates it from scratch, reapplies every migration in `prisma/migrations/` from the very first one, and then runs the seed script ([7.12](#712-seed-example)) automatically. Reach for this when the local database and the migration history have drifted apart and Prisma refuses to apply a new migration cleanly (`Migrations in conflict`, see [7.15](#715-common-prisma-and-postgresql-errors)) — it's the "just start over" escape hatch for a local database, not something to run against real data.

### 7.10 Modifying an Existing Schema: Update `User` and Add a New Table

This is the general case the previous step builds up to: the schema already exists and now needs to grow. Say logins should now persist a session, and `User` should have an optional name:

```prisma
model User {
  id        Int       @id @default(autoincrement())
  email     String    @unique
  password  String
  name      String?
  createdAt DateTime  @default(now())
  sessions  Session[]
}

model Session {
  id        Int      @id @default(autoincrement())
  token     String   @unique
  userId    Int
  user      User     @relation(fields: [userId], references: [id])
  expiresAt DateTime
}
```

Then either `db push` (while still iterating) or a new named migration ([7.9](#79-create-and-apply-the-first-migration)) once it's stable:

```bash
pnpm exec prisma migrate dev --name add-name-and-sessions
```

That's the general rule for growing a schema over time — it never changes: edit `schema.prisma` (add fields, add models, add relations), then push or migrate again. Prisma diffs the current database against the schema and figures out the SQL on its own; nothing needs to be written by hand.

### 7.11 Simple Backend Entry Point (`src/index.ts`): Login Example

A minimal Express server using the schema above — register is left out for brevity, but `/login` and `/me` show the full pattern: hash comparison, a `Session` row, and an `httpOnly` cookie configured for **cross-domain** use, since the frontend (Cloudflare Pages) and this API (a VPS) live on different domains in production — see [8.5](#85-cors-and-cookies-across-different-domains) for the full explanation.

```typescript
// src/index.ts
import "dotenv/config";
import express from "express";
import cors from "cors";
import bcrypt from "bcrypt";
import crypto from "crypto";
import cookieParser from "cookie-parser";
import { PrismaClient } from "@prisma/client";
import { PrismaPg } from "@prisma/adapter-pg";

const adapter = new PrismaPg({ connectionString: process.env.DATABASE_URL! });
const prisma = new PrismaClient({ adapter });

const app = express();
const IS_PRODUCTION = process.env.NODE_ENV === "production";

// Explicit origin allowlist instead of `origin: true` (which reflects any
// origin) — safer once this is reachable from the public internet.
const allowedOrigins = (process.env.ALLOWED_ORIGINS ?? "")
  .split(",")
  .map((o) => o.trim())
  .filter(Boolean);

app.use(
  cors({
    origin(origin, callback) {
      if (!origin || allowedOrigins.length === 0 || allowedOrigins.includes(origin)) {
        callback(null, true);
        return;
      }
      callback(new Error("Not allowed by CORS"));
    },
    credentials: true,
  }),
);
app.use(express.json());
app.use(cookieParser());

const PORT = process.env.PORT || 3001;
const COOKIE_NAME = "session_token";

// SameSite=None + Secure is required for the browser to send this cookie on
// cross-site requests (frontend and API on different domains); Secure means
// this only works over HTTPS, which is why the API needs a real TLS
// certificate in production ([8.7](#87-https-in-front-of-the-backend-caddy)).
// In local dev (same-origin via Vite's proxy) "lax" without Secure still works.
const cookieOptions = {
  httpOnly: true,
  secure: IS_PRODUCTION,
  sameSite: (IS_PRODUCTION ? "none" : "lax") as "none" | "lax",
};

// POST /login — checks the password and opens a session
app.post("/login", async (req, res) => {
  const { email, password } = req.body;

  const user = await prisma.user.findUnique({ where: { email } });
  const valid = user && (await bcrypt.compare(password, user.password));

  if (!valid) {
    return res.status(401).json({ error: "Invalid credentials" });
  }

  const token = crypto.randomBytes(32).toString("hex");
  const expiresAt = new Date(Date.now() + 1000 * 60 * 60 * 24); // 24h

  await prisma.session.create({ data: { token, userId: user.id, expiresAt } });

  res.cookie(COOKIE_NAME, token, { ...cookieOptions, expires: expiresAt });
  res.json({ id: user.id, email: user.email, name: user.name });
});

// GET /me — returns the logged-in user based on the session cookie
app.get("/me", async (req, res) => {
  const token = req.cookies[COOKIE_NAME];
  const session =
    token && (await prisma.session.findUnique({ where: { token }, include: { user: true } }));

  if (!session || session.expiresAt < new Date()) {
    return res.status(401).json({ error: "Not authenticated" });
  }

  res.json({ id: session.user.id, email: session.user.email, name: session.user.name });
});

app.listen(PORT, () => console.log(`API running on http://localhost:${PORT}`));
```

### 7.12 Seed Example

```typescript
// prisma/seed.ts
import "dotenv/config";
import { PrismaClient } from "@prisma/client";
import { PrismaPg } from "@prisma/adapter-pg";
import bcrypt from "bcrypt";

const adapter = new PrismaPg({ connectionString: process.env.DATABASE_URL! });
const prisma = new PrismaClient({ adapter });

async function main() {
  await prisma.user.upsert({
    where: { email: "admin@example.com" },
    update: {},
    create: {
      email: "admin@example.com",
      password: await bcrypt.hash("admin123", 10),
      name: "Admin",
    },
  });
}

main()
  .catch((e) => {
    console.error(e);
    process.exit(1);
  })
  .finally(() => prisma.$disconnect());
```

```bash
pnpm db:seed
```

No extra wiring needed — the seed command is already pointed at this file by `prisma.config.ts` ([7.5](#75-configuration-files-tsconfigjson-prismaconfigts-and-pnpm-workspaceyaml)). One easy-to-miss requirement: the Prisma Client must already be generated before seeding — on a fresh `pnpm install` (or after wiping `node_modules`), run `pnpm exec prisma generate` once before `pnpm db:seed`, or it fails with `Cannot find module '.prisma/client/default'`.

### 7.13 Prisma Studio

```bash
pnpm exec prisma studio
```

Opens a visual database browser at `http://localhost:5555` — view, create, edit and delete rows in any table without writing SQL.

### 7.14 Day-to-Day Workflow and Reference Commands

```bash
# 1. Start the database (this backend's own docker-compose.yml — see 9.2)
docker compose up -d postgres

# 2. Start the backend in dev mode (generate + push + watch, see 8.3)
pnpm dev

# --- whenever the schema changes ---

# 3a. Quick iteration, no migration history yet
pnpm exec prisma db push

# 3b. Once the model is stable, a real versioned migration
pnpm exec prisma migrate dev --name <descriptive_name>

# 4. (optional) inspect data visually
pnpm exec prisma studio

# --- end of the day ---

# 5. Stop the database
docker compose down
```

Quick reference:

```bash
# Docker
docker compose up -d postgres      # start only Postgres (local dev)
docker compose up -d --build       # build + start Postgres AND the backend (full stack, prod-style)
docker compose down                # stop everything (keeps data)
docker compose down -v             # stop + wipe all data (volume included) — needed if a stored
                                    # password stops matching .env, see 8.15
docker compose logs -f backend     # follow the backend's logs

# Prisma
pnpm exec prisma db push                # push schema, no migration file (fast local iteration)
pnpm exec prisma migrate dev --name <name>   # new versioned migration
pnpm exec prisma migrate deploy         # apply existing migrations (production/CI, no prompts)
pnpm exec prisma migrate reset          # ⚠️ wipe local DB, reapply all migrations + reseed (local only)
pnpm exec prisma generate               # regenerate the client
pnpm exec prisma studio                 # visual data browser
pnpm db:seed                            # run the seed script

# Dev server
pnpm dev                          # docker compose up -d postgres + generate + push + hot reload
```

### 7.15 Common Prisma and PostgreSQL Errors

| Problem | Likely cause | Fix |
|---|---|---|
| `Connection refused` when migrating | The container isn't running | `docker compose up -d postgres` |
| `Error: P1000` (authentication failed) on a container that starts fine | The `.env` password was changed, but the Postgres **volume already exists** with the old password baked in — Postgres never re-reads `POSTGRES_PASSWORD` after first init | `docker compose down -v` (wipes the volume) then `docker compose up -d --build` again |
| `Error: P1001` (can't reach database) | Wrong `DATABASE_URL` | Check user, password, host and port |
| `PrismaConfigEnvError: Cannot resolve environment variable: DATABASE_URL` when running `prisma generate`/`migrate`/`studio` | `prisma.config.ts` needs `DATABASE_URL` in the environment, and nothing loaded `.env` in this shell/build step | Export it inline for that one command, e.g. `DATABASE_URL="postgresql://user:pass@localhost:5432/db" pnpm exec prisma generate` — any placeholder works for `generate` |
| `[ERR_PNPM_IGNORED_BUILDS]` during `pnpm install` | pnpm ≥ 10 blocks lifecycle/build scripts by default (Prisma engines, `bcrypt`, `esbuild`) | Add `allowBuilds` to `pnpm-workspace.yaml` — see [7.5](#75-configuration-files-tsconfigjson-prismaconfigts-and-pnpm-workspaceyaml) |
| `Cannot find module '.prisma/client/default'` when seeding | The Prisma Client was never generated in this environment (fresh install, or `node_modules` wiped) | `pnpm exec prisma generate` before `pnpm db:seed` |
| `sh: 1: tsc: not found` on build | `typescript` isn't declared as a direct dependency of this package (easy to miss if it used to come from a monorepo root) | Add `typescript` to `devDependencies` — see [7.3](#73-install-dependencies) |
| `prisma:warn Prisma failed to detect the libssl/openssl version` during install/generate in a `node:*-slim` Docker image | Harmless in practice — Prisma falls back to a default engine variant | Safe to ignore; only worth acting on if queries actually fail at runtime, in which case switch away from a `-slim` base image |
| Prisma Client out of date | Schema changed without regenerating | `pnpm exec prisma generate` |
| Migrations in conflict | Local schema doesn't match the database | `pnpm exec prisma migrate reset` (⚠️ wipes data) |
| Port `5432` already in use | Another PostgreSQL instance is running | Change the port in `docker-compose.yml` to e.g. `5433:5432` and update `DATABASE_URL` |
| `401 Unauthorized` on every request in production, but it worked in local dev | Cookie is `SameSite=Lax`/non-`Secure` while frontend and backend are now on different domains — the browser silently drops it | Use the production cookie settings from [7.11](#711-simple-backend-entry-point-srcindexts-login-example) / [8.5](#85-cors-and-cookies-across-different-domains); see also [12. Common HTTP Status Codes](#12-common-http-status-codes) |
| `No permitido por CORS` / `Not allowed by CORS` | The frontend's exact origin isn't in `ALLOWED_ORIGINS`, or it's missing `https://`, or it has a trailing slash | Fix `ALLOWED_ORIGINS` in `.env` (exact match required) and restart the backend — see [8.5](#85-cors-and-cookies-across-different-domains) |

---

## 8. Full Separation: Independent Backend, Frontend(s) and Deployment

An alternative to the monorepo approach: the backend from [7](#7-database--backend-prisma--postgresql) and each Vite + React frontend live in **completely separate repositories**, with no shared workspace, root `package.json`, or `docker-compose.yml`. The backend deploys to a VPS as a Docker container; each frontend deploys independently to Cloudflare Pages.

### 8.1 Why Full Separation Instead of a Monorepo

| | Monorepo (pnpm workspace) | Full separation |
|---|---|---|
| Deploy targets | Awkward when frontend and backend go to genuinely different platforms (e.g. Cloudflare Pages vs a VPS) | Natural — each repo deploys to wherever it needs to, independently |
| Shared internal packages (e.g. shared types) | Free — `workspace:*` just works | Not available — shared types/fetch helpers get duplicated by hand into each repo |
| Coupling | One `git clone` gets everything; one `pnpm install` at the root sets up all packages | Each repo is `git clone`d, installed and versioned on its own |
| Risk | A change to a shared package can silently affect every consumer | Nothing changes without an explicit edit in that specific repo — but keeping multiple copies of the same fetch wrapper/types in sync across repos is now a manual discipline, not something the tooling enforces |

There's no universally correct choice — pick based on where each piece will actually be hosted. The rest of this section documents the full-separation setup end to end.

### 8.2 Backend Repo: `docker-compose.yml` (Postgres and API)

Unlike the monorepo's shared root compose file (which only ran Postgres), the backend's own `docker-compose.yml` runs **both** Postgres and the backend itself — this is what actually ships to the VPS:

```yaml
services:
  postgres:
    image: postgres:18
    container_name: postgres
    restart: unless-stopped
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: ${DB_PASSWORD}
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres -d mydb"]
      interval: 5s
      timeout: 5s
      retries: 5

  backend:
    build: .
    image: service-manager-backend
    container_name: backend
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    environment:
      DATABASE_URL: postgresql://postgres:${DB_PASSWORD}@postgres:5432/mydb?schema=public
      PORT: 3001
      NODE_ENV: production
      ADMIN_USERNAME: ${ADMIN_USERNAME}
      ADMIN_PASSWORD: ${ADMIN_PASSWORD}
      ALLOWED_ORIGINS: ${ALLOWED_ORIGINS}
    ports:
      - "3001:3001"

volumes:
  postgres_data:
    name: postgres_data
```

Notes:

- `container_name` and `image` are set explicitly on both services — without `image:` on `backend`, Docker Compose names the built image `<folder-name>-backend`, which is rarely what you want to see in `docker images`.
- Inside the Docker network, the backend reaches Postgres at host `postgres` (the service name), **not** `localhost` — that only applies when running the backend outside Docker.
- In production, don't publish Postgres's `5432` to the host (remove any `ports:` under `postgres`) — nothing outside the VPS needs to talk to it directly, since the backend is on the same Docker network.
- For **local development**, publishing `5432:5432` on `postgres` is exactly what lets `pnpm dev` ([7.3](#73-install-dependencies)) run the backend outside Docker while still reaching the containerized database.

### 8.3 Backend `Dockerfile` (pnpm, Node 24, Multi-Stage)

```dockerfile
FROM node:24-slim AS base
WORKDIR /app
RUN corepack enable

# ── deps ─────────────────────────────────────────────────────────────────────
FROM base AS deps
COPY package.json ./
COPY pnpm-lock.yaml ./
COPY pnpm-workspace.yaml ./
COPY prisma ./prisma
RUN pnpm install --ignore-scripts=false

# ── build ────────────────────────────────────────────────────────────────────
FROM deps AS build
COPY . .
RUN DATABASE_URL="postgresql://user:pass@localhost:5432/db" pnpm exec prisma generate
RUN pnpm run build

# ── runtime ──────────────────────────────────────────────────────────────────
FROM base AS runtime
ENV NODE_ENV=production
COPY --from=deps /app/node_modules ./node_modules
COPY --from=build /app/dist ./dist
COPY --from=build /app/prisma ./prisma
COPY package.json ./

EXPOSE 3001
CMD ["sh", "-c", "pnpm exec prisma migrate deploy && node dist/index.js"]
```

Points worth calling out:

- `node:24-slim` — Node 24 is the current LTS; `-slim` keeps the image small. Avoid `node:latest`, which silently jumps major versions on every rebuild.
- `--ignore-scripts=false` on `pnpm install` — needed alongside `allowBuilds` in `pnpm-workspace.yaml` ([7.5](#75-configuration-files-tsconfigjson-prismaconfigts-and-pnpm-workspaceyaml)), or the image ends up with a half-installed Prisma/`bcrypt`.
- The `DATABASE_URL="..."` placeholder before `prisma generate` — this runs at **image build time**, before any real `.env` exists; `generate` only needs a syntactically valid connection string, it never connects.
- `COPY --from=deps` vs `COPY --from=build` in `runtime` — `node_modules` comes from `deps` (installed dependencies), `dist/` and `prisma/` from `build` (compiled code and migrations, since that's the stage that ran `COPY . .`).
- The `CMD` runs `prisma migrate deploy` on every boot before starting the server — migrations apply automatically, nothing to run by hand on the VPS.

Also add a `.dockerignore` next to the `Dockerfile`, or `node_modules`/`dist` from the host get copied into the build context and can break the build:

```
node_modules
dist
.env
```

### 8.4 `pnpm-workspace.yaml`: Allowing Build Scripts (pnpm 10 or Newer)

Covered in [7.5](#75-configuration-files-tsconfigjson-prismaconfigts-and-pnpm-workspaceyaml) — repeated here because it's specifically what makes the Docker build in [8.3](#83-backend-dockerfile-pnpm-node-24-multi-stage) succeed instead of failing with `[ERR_PNPM_IGNORED_BUILDS]`:

```yaml
allowBuilds:
  '@prisma/engines': true
  bcrypt: true
  esbuild: true
  prisma: true
```

Must be copied into the Docker build context (`COPY pnpm-workspace.yaml ./` in the `deps` stage) — if it's missing from `.dockerignore` accidentally, or just never copied, the build fails inside the container the same way it does locally without it.

### 8.5 CORS and Cookies Across Different Domains

This is the part that actually breaks when going from monorepo (same-origin via Vite's dev proxy) to full separation (frontend and backend genuinely on different domains) — and the single most common source of "it works locally but not in production" here.

**CORS** — an explicit origin allowlist instead of reflecting any origin:

```typescript
const allowedOrigins = (process.env.ALLOWED_ORIGINS ?? "")
  .split(",")
  .map((o) => o.trim())
  .filter(Boolean);

app.use(
  cors({
    origin(origin, callback) {
      if (!origin || allowedOrigins.length === 0 || allowedOrigins.includes(origin)) {
        callback(null, true);
        return;
      }
      callback(new Error("Not allowed by CORS"));
    },
    credentials: true,
  }),
);
```

`ALLOWED_ORIGINS` must list the **exact** production origins of every frontend that calls this backend (`https://admin.example.com,https://portal.example.com`) — protocol included, no trailing slash. A mismatch here is the direct cause of `No permitido por CORS` / `Not allowed by CORS`.

**Cookies** — with the frontend and backend on different domains, every login/session cookie is a cross-site cookie from the browser's point of view:

```typescript
const IS_PRODUCTION = process.env.NODE_ENV === "production";

const cookieOptions = {
  httpOnly: true,
  secure: IS_PRODUCTION,
  sameSite: (IS_PRODUCTION ? "none" : "lax") as "none" | "lax",
};
```

- `SameSite=Lax` (the default) blocks the cookie on cross-site `fetch`/`XHR` calls — only `SameSite=None` allows it.
- `SameSite=None` **requires** `Secure`, which means the backend must be served over real HTTPS in production ([8.7](#87-https-in-front-of-the-backend-caddy)) — without it, the browser refuses to set the cookie at all, and every request after login looks unauthenticated (`401`) even though login itself appeared to succeed.
- Locally, frontend and backend are still effectively same-site (`localhost` talking to `localhost`, or same-origin behind Vite's dev proxy), so `Lax` without `Secure` keeps working — hence branching on `NODE_ENV`.

`clearCookie(...)` on logout must use **the same options** (`httpOnly`, `secure`, `sameSite`) used when the cookie was set, or the browser won't recognize it as the same cookie to remove.

### 8.6 Each Frontend as Its Own Repo (Cloudflare Pages)

Nothing changes in the frontend's own code for this to work — the fetch wrapper already reads the backend's base URL from an environment variable:

```typescript
// src/api.ts
const BASE = import.meta.env.VITE_API_URL ?? "";

async function request<T>(path: string, init?: RequestInit): Promise<T> {
  const res = await fetch(`${BASE}${path}`, {
    ...init,
    credentials: "include",
    headers: { "Content-Type": "application/json", ...(init?.headers ?? {}) },
  });
  if (!res.ok) {
    const body = await res.json().catch(() => ({}));
    throw new Error((body as { error?: string }).error ?? `HTTP ${res.status}`);
  }
  if (res.status === 204) return undefined as T;
  return res.json() as Promise<T>;
}
```

In dev, leaving `VITE_API_URL` unset (`BASE` becomes `""`) works together with Vite's proxy (`/api` → `http://localhost:3001`, [5.3](#53-viteconfigts-reference)). In Cloudflare Pages:

1. Push this frontend as its own Git repository.
2. Create a Cloudflare Pages project connected to that repo.
3. Build command: `npm run build` (or `pnpm build`). Output directory: `dist`.
4. Under **Settings → Environment variables**, set `VITE_API_URL` to the backend's real HTTPS URL (e.g. `https://api.example.com`, no trailing slash).
5. Deploy, then add the resulting Pages domain to the backend's `ALLOWED_ORIGINS` ([8.5](#85-cors-and-cookies-across-different-domains)) and restart the backend container.

Multiple independent frontends (e.g. an admin panel and a separate customer-facing portal) can point at the same backend this way — each is its own Pages project, its own repo, and just needs its own entry added to `ALLOWED_ORIGINS`.

### 8.7 HTTPS in Front of the Backend (Caddy)

Required because of the cookie settings in [8.5](#85-cors-and-cookies-across-different-domains) — `Secure` cookies are simply not set by the browser over plain HTTP. Caddy is the simplest option since it issues and renews the TLS certificate on its own:

```bash
sudo apt install -y caddy
```

`/etc/caddy/Caddyfile`:

```
api.example.com {
    reverse_proxy localhost:3001
}
```

```bash
sudo systemctl restart caddy
```

The domain's DNS `A` record must already point at this VPS's IP **before** restarting Caddy, or certificate issuance fails.

### 8.8 Local Development Without Docker for the Backend

The full production `docker-compose.yml` from [8.2](#82-backend-repo-docker-composeyml-postgres-and-api) also builds and runs the backend itself — convenient for a final end-to-end check, but slower to iterate against than `tsx watch`. Day to day, only Postgres runs in Docker, and the backend runs directly on the host via the `dev` script from [7.3](#73-install-dependencies):

```bash
docker compose up -d postgres   # only the database, from the same compose file
pnpm dev                        # generate + db push + tsx watch, outside Docker
```

This is exactly why `postgres` still publishes `5432:5432` in [8.2](#82-backend-repo-docker-composeyml-postgres-and-api) — it's what lets `DATABASE_URL` in the local `.env` point at `localhost:5432` while `pnpm dev` runs on the host. When you actually want to test the full container build (`backend` service included), use `docker compose up -d --build` instead, and remember the container talks to Postgres via the service name `postgres`, not `localhost` — the two `DATABASE_URL`s (host `.env` vs the one injected into the `backend` container in `docker-compose.yml`) are intentionally different for this reason.

### 8.9 Final Project Structure (Three Independent Repos)

No shared root — three separate repositories, each deployed independently:

```
service-manager-backend/          (→ VPS, Docker)
├── .github/
│   └── workflows/
│       ├── audit.yml
│       ├── deploy.yml
│       └── prettier.yml
├── prisma/
│   ├── migrations/
│   ├── schema.prisma
│   └── seed.ts
├── src/
│   └── index.ts
├── .dockerignore
├── .env                          (never committed)
├── .gitignore
├── docker-compose.yml
├── Dockerfile
├── package.json
├── pnpm-workspace.yaml
├── prisma.config.ts
└── tsconfig.json

admin-frontend/                   (→ Cloudflare Pages)
├── .github/
│   └── workflows/
│       ├── audit.yml
│       └── prettier.yml
├── public/
└── src/
    ├── components/
    ├── layouts/
    ├── pages/
    ├── api.ts
    ├── types.ts
    ├── App.tsx
    ├── global.css
    └── main.tsx

customer-portal/                  (→ Cloudflare Pages, separate project)
├── .github/
│   └── workflows/
│       ├── audit.yml
│       └── prettier.yml
├── public/
└── src/
    ├── components/
    ├── layouts/
    ├── pages/
    ├── api.ts
    ├── App.tsx
    ├── global.css
    └── main.tsx
```

Only the backend gets `deploy.yml` — it's the one repo that deploys by SSH to a VPS ([8.3](#83-backend-dockerfile-pnpm-node-24-multi-stage)). `audit.yml` and `prettier.yml` are identical across all three, since they're generic checks that don't depend on how (or where) a repo deploys ([11.9](#119-github-actions-cicd-workflows)).

Each repo has its own `package.json`, its own `pnpm install`, and its own `git` history. `admin-frontend/src/types.ts` exists because there's no shared workspace package to import domain types from anymore — they're copied in and kept manually in sync with whatever the backend actually returns; the same applies to the near-identical `api.ts` fetch wrapper duplicated across both frontends.

### 8.10 Continuous Deployment on Push (GitHub Actions)

Everything so far still means logging into the VPS by hand after every change (`git pull`, `docker compose up -d --build backend`). GitHub Actions can do that automatically on every `git push`, using the repo's built-in CI/CD instead of any extra service.

The frontends already get this for free — Cloudflare Pages redeploys automatically as soon as it sees a new commit on the connected branch, no workflow file needed. This section is specifically for the **backend**, which doesn't have anything like that built in.

**Step 1 — Generate a dedicated SSH key pair for deployment**, on the VPS itself:

```bash
ssh-keygen -t ed25519 -f ~/.ssh/deploy_key -N ""
cat ~/.ssh/deploy_key.pub >> ~/.ssh/authorized_keys
cat ~/.ssh/deploy_key
```

The last command prints the **private** key — copy its full output (including the `-----BEGIN...-----`/`-----END...-----` lines) for the next step. Using a dedicated key (instead of your personal one) means it can be revoked later without affecting your own SSH access.

**Step 2 — Store three secrets in the GitHub repo**, under **Settings → Secrets and variables → Actions → New repository secret**:

| Secret name | Value |
|---|---|
| `SSH_HOST` | The VPS's IP address (or domain) |
| `SSH_USERNAME` | The Linux user to connect as on the VPS |
| `SSH_PRIVATE_KEY` | The private key printed in Step 1 |

Secrets are encrypted at rest and never shown again in the UI once saved — treat the values as you would any other credential.

**Step 3 — Add the workflow file** at `.github/workflows/deploy.yml` in the backend's repo:

```yaml
name: Deploy backend

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: SSH and deploy
        uses: appleboy/ssh-action@v1
        with:
          host: ${{ secrets.SSH_HOST }}
          username: ${{ secrets.SSH_USERNAME }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          script: |
            cd ~/service-manager-backend
            git pull
            docker compose up -d --build backend
```

What each part does:

- `on: push: branches: [main]` — this workflow only runs on pushes to `main`.
- `appleboy/ssh-action` — a community GitHub Action that opens an SSH connection using the three secrets above and runs `script:` on the remote host, exactly as if it were typed by hand over SSH.
- `cd ~/service-manager-backend` — must match the actual path where the repo was cloned on the VPS.
- `git pull` — fetches the commit that was just pushed.
- `docker compose up -d --build backend` — rebuilds only the `backend` image and recreates that one container ([8.2](#82-backend-repo-docker-composeyml-postgres-and-api)); `postgres` is untouched, matching the reasoning in [8.2](#82-backend-repo-docker-composeyml-postgres-and-api) about not restarting the database on every code change.

**Step 4 — Push and watch it run**: `git push origin main`, then check the **Actions** tab on GitHub — a green check means the VPS already pulled and rebuilt on its own.

Since the container's `CMD` runs `prisma migrate deploy` on every boot ([8.3](#83-backend-dockerfile-pnpm-node-24-multi-stage)), any pending migration is applied automatically as part of this same deploy — no separate manual step for that either.

A couple of things worth keeping in mind:

- This gives push access to your VPS to anyone who can push to `main` (or merge into it) — branch protection rules on GitHub are worth setting up if more than one person has write access to the repo.
- The exact same pattern (workflow file + three secrets) can be reused for any other repo that needs this — it isn't specific to this backend, only the `cd` path and the `docker compose` command at the end change.

---
## 9. Linux Server & Docker Deployment

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

### 9.1 Connect with Bitvise SSH Client

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

### 9.2 Basic Linux Setup

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

### 9.3 Install Only the Basic Utilities Needed Here

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

### 9.4 Node.js: Required by the Projects

**Node.js is required for this development stack** — Vite, Next.js and pnpm all use it. There are two different places it can exist:

```text
Development machine
    └── Node.js + pnpm

Production server
    └── Docker
         └── node:latest
              └── your application
```

For production, the Linux host does **not** need its own Node.js installation — the Docker image already contains it, so there's nothing to install twice.

If you intentionally want Node directly on the server anyway, you can install the Ubuntu package:

```bash
sudo apt install -y nodejs npm
```

Check it:

```bash
node -v
npm -v
```

For the Docker deployment in this README, you can skip those host commands.

### 9.5 Install Docker and Docker Compose

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

### 9.6 Allow Your User to Run Docker Without `sudo`

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

### 9.7 First Docker Test

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

### 9.8 Basic Linux Commands for Deployments

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

### 9.9 Firewall Basics with UFW

The server needs SSH, HTTP and HTTPS. Since every domain will always sit behind Cloudflare (see [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl)), it's worth restricting `80`/`443` to Cloudflare's own IP ranges instead of the whole Internet — that way nobody can bypass Cloudflare's protection by hitting the server's IP directly.

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

> If a site is ever used without Cloudflare in front of it, allow `80/tcp` and `443/tcp` from anywhere instead (`sudo ufw allow 80/tcp` / `sudo ufw allow 443/tcp`) — but that also means the Origin Certificate from [9.14](#914-traefik--cloudflare-origin-certificate--three-websites) won't be trusted by regular browsers, since it's only trusted by Cloudflare.

### 9.10 Create the Server Structure

Create the main folder:

```bash
sudo mkdir -p /opt/web
cd /opt/web
```

Create the folder for the Cloudflare Origin Certificate (generated in [9.14](#914-traefik--cloudflare-origin-certificate--three-websites)):

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

### 9.11 Vite + React Dockerfile

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

### 9.12 Next.js Dockerfile

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

### 9.13 `.dockerignore`

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

### 9.14 Traefik + Cloudflare Origin Certificate + Three Websites

Traefik is the only reverse proxy in this architecture.

It will:

1. Listen on server ports `80` and `443`.
2. Detect the Docker containers that have Traefik labels.
3. Match each domain to the correct container.
4. Redirect HTTP to HTTPS.
5. Present a TLS certificate to whoever connects on `443`.

Traefik's Docker provider reads container labels. Using `exposedbydefault=false` means containers are ignored unless they explicitly opt in with `traefik.enable=true`.

Since every domain here is always proxied through Cloudflare (see [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl)), Cloudflare's free Universal SSL already handles the certificate that public visitors see — Traefik doesn't need to request or renew a Let's Encrypt certificate for that. What Traefik still needs is a certificate for the **Cloudflare → origin** leg of the connection, so that "Full (strict)" mode can verify it. That's what a free **Cloudflare Origin Certificate** is for: generate it once in the Cloudflare dashboard (**SSL/TLS → Origin Server → Create Certificate**), list all three hostnames as SANs (`site1.example.com`, `site2.example.com`, `site3.example.com`), and it stays valid for up to 15 years — no ACME challenge, no renewal automation needed.

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

### 9.15 Understand the Important Traefik Lines

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

These mount the Cloudflare Origin Certificate and the file-provider config that loads it (see [9.14](#914-traefik--cloudflare-origin-certificate--three-websites)). No ACME resolver, no HTTP-01 challenge, and nothing to renew — the certificate is generated once in the Cloudflare dashboard and is valid for up to 15 years.

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

### 9.16 Why the Three Websites Are Different

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

### 9.17 DNS Setup

Before HTTPS can work, the domains must point to the server through Cloudflare.

In the Cloudflare dashboard, under **DNS → Records**, create:

```text
site1.example.com → A → SERVER_PUBLIC_IP → Proxied (orange cloud)
site2.example.com → A → SERVER_PUBLIC_IP → Proxied (orange cloud)
site3.example.com → A → SERVER_PUBLIC_IP → Proxied (orange cloud)
```

Use `A` records for IPv4 addresses, and keep the proxy status **Proxied** (orange cloud), not **DNS only** (grey cloud). Proxied is what actually puts Cloudflare in front of the site — it hides the server's real IP, applies the free protection described in [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl), and terminates the public-facing SSL. A grey-cloud record just points visitors straight at the server, bypassing all of that.

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

### 9.18 First Deployment

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

### 9.19 Useful Deployment Commands

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

### 9.20 Update Only One Website

Suppose only `web2` changed. `docker-compose.yml` and `certs/` live one level above `web2/`, so none of this touches them.

Back up anything that only exists on the server and isn't in your new zip (usually the `Dockerfile`, if you created it directly on the server instead of keeping it in your project — see [9.11](#911-vite--react-dockerfile)/[9.12](#912-nextjs-dockerfile) — and any `.env` file):

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

### 9.21 Docker Disk Cleanup

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

### 9.22 Fail2ban Basic Configuration

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

Fail2ban is an additional layer. It does not replace updates, firewall rules or SSH keys. It's only needed here for SSH — SSH isn't proxied through Cloudflare, so Cloudflare's DDoS/bot protection never sees it. The websites themselves don't need a `[traefik]`/HTTP jail: that surface already sits behind Cloudflare's free protection (see [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl)), and UFW ([9.9](#99-firewall-basics-with-ufw)) already blocks anyone trying to hit ports `80`/`443` directly instead of through Cloudflare.

### 9.23 Basic SSH Hardening

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

### 9.24 Troubleshooting

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

1. The DNS record is **Proxied** (orange cloud), not DNS only — see [9.17](#917-dns-setup).
2. SSL/TLS mode in Cloudflare is set to **Full (strict)**, not Flexible ([10.4](#104-vite--nextjs--cloudflare-protection--free-ssl)).
3. `/opt/web/certs/cert.pem` and `key.pem` exist and hold the Origin Certificate/Key generated in [9.14](#914-traefik--cloudflare-origin-certificate--three-websites), not placeholders.
4. The Origin Certificate's SANs include the exact domain being requested.
5. UFW allows `80`/`443` from Cloudflare's IP ranges ([9.9](#99-firewall-basics-with-ufw)).
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

### 9.25 Final Production Checklist

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
## 10. Deployment

### 10.1 Google Search Console

1. Go to [Google Search Console](https://search.google.com/search-console) and add a new property using the site's domain or URL prefix.
2. Verify ownership — via DNS TXT record (domain property) or an HTML file/meta tag (URL-prefix property), depending on the method chosen.
3. Once verified, submit the sitemap under **Sitemaps** using the URL generated by the project (e.g. `https://mysite.com/sitemap-index.xml` for Vite + React).
4. Use the **URL Inspection** tool to request indexing for key pages after the first deploy.

### 10.2 Cloudflare Pages

1. In the [Cloudflare dashboard](https://dash.cloudflare.com/), go to **Workers & Pages → Create → Pages**, and connect the GitHub repository.
2. Configure the build settings:
   - **Framework preset**: Vite + React (Cloudflare has presets for both).
   - **Build command**: `pnpm build` (or `npm run build`).
   - **Build output directory**: `dist` (default for Vite + React).
3. Add any required environment variables under **Settings → Environment variables**.
4. Every push to the connected branch (e.g. `main`) triggers an automatic deploy; other branches get preview deployments.
5. Under **Custom domains**, attach the production domain once it's ready.

Astro sites always live in your own Cloudflare Pages account, but the domain itself usually belongs to the client — see [10.5](#105-pointing-the-clients-domain-astro) for how to point it there.

### 10.3 Cloudflare Domains & Rules

- **DNS**: if the domain is registered with Cloudflare (or just uses Cloudflare as DNS), add/verify the records under **DNS → Records**. Pages projects usually just need a `CNAME` pointing to the `*.pages.dev` deployment, added automatically when attaching a custom domain.
- **SSL/TLS**: keep the encryption mode set to **Full** or **Full (strict)** for Pages projects.
- **Redirect rules**: under **Rules → Redirect Rules**, common basics are forcing `www` → apex (or the reverse) and forcing `https`.
- **Page Rules / Cache Rules**: useful for basics like always redirecting `http://` to `https://`, or setting cache behavior for static assets under `/images/*` or `/assets/*`.

### 10.4 Vite + Next.js + Cloudflare Protection & Free SSL

This section applies to the self-hosted Vite/Next.js sites from [9. Linux Server & Docker Deployment](#9-linux-server--docker-deployment) — the Docker + Traefik setup running on your own VPS, as opposed to [10.2](#102-cloudflare-pages) which is for Cloudflare Pages. On the free plan, Cloudflare in front of that server gives you both protection and SSL with nothing extra to buy or renew.

**1. Add the site and proxy the DNS record**

In the Cloudflare dashboard, add the domain and create the `A` record described in [9.17](#917-dns-setup), keeping it **Proxied** (orange cloud). This is what actually routes traffic through Cloudflare instead of straight to the server, and it's a prerequisite for everything below.

**2. Set the SSL/TLS encryption mode to Full (strict)**

Under **SSL/TLS → Overview**, choose **Full (strict)**. This encrypts both legs of the connection: browser → Cloudflare (Cloudflare's free Universal SSL certificate, issued and renewed automatically) and Cloudflare → your server (the Cloudflare Origin Certificate from [9.14](#914-traefik--cloudflare-origin-certificate--three-websites)). Avoid **Flexible** — it only encrypts the first leg, leaving Cloudflare-to-server traffic in plain HTTP.

**3. Turn on "Always Use HTTPS"**

Under **SSL/TLS → Edge Certificates**, enable **Always Use HTTPS** so any `http://` request gets redirected. This is redundant with Traefik's own HTTP→HTTPS redirect ([9.15](#915-understand-the-important-traefik-lines)), but costs nothing to leave on and catches requests before they even reach the server.

**4. Protection that's on by default (nothing to configure)**

The free plan already includes, automatically, for any proxied domain:

- Unmetered DDoS protection at the network edge.
- The server's real IP is hidden — only Cloudflare's IPs are ever visible to visitors, which is what [9.9](#99-firewall-basics-with-ufw)'s UFW rule (allowing `80`/`443` only from Cloudflare's ranges) is there to enforce.
- A CDN cache for static assets, reducing load on the server.

**5. Optional extra protection (free plan)**

- **Bot Fight Mode** (**Security → Bots**) — challenges known bad bots.
- **Under Attack Mode** (**Security → Settings**) — puts up a JS challenge page for every visitor; use temporarily during an active attack, not by default, since it adds friction for real visitors.
- Up to 5 free custom **WAF rules** (**Security → WAF**) if you want to block or challenge specific patterns (e.g. a known bad path or country).

**What this replaces**

Because Cloudflare handles the above automatically, this setup intentionally drops what a non-Cloudflare deployment would otherwise need: no Let's Encrypt/ACME renewal loop on the server ([9.14](#914-traefik--cloudflare-origin-certificate--three-websites)), no open port `80`/`443` to the whole Internet ([9.9](#99-firewall-basics-with-ufw)), and no separate HTTP-layer fail2ban jail ([9.22](#922-fail2ban-basic-configuration)) — Fail2ban stays, but only for SSH.

Everything above assumes the domain's DNS is already a zone inside your own Cloudflare account. When the domain actually belongs to a client, see [10.6](#106-pointing-the-clients-domain-vite--nextjs) for how to get it pointed at the server.

### 10.5 Pointing the Client's Domain (Astro)

This applies to Astro sites deployed on [10.2](#102-cloudflare-pages): the Pages project always lives in **your** Cloudflare account, but the domain (e.g. `clientsite.com`) belongs to the client. There are two ways to connect them, depending on how much access the client is willing to give you.

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

### 10.6 Pointing the Client's Domain (Vite + Next.js)

This applies to the self-hosted Vite/Next.js sites from [9. Linux Server & Docker Deployment](#9-linux-server--docker-deployment), using the free SSL setup from [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl). Unlike Astro on Pages, this setup needs the domain to actually be **proxied through Cloudflare** (orange cloud) for the free Universal SSL and DDoS/bot protection to apply — a plain DNS-only record pointed at the server bypasses Cloudflare entirely.

**Option A — The client moves their nameservers into your Cloudflare account**

1. Add the domain to your Cloudflare account the same way as in [10.5](#105-pointing-the-clients-domain-astro), Option A (steps 1–4).
2. Once the domain is **Active** in your account, follow [9.17](#917-dns-setup) exactly: create the `A` record pointing to the server's public IP, kept **Proxied** (orange cloud).
3. Generate/reuse the Cloudflare **Origin Certificate** for that domain ([9.14](#914-traefik--cloudflare-origin-certificate--three-websites)) and add it to Traefik's `dynamic` config alongside the existing sites.
4. Set **SSL/TLS → Overview** to **Full (strict)** for the zone, as in [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl).

**Option B — The client keeps their own Cloudflare account**

Use this when the client already has the domain on Cloudflare themselves and doesn't want to change nameservers.

1. Give the client the server's public IP and ask them to create an `A` record (e.g. `app.clientsite.com` → your server IP) in **their** Cloudflare dashboard, kept **Proxied** (orange cloud). Without Proxied, they get no free SSL or protection from Cloudflare — traffic goes straight to the server over plain HTTP unless you handle certificates yourself.
2. Ask the client to set their zone's **SSL/TLS → Overview** to **Full (strict)** — same reasoning as [10.4](#104-vite--nextjs--cloudflare-protection--free-ssl): Flexible would leave the Cloudflare→server leg unencrypted.
3. You still need a **Cloudflare Origin Certificate** on the server for that domain so the Cloudflare→server leg is encrypted. Since the zone lives in the client's account, either:
   - Ask the client to generate the Origin Certificate themselves (**SSL/TLS → Origin Server → Create Certificate**, covering the subdomain you need) and send you the cert/key pair, which you drop into `certs/` and reference in Traefik's `dynamic` config exactly like the other sites in [9.14](#914-traefik--cloudflare-origin-certificate--three-websites); or
   - Ask them to add you as a member on their Cloudflare account (**Manage Account → Members**) with access scoped to that zone, so you can generate the certificate yourself without them needing to know what it is.
4. Add a new router/service block in `docker-compose.yml` for the client's domain, following the pattern in [9.16](#916-why-the-three-websites-are-different) — same idea, just with the client's domain in the `Host(...)` rule instead of one of your own.
5. Firewall-wise, nothing changes: UFW ([9.9](#99-firewall-basics-with-ufw)) already only allows `80`/`443` from Cloudflare's IP ranges regardless of which Cloudflare account is proxying the request.

**Option A vs Option B**

| | Option A (your account) | Option B (client's account) |
|---|---|---|
| Who manages DNS | You | The client |
| Nameserver change needed | Yes | No |
| Origin Certificate generated by | You | You or the client, depending on access |
| Best for | Long-term/ongoing clients | Clients who want to keep control of their domain |

---
## 11. Git and GitHub

### 11.1 Initial Setup (First-Time Project)

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

### 11.2 Daily Workflow

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

### 11.3 Branching

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

### 11.4 Other Useful Commands

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

### 11.5 Undoing Things: `reset`, `restore`, `revert`

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

### 11.6 `rebase` vs `merge`

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

### 11.7 Force Push and Other Dangerous Commands

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

### 11.8 Real Branching Flow: Feature Branch → Main

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

### 11.9 GitHub Actions: CI/CD Workflows

GitHub Actions runs workflow files automatically on events like `push` or `pull_request` — no external CI service needed. Each workflow lives in `.github/workflows/<name>.yml`, in the repo it applies to (with full separation, [8.9](#89-final-project-structure-three-independent-repos), each repo needs its own copy of whichever of these apply to it).

**Deploy on push (backend only)** — connects to the VPS over SSH and rebuilds the container, replacing the manual `git pull` + `docker compose up -d --build` from [8](#8-full-separation-independent-backend-frontends-and-deployment):

```yaml
# .github/workflows/deploy.yml
name: Deploy backend

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: SSH and deploy
        uses: appleboy/ssh-action@v1
        with:
          host: ${{ secrets.SSH_HOST }}
          username: ${{ secrets.SSH_USERNAME }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          script: |
            cd ~/service-manager-backend
            git pull
            docker compose up -d --build backend
```

`SSH_HOST`, `SSH_USERNAME` and `SSH_PRIVATE_KEY` are repository secrets (**Settings → Secrets and variables → Actions**) — never hardcode credentials directly in a workflow file, since it's committed and visible to anyone with read access to the repo. The private key should be a dedicated deploy key (`ssh-keygen -t ed25519 -f ~/.ssh/deploy_key`), added to `~/.ssh/authorized_keys` on the server, so it can be revoked independently of anyone's personal key.

**Dependency security audit** — runs on every push and on PRs targeting `main`, flagging known vulnerabilities in installed packages:

```yaml
# .github/workflows/audit.yml
name: Security Audit

on:
  push:
  pull_request:
    branches: ["main"]

jobs:
  audit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v7

      - name: Install pnpm
        uses: pnpm/setup@v2
        with:
          version: 12
          runtime: node@24

      - name: Run Security Audit
        # Runs pnpm audit. To check production dependencies only, use: pnpm audit --prod
        run: pnpm audit
```

**Code style check** — fails the workflow (and shows a red X on the PR) if any file isn't formatted with Prettier:

```yaml
# .github/workflows/prettier.yml
name: Code Style (Prettier)

on:
  push:
  pull_request:
    branches: ["main"]

jobs:
  prettier:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v7

      - name: Install pnpm
        uses: pnpm/setup@v2
        with:
          version: 12
          runtime: node@24

      - name: Install Dependencies
        run: pnpm install --frozen-lockfile

      - name: Check Code Style
        run: pnpm run format:check
```

Requires a `format:check` script in `package.json` (e.g. `"format:check": "prettier --check ."`) — the same command run locally before committing.

`pnpm/setup@v2` replaces the two separate steps used previously (`actions/setup-node` + `pnpm/action-setup`) — `runtime: node@24` installs the Node.js runtime and `version: 12` the pnpm version, both in a single step.

`audit.yml` and `prettier.yml` are generic enough to copy as-is into any repo that has a `package.json` and a lockfile; `deploy.yml` is specific to whichever repo actually deploys by SSH (the backend, in the full-separation setup from [8](#8-full-separation-independent-backend-frontends-and-deployment) — the frontends deploy via Cloudflare Pages instead, which redeploys on push without needing a workflow file at all).

---

## 12. Common HTTP Status Codes

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
