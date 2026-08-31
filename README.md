# Developer Notes

Personal reference notes for setting up a web development environment, scaffolding websites with **Astro, Vite + React, and Next.js**, and working with Git/GitHub. The classes, tags, colors, and fonts used in the examples below are illustrative — swap them for any generic CSS classes, framework, or design system.

## Index

- [1. Required Programs](#1-required-programs)
- [2. VS Code Extensions](#2-vs-code-extensions)
- [3. VS Code Keyboard Shortcuts](#3-vs-code-keyboard-shortcuts)
  - [3.1 General](#31-general)
  - [3.2 Editing](#32-editing)
  - [3.3 Navigation](#33-navigation)
- [4. Website Development — Astro + Tailwind](#4-website-development--astro--tailwind)
  - [4.1 Project Setup](#41-project-setup)
  - [4.2 Tailwind CSS Setup](#42-tailwind-css-setup)
  - [4.3 Tailwind Theme, Custom Fonts & View Transitions](#43-tailwind-theme-custom-fonts--view-transitions)
  - [4.4 Sitemap Integration](#44-sitemap-integration)
  - [4.5 404 Page](#45-404-page)
  - [4.6 Main Layout with Open Graph and Transitions](#46-main-layout-with-open-graph-and-transitions)
  - [4.7 Open Graph Quick Guide](#47-open-graph-quick-guide)
  - [4.8 Prettier Setup](#48-prettier-setup)
  - [4.9 Windows Execution Policy Fix](#49-windows-execution-policy-fix)
  - [4.10 Recovering from an npm Install Mistake](#410-recovering-from-an-npm-install-mistake)
  - [4.11 Running the Dev Server](#411-running-the-dev-server)
  - [4.12 Project Structure & Architecture](#412-project-structure--architecture)
- [5. Shared Website Setup — Vite + React + Next.js](#5-shared-website-setup--vite--react--nextjs)
  - [5.1 Tailwind Theme & Custom Fonts](#51-tailwind-theme--custom-fonts)
  - [5.2 Open Graph & HTML Metadata](#52-open-graph--html-metadata)
  - [5.3 `robots.txt`](#53-robotstxt)
  - [5.4 404 / Not Found Page](#54-404--not-found-page)
  - [5.5 Sitemap Integration](#55-sitemap-integration)
  - [5.6 Prettier Setup](#56-prettier-setup)
  - [5.7 Windows PowerShell Execution Policy / npm Recovery](#57-windows-powershell-execution-policy--npm-recovery)
  - [5.8 Development Servers](#58-development-servers)
  - [5.9 Common Project Structure](#59-common-project-structure)
- [6. Website Development — Vite + React](#6-website-development--vite--react)
  - [6.1 Scaffolding a New Project](#61-scaffolding-a-new-project)
  - [6.2 Install Base Dependencies](#62-install-base-dependencies)
  - [6.3 Add Tailwind CSS](#63-add-tailwind-css)
  - [6.4 vite.config.ts Reference](#64-viteconfigts-reference)
  - [6.5 Add React Router DOM](#65-add-react-router-dom)
  - [6.6 Layout Route with `Outlet`](#66-layout-route-with-outlet)
  - [6.7 Project Structure & Architecture](#67-project-structure--architecture)
- [7. Website Development — Next.js](#7-website-development--nextjs)
  - [7.1 Create a New Project](#71-create-a-new-project)
  - [7.2 Development](#72-development)
  - [7.3 Production Build](#73-production-build)
  - [7.4 Project Structure](#74-project-structure)
  - [7.5 Metadata Example](#75-metadata-example)
  - [7.6 Server and Client Components](#76-server-and-client-components)
  - [7.7 Production Notes](#77-production-notes)
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
  - [8.14 Traefik + Let's Encrypt + Three Websites](#814-traefik--lets-encrypt--three-websites)
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
- [10. Git and GitHub](#10-git-and-github)
  - [10.1 Initial Setup (First-Time Project)](#101-initial-setup-first-time-project)
  - [10.2 Daily Workflow](#102-daily-workflow)
  - [10.3 Branching](#103-branching)
  - [10.4 Other Useful Commands](#104-other-useful-commands)


# Developer Notes

Personal reference notes for setting up a web development environment, scaffolding websites with **Vite + React and Next.js**, and working with Git/GitHub. The classes, tags, colors, and fonts used in the examples below are illustrative — swap them for any generic CSS classes, framework, or design system.

## 1. Required Programs

| Program | Purpose | Link |
|---|---|---|
| Node.js | Required JavaScript runtime for local development, builds, Vite and Next.js | [nodejs.org/en/download](https://nodejs.org/en/download) |
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

## 4. Website Development — Astro + Tailwind

### 4.1 Project Setup

```bash
pnpm create astro@latest
```

### 4.2 Tailwind CSS Setup

Install Tailwind CSS via the Vite plugin (see [official Tailwind + Vite docs](https://tailwindcss.com/docs/installation/using-vite)):

```bash
pnpm add tailwindcss @tailwindcss/vite
```

`src/styles/global.css`:

```css
@import "tailwindcss";
```

### 4.3 Tailwind Theme, Custom Fonts & View Transitions

`global.css` can be extended with custom fonts (via Google Fonts or self-hosted), a `@theme` block to register them as Tailwind font tokens, and custom animations for Astro's View Transitions:

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
@import "tailwindcss";

@theme {
  --font-sans: 'Poppins', system-ui, sans-serif;
  --font-display: 'Space Grotesk', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', monospace;
}

::view-transition-old(root) {
  animation: fade-out 0.25s ease forwards;
}

::view-transition-new(root) {
  animation: fade-in 0.25s ease forwards;
}

@keyframes fade-out {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```

The `@theme` block exposes `--font-sans`, `--font-display`, and `--font-mono` as Tailwind utilities (`font-sans`, `font-display`, `font-mono`) usable directly in class names. The `::view-transition-*` rules define a simple crossfade for page navigations powered by `<ClientRouter />` (see [4.6](#46-main-layout-with-open-graph-and-transitions)).

### 4.4 Sitemap Integration

```bash
pnpm astro add sitemap
```

`astro.config.mjs`:

```js
// @ts-check
import { defineConfig } from 'astro/config';
import sitemap from '@astrojs/sitemap';
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  site: 'https://mysite.com', // real client URL
  integrations: [sitemap()],
  vite: {
    plugins: [tailwindcss()]
  }
});
```

### 4.5 404 Page

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

> The `class` names and layout structure here are just an example — swap them for any generic CSS classes or framework.

### 4.6 Main Layout with Open Graph and Transitions

`src/layouts/Layout.astro`:

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
  <body class="min-h-screen flex flex-col bg-[#faf9f7] text-[#1e1c1a] font-[Poppins,sans-serif]">
    <Navbar />
    <main class="flex-1">
      <slot />
    </main>
    <Footer />
  </body>
</html>
```

`ClientRouter` enables Astro's View Transitions for smooth navigation without full page reloads.

### 4.7 Open Graph Quick Guide

Open Graph controls how the site looks when shared on social media, WhatsApp, Slack, etc.

| Meta tag | Purpose |
|---|---|
| `og:title` | Title of the preview card |
| `og:description` | Short description (~155 characters max) |
| `og:image` | Preview image — minimum 1200×630px, publicly accessible |
| `og:url` | Canonical URL of the page |
| `og:type` | `website` for regular pages, `article` for blog posts |

The `og:image` must be uploaded to the server and accessible via an absolute URL — relative paths do not work. Tools to preview: [opengraph.xyz](https://www.opengraph.xyz/) and Meta's official sharing debugger.

### 4.8 Prettier Setup

```bash
pnpm add -D prettier
pnpm add -D prettier-plugin-astro
```

`package.json` scripts:

```json
"format": "prettier --write .",
"format:check": "prettier --check ."
```

```bash
pnpm install
```

### 4.9 Windows Execution Policy Fix

If `pnpm create astro@latest` or `pnpm install` throws a script execution error in PowerShell, open a new terminal in VS Code and run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

Confirm with `Y` and re-run the command.

> During Astro's setup, the CLI may ask about ESLint or other tools — press Enter to confirm the default selection and continue.

### 4.10 Recovering from an npm Install Mistake

If the project was installed with `npm` by mistake and needs to be reset:

```bash
# Remove node_modules and lockfiles
rm -rf node_modules package-lock.json

# Reinstall with pnpm
pnpm install
```

### 4.11 Running the Dev Server

```bash
pnpm dev
```

### 4.12 Project Structure & Architecture

Typical folder layout for an Astro-based site (adaptable to any generic web project):

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

**`public/`** — Static assets served as-is, without processing. Anything here is copied directly to the final build output at the same path.

- `favicon.svg` / `icon.png` — Site icon(s) referenced in the `<head>` of the layout.
- `images/` — Static images that don't need build-time optimization (e.g. Open Graph banner, logos).
- `robots.txt` — Tells search engine crawlers which pages they can access, and points them to the sitemap.

```
User-agent: *
Allow: /

Sitemap: https://mysite.com/sitemap-index.xml
```

**`src/components/`** — Reusable UI pieces used across multiple pages (e.g. `Hero.astro`, `Navbar.astro`, `Footer.astro`). Each component encapsulates its own markup, styles, and logic.

**`src/layouts/`** — Page wrappers that define the shared HTML shell (head, meta tags, Open Graph, `<Navbar />` / `<Footer />`, `<slot />` for page content). See [4.6](#46-main-layout-with-open-graph-and-transitions). Most projects only need one `Layout.astro`, but additional layouts can be added for different page types (e.g. a blog post layout).

**`src/pages/`** — File-based routing: each file becomes a route.

- `index.astro` → homepage (`/`)
- `terms-of-service.astro` → `/terms-of-service`
- `privacy-policy.astro` → `/privacy-policy`
- `contact.astro` → `/contact`
- `404.astro` → custom not-found page (see [4.5](#45-404-page))

**`src/styles/`** — Global stylesheets. `global.css` is where Tailwind is imported (see [4.2](#42-tailwind-css-setup)) and where fonts/theme tokens live (see [4.3](#43-tailwind-theme-custom-fonts--view-transitions)).

---

---

> **Deployment note:** Astro is included as a development reference, but it is not part of the Docker/server setup in this README. Astro sites are deployed directly to Cloudflare Pages.

## 5. Shared Website Setup — Vite + React + Next.js

These are the parts that are common or useful across both Vite + React and Next.js projects. Framework-specific configuration stays in sections 5 and 6.

### 5.1 Tailwind Theme & Custom Fonts

The same Tailwind theme pattern can be used in both projects:

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
@import "tailwindcss";

@theme {
  --font-sans: 'Poppins', system-ui, sans-serif;
  --font-display: 'Space Grotesk', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', monospace;
}
```

The `@theme` block exposes `font-sans`, `font-display`, and `font-mono` as Tailwind utility names.

### 5.2 Open Graph & HTML Metadata

Open Graph controls how the website looks when shared on social media, WhatsApp, Slack and similar platforms.

| Meta tag | Purpose |
|---|---|
| `og:title` | Title of the preview card |
| `og:description` | Short description |
| `og:image` | Preview image — preferably 1200×630px or larger |
| `og:url` | Canonical URL |
| `og:type` | `website` for normal pages |

Generic example:

```html
<meta name="description" content="Business description" />
<meta property="og:title" content="Business title" />
<meta property="og:description" content="Business description" />
<meta property="og:image" content="https://mysite.com/banner.png" />
<meta property="og:url" content="https://mysite.com" />
<meta property="og:type" content="website" />
```

For Vite + React, these tags normally live in `index.html`. For Next.js, use the Metadata API in `app/layout.tsx` or route-level metadata.

The image should be publicly reachable through an absolute HTTPS URL.

### 5.3 `robots.txt`

`robots.txt` is framework-independent. The final URL is always:

```text
https://mysite.com/robots.txt
```

For Vite, place it in:

```text
public/robots.txt
```

For Next.js, the same `public/robots.txt` approach works for a static file.

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

Replace the sitemap URL with the actual sitemap URL for the project.

### 5.4 404 / Not Found Page

Both frameworks need a not-found page, but the implementation is different.

**Vite + React:** with React Router, a catch-all route is enough:

```tsx
<Route path="*" element={<NotFound />} />
```

**Next.js App Router:** create:

```text
app/not-found.tsx
```

Example:

```tsx
export default function NotFound() {
  return (
    <main className="flex min-h-[60vh] flex-col items-center justify-center gap-4 text-center">
      <h1 className="text-6xl font-bold">404</h1>
      <p className="text-xl">Page not found</p>
      <a href="/" className="underline">
        Back to home
      </a>
    </main>
  )
}
```

### 5.5 Sitemap Integration

A sitemap is useful for SEO and should normally be submitted to Google Search Console.

**Vite + React:**

```bash
pnpm add -D vite-plugin-sitemap
```

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import Sitemap from 'vite-plugin-sitemap'

export default defineConfig({
  plugins: [
    react(),
    Sitemap({
      hostname: 'https://mysite.com',
    }),
  ],
})
```

**Next.js App Router:** create:

```text
app/sitemap.ts
```

Example:

```typescript
import type { MetadataRoute } from 'next'

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    {
      url: 'https://mysite.com',
      lastModified: new Date(),
    },
  ]
}
```

### 5.6 Prettier Setup

Install Prettier:

```bash
pnpm add -D prettier
```

Add these scripts to `package.json`:

```json
"format": "prettier --write .",
"format:check": "prettier --check ."
```

Then install dependencies normally:

```bash
pnpm install
```

### 5.7 Windows PowerShell Execution Policy / npm Recovery

If PowerShell blocks package scripts such as `pnpm install`, run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

If a project was accidentally installed with npm and you want to reset it back to pnpm:

```bash
rm -rf node_modules package-lock.json
pnpm install
```

### 5.8 Development Servers

Vite:

```bash
pnpm dev
```

Next.js:

```bash
pnpm dev
```

Typical defaults are:

```text
Vite     → http://localhost:5173
Next.js  → http://localhost:3000
```

Always use the exact URL printed by the terminal.

### 5.9 Common Project Structure

Both projects normally have:

```text
public/          # Favicon, images, robots.txt and other public files
components/      # Reusable React components
```

Vite + React commonly adds:

```text
src/
  components/
  pages/
  layouts/
  App.tsx
  main.tsx
```

Next.js commonly uses:

```text
app/
  layout.tsx
  page.tsx
  not-found.tsx
  sitemap.ts
```

The routing system is the main structural difference: Vite usually relies on React Router or another router, while Next.js provides routing through the framework itself.

---

## 6. Website Development — Vite + React

### 6.1 Scaffolding a New Project

```bash
pnpm create vite@latest project-name --template react-ts
cd project-name
```

### 6.2 Install Base Dependencies

```bash
pnpm install
```

### 6.3 Add Tailwind CSS

```bash
pnpm add tailwindcss @tailwindcss/vite
```

In `src/index.css` (or `src/styles/global.css`):

```css
@import "tailwindcss";
```

### 6.4 vite.config.ts Reference

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

### 6.5 Add React Router DOM

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

### 6.6 Layout Route with `Outlet`

For a shared shell (navbar + footer on every page, similar to the framework's `Layout.the framework`), use a layout route with React Router's `<Outlet />`, which renders whichever child route matched:

`src/layouts/MainLayout.tsx`:

```typescriptreact
import { Outlet } from 'react-router-dom'
import Navbar from '../components/Navbar'
import Footer from '../components/Footer'

export default function MainLayout() {
  return (
    <div className="min-h-screen bg-zinc-950 text-zinc-50 font-sans selection:bg-zinc-800 selection:text-white antialiased flex flex-col">
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

### 6.7 Project Structure & Architecture

Typical folder layout for a Vite + React site:

```
/
├── public/
│   ├── favicon.svg
│   ├── icon.png
│   └── images/
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

**`public/`** — Static assets served as-is; same role as described in [4.3 `robots.txt`](#44-robotstxt).

**`src/components/`** — Reusable UI pieces (`Hero.tsx`, `Navbar.tsx`, `Footer.tsx`) shared across pages.

**`src/layouts/`** — Shared page shells rendered via a layout route with `<Outlet />` (see [7.6](#57-layout-route-with-outlet)), equivalent to a shared application shell.

**`src/pages/`** — One component per route, registered manually in `App.tsx` when using React Router:

- `Home.tsx` → `/`
- `About.tsx` → `/about`
- `Contact.tsx` → `/contact`
- `TermsOfService.tsx` → `/terms-of-service`
- `PrivacyPolicy.tsx` → `/privacy-policy`
- `NotFound.tsx` → catch-all `*` route

**`src/global.css`** (or `index.css`) — Where Tailwind is imported and font/theme tokens are defined (see [5.1](#42-tailwind-theme--custom-fonts)).

**`index.html`** — The single HTML entry point; holds the `<head>` meta tags and Open Graph tags (see [5.2](#43-open-graph--html-metadata)), and the `#root` mount point for React.

---
## 7. Website Development — Next.js

Next.js is the second deployment target in this README. Unlike a normal Vite static build, a standard Next.js application runs a Node.js server in production.

### 7.1 Create a New Project

```bash
pnpm create next-app@latest my-next-site
cd my-next-site
pnpm install
```

A typical setup for this README is:

- TypeScript: `Yes`
- ESLint: `Yes`
- Tailwind CSS: `Yes`
- App Router: `Yes`

### 7.2 Development

```bash
pnpm dev
```

Usually:

```text
http://localhost:3000
```

### 7.3 Production Build

The normal production commands are:

```bash
pnpm build
pnpm start
```

`pnpm build` creates the optimized production output.

`pnpm start` runs the production Next.js server, normally on port `3000`.

### 7.4 Project Structure

A typical App Router project can look like:

```text
/
├── public/
│   ├── favicon.ico
│   ├── images/
│   └── robots.txt
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   ├── not-found.tsx
│   └── sitemap.ts
├── components/
├── lib/
├── package.json
├── next.config.ts
└── tsconfig.json
```

`app/page.tsx` is the homepage, `app/layout.tsx` is the root layout, `app/not-found.tsx` handles 404 pages and `app/sitemap.ts` can generate the sitemap.

### 7.5 Metadata Example

Use the Next.js Metadata API rather than manually maintaining a large HTML head:

```tsx
import type { Metadata } from 'next'

export const metadata: Metadata = {
  title: 'Business title',
  description: 'Business description',
  openGraph: {
    title: 'Business title',
    description: 'Business description',
    url: 'https://mysite.com',
    siteName: 'Business title',
    images: [
      {
        url: 'https://mysite.com/banner.png',
        width: 1200,
        height: 630,
      },
    ],
    type: 'website',
  },
}
```

### 7.6 Server and Client Components

App Router components are Server Components by default.

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

### 7.7 Production Notes

For the Docker deployment in section 7:

- A normal Next.js application should run `next start`.
- Do not treat a normal Next.js application as a `dist/` static site.
- The Next.js container listens internally on port `3000`.
- Traefik forwards HTTPS traffic to that internal port.

> Next.js can also be configured for static export, but that is a different deployment model. This README treats Next.js as a normal Node.js application running in Docker.

---

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

Ubuntu provides `docker-compose-v2` for the modern `docker compose` command. citeturn568230search0turn568230search2

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

The server needs SSH, HTTP and HTTPS.

First allow SSH:

```bash
sudo ufw allow OpenSSH
```

Then allow HTTP:

```bash
sudo ufw allow 80/tcp
```

Then HTTPS:

```bash
sudo ufw allow 443/tcp
```

Enable the firewall:

```bash
sudo ufw enable
```

Check it:

```bash
sudo ufw status verbose
```

The intended open services are approximately:

```text
22/tcp   SSH
80/tcp   HTTP
443/tcp  HTTPS
```

**Important:** allow SSH before enabling UFW. Otherwise you can lock yourself out.

Do not open application ports such as `3000` to the Internet. Traefik reaches the websites through Docker networking.

### 8.10 Create the Server Structure

Create the main folder:

```bash
sudo mkdir -p /opt/web
cd /opt/web
```

Create the Let's Encrypt storage:

```bash
sudo mkdir -p /opt/web/letsencrypt
sudo touch /opt/web/letsencrypt/acme.json
sudo chmod 600 /opt/web/letsencrypt/acme.json
```

The `acme.json` file stores Traefik's ACME account and certificate information. Keeping it restricted to the owner is an important baseline.

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
├── letsencrypt/
│   └── acme.json
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

### 8.14 Traefik + Let's Encrypt + Three Websites

Traefik is the only reverse proxy in this architecture.

It will:

1. Listen on server ports `80` and `443`.
2. Detect the Docker containers that have Traefik labels.
3. Match each domain to the correct container.
4. Redirect HTTP to HTTPS.
5. Request and renew Let's Encrypt certificates.

Traefik's Docker provider reads container labels. Using `exposedbydefault=false` means containers are ignored unless they explicitly opt in with `traefik.enable=true`. citeturn451080search6turn451080search5

This example uses the Let's Encrypt **HTTP-01** challenge. The domain must point to the server and HTTP/80 must be reachable from the Internet for validation. HTTPS/443 is also required for normal secure traffic. citeturn451080search2

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

      - --entrypoints.web.address=:80
      - --entrypoints.websecure.address=:443

      - --entrypoints.web.http.redirections.entrypoint.to=websecure
      - --entrypoints.web.http.redirections.entrypoint.scheme=https

      - --certificatesresolvers.letsencrypt.acme.httpchallenge=true
      - --certificatesresolvers.letsencrypt.acme.httpchallenge.entrypoint=web
      - --certificatesresolvers.letsencrypt.acme.email=YOUR_EMAIL@example.com
      - --certificatesresolvers.letsencrypt.acme.storage=/letsencrypt/acme.json

      - --log.level=INFO

    ports:
      - "80:80"
      - "443:443"

    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - ./letsencrypt:/letsencrypt

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
      - traefik.http.routers.web1.tls.certresolver=letsencrypt
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
      - traefik.http.routers.web2.tls.certresolver=letsencrypt
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
      - traefik.http.routers.web3.tls.certresolver=letsencrypt
      - traefik.http.services.web3.loadbalancer.server.port=80

networks:
  web:
    external: true
```

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

**Let's Encrypt**

```text
--certificatesresolvers.letsencrypt.acme.httpchallenge=true
```

Traefik uses the HTTP-01 challenge to obtain certificates.

**Persistent certificates**

```text
./letsencrypt:/letsencrypt
```

Without persistent storage, recreating the Traefik container would lose the ACME data.

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

Before HTTPS can work, the domains must point to the server.

Example:

```text
site1.example.com → SERVER_PUBLIC_IP
site2.example.com → SERVER_PUBLIC_IP
site3.example.com → SERVER_PUBLIC_IP
```

Use `A` records for IPv4 addresses.

The important rule is:

```text
Domain → server running Traefik → ports 80/443
```

You can verify resolution from a computer with:

```bash
nslookup site1.example.com
```

or:

```bash
curl -I http://site1.example.com
```

Do not move on to HTTPS troubleshooting until the domain reaches the correct server.

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

Suppose only `web2` changed.

Replace the project files in:

```text
/opt/web/web2
```

Then run:

```bash
docker compose up --build -d web2
```

Only `web2` is rebuilt/recreated. Traefik continues running and the other websites are not rebuilt.

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

Fail2ban is an additional layer. It does not replace updates, firewall rules or SSH keys.

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

**Let's Encrypt certificate is not issued**

Check in this order:

1. DNS points to the correct server.
2. UFW allows port `80`.
3. The server is reachable from the Internet on port `80`.
4. The `Host(...)` rule exactly matches the domain.
5. `/opt/web/letsencrypt/acme.json` exists.
6. Traefik logs show the ACME process.

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
[ ] acme.json exists with restricted permissions
[ ] DNS records point to the server
[ ] Vite Dockerfile builds correctly
[ ] Next.js Dockerfile builds correctly
[ ] Traefik routes use the correct domains
[ ] Let's Encrypt certificates are issued
[ ] Fail2ban is running
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

### 9.3 Cloudflare Domains & Rules

- **DNS**: if the domain is registered with Cloudflare (or just uses Cloudflare as DNS), add/verify the records under **DNS → Records**. Pages projects usually just need a `CNAME` pointing to the `*.pages.dev` deployment, added automatically when attaching a custom domain.
- **SSL/TLS**: keep the encryption mode set to **Full** or **Full (strict)** for Pages projects.
- **Redirect rules**: under **Rules → Redirect Rules**, common basics are forcing `www` → apex (or the reverse) and forcing `https`.
- **Page Rules / Cache Rules**: useful for basics like always redirecting `http://` to `https://`, or setting cache behavior for static assets under `/images/*` or `/assets/*`.

---
## 10. Git and GitHub

### 10.1 Initial Setup (First-Time Project)

Use these commands when starting a brand-new project locally and connecting it to a GitHub repository.

| Command | Description |
|---|---|
| `git init` | Initializes a new, empty Git repository in the local project folder |
| `git add .` | Stages all modified and new files, preparing them to be saved |
| `git commit -m "initial commit"` | Saves staged changes locally with a descriptive message |
| `git branch -M main` | Renames the default local branch to `main` |
| `git remote add origin <repository-URL>` | Links the local repository to the remote repository on GitHub |
| `git push -u origin main` | Uploads local commits to the `main` branch on GitHub for the first time |

### 10.2 Daily Workflow

Use these steps every time files are edited and need to be pushed to GitHub.

| Command | Description |
|---|---|
| `git status` | Shows which files have been modified or added (safe to run anytime) |
| `git add .` | Stages the latest changes |
| `git commit -m "describe your changes here"` | Saves changes locally with a message explaining what was done |
| `git push` | Uploads newly saved local commits to GitHub |

### 10.3 Branching

Branches allow working on new features safely without breaking the live site.

| Command | Description |
|---|---|
| `git branch` | Lists all local branches and shows the current one |
| `git branch <branch-name>` | Creates a new branch |
| `git checkout <branch-name>` (or `git switch <branch-name>`) | Switches to the specified branch |
| `git checkout -b <branch-name>` (or `git switch -c <branch-name>`) | Creates a new branch and switches to it immediately |
| `git merge <branch-name>` | Merges changes from the specified branch into the current branch |

### 10.4 Other Useful Commands

| Command | Description |
|---|---|
| `git pull` | Downloads and integrates the latest changes from GitHub into the local project (essential when working with others) |
| `git clone <repository-URL>` | Downloads an existing GitHub repository onto the local machine |
| `git log` | Displays the history of all commits made in the repository |
