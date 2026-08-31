# Developer Notes

Personal reference notes for setting up a web development environment, scaffolding a website (Astro or Vite + React), and working with Git/GitHub. The classes, tags, colors, and fonts used in the examples below are illustrative — swap them for any generic CSS classes, framework, or design system.

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
- [5. Website Development — Vite + React](#5-website-development--vite--react)
  - [5.1 Scaffolding a New Project](#51-scaffolding-a-new-project)
  - [5.2 Install Base Dependencies](#52-install-base-dependencies)
  - [5.3 Add Tailwind CSS](#53-add-tailwind-css)
  - [5.4 Tailwind Theme & Custom Fonts](#54-tailwind-theme--custom-fonts)
  - [5.5 vite.config.ts Reference](#55-viteconfigts-reference)
  - [5.6 Add React Router DOM](#56-add-react-router-dom)
  - [5.7 Layout Route with `Outlet`](#57-layout-route-with-outlet)
  - [5.8 404 / Not Found Page](#58-404--not-found-page)
  - [5.9 Open Graph in Vite](#59-open-graph-in-vite)
  - [5.10 robots.txt Reference](#510-robotstxt-reference)
  - [5.11 Sitemap Integration](#511-sitemap-integration)
  - [5.12 Prettier Setup](#512-prettier-setup)
  - [5.13 Windows Execution Policy Fix / npm Recovery](#513-windows-execution-policy-fix--npm-recovery)
  - [5.14 Running the Dev Server](#514-running-the-dev-server)
  - [5.15 Project Structure & Architecture](#515-project-structure--architecture)
- [6. Deployment](#6-deployment)
  - [6.1 Google Search Console](#61-google-search-console)
  - [6.2 Cloudflare Pages](#62-cloudflare-pages)
  - [6.3 Cloudflare Domains & Rules](#63-cloudflare-domains--rules)
- [7. Git and GitHub](#7-git-and-github)
  - [7.1 Initial Setup (First-Time Project)](#71-initial-setup-first-time-project)
  - [7.2 Daily Workflow](#72-daily-workflow)
  - [7.3 Branching](#73-branching)
  - [7.4 Other Useful Commands](#74-other-useful-commands)

---

## 1. Required Programs

| Program | Purpose | Link |
|---|---|---|
| Node.js | JavaScript runtime required to run the tooling below | [nodejs.org/en/download](https://nodejs.org/en/download) |
| pnpm | Fast, disk-efficient package manager | [pnpm.io/installation](https://pnpm.io/installation) |

Install Node.js first, then install pnpm.

---

## 2. VS Code Extensions

| Extension | Purpose |
|---|---|
| Astro | Language support for `.astro` files |
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

## 5. Website Development — Vite + React

### 5.1 Scaffolding a New Project

```bash
pnpm create vite@latest project-name --template react-ts
cd project-name
```

### 5.2 Install Base Dependencies

```bash
pnpm install
```

### 5.3 Add Tailwind CSS

```bash
pnpm add tailwindcss @tailwindcss/vite
```

In `src/index.css` (or `src/styles/global.css`):

```css
@import "tailwindcss";
```

### 5.4 Tailwind Theme & Custom Fonts

Same pattern as in Astro (see [4.3](#43-tailwind-theme-custom-fonts--view-transitions)) — import fonts and register them as theme tokens directly in the global stylesheet:

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
@import "tailwindcss";

@theme {
  --font-sans: 'Poppins', system-ui, sans-serif;
  --font-display: 'Space Grotesk', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', monospace;
}
```

The `::view-transition-*` rules from the Astro example are Astro-specific (they hook into `<ClientRouter />`) and don't apply here unless the [View Transitions API](https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API) is wired up manually in React.

### 5.5 vite.config.ts Reference

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

### 5.6 Add React Router DOM

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

### 5.7 Layout Route with `Outlet`

For a shared shell (navbar + footer on every page, similar to Astro's `Layout.astro`), use a layout route with React Router's `<Outlet />`, which renders whichever child route matched:

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

### 5.8 404 / Not Found Page

Same idea as the Astro 404 page (see [4.5](#45-404-page)) — short and generic. `Link` is used instead of a plain `<a>` so navigation stays client-side (no full page reload):

`src/pages/NotFound.tsx`:

```typescriptreact
import { Link } from 'react-router-dom';

export default function NotFound() {
  return (
    <section className="flex flex-col items-center justify-center min-h-[60vh] gap-4 text-center px-6">
      <h1 className="text-6xl font-bold">404</h1>
      <p className="text-xl">Page not found</p>
      <Link to="/" className="underline">
        Back to home
      </Link>
    </section>
  );
}
```

### 5.9 Open Graph in Vite

In Vite/React projects the base HTML is `index.html` — this is Vite's actual entry point (there's no separate layout file like Astro's `Layout.astro`; the `<head>` lives directly in this file). Add the meta tags directly in the `<head>`:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Business title</title>
    <meta name="description" content="Business description" />
    <meta property="og:title" content="Business title" />
    <meta property="og:description" content="Business description" />
    <meta property="og:image" content="https://mysite.com/banner.png" />
    <meta property="og:url" content="https://mysite.com" />
    <meta property="og:type" content="website" />
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

If a plain `index.html` is needed without Open Graph (e.g. before the site is ready to be shared publicly), just remove the `og:*` meta lines and the `description` line above.

**Optional — block indexing while in development:**

```html
<meta name="robots" content="noindex,nofollow" />
```

Add this inside `<head>` to keep search engines from indexing a staging/preview deployment. Remove it once the site is ready to go live and be indexed.

For per-route dynamic Open Graph tags in React, use [react-helmet-async](https://github.com/staylor/react-helmet-async).

### 5.10 robots.txt Reference

`robots.txt` lives at `public/robots.txt` and works the same way regardless of framework (Astro, Vite, etc.) — it's a static file served at the site root and read by crawlers before anything else.

**Allow indexing** (default for a live production site):

```
User-agent: *
Allow: /

Sitemap: https://mysite.com/sitemap.xml
```

**Deny indexing** (staging/preview deployments, or a site not ready to go public):

```
User-agent: *
Disallow: /
```

`Disallow: /` is broader than the `noindex` meta tag from [5.9](#59-open-graph-in-vite) — it tells crawlers not to even crawl the site, whereas `noindex` only stops indexing of pages they do crawl. For staging environments, using both together gives the strongest guarantee.

### 5.11 Sitemap Integration

```bash
pnpm add -D vite-plugin-sitemap
```

`vite.config.ts`:

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react' // or another framework plugin (vue, svelte, etc.)
import Sitemap from 'vite-plugin-sitemap'

export default defineConfig({
  plugins: [
    react(),
    Sitemap({
      hostname: 'https://mysite.com', // replace with the real site URL
    }),
  ],
})
```

**Dynamic routes** — if the app has routes generated at runtime (e.g. blog posts loaded from an API), pass them to the plugin via `dynamicRoutes`:

```typescript
Sitemap({
  hostname: 'https://mysite.com',
  dynamicRoutes: [
    '/blog/post-1',
    '/blog/post-2',
  ],
})
```

### 5.12 Prettier Setup

```bash
pnpm add -D prettier
```

`package.json` scripts:

```json
"format": "prettier --write .",
"format:check": "prettier --check ."
```

```bash
pnpm install
```

> Unlike the Astro setup, `prettier-plugin-astro` isn't needed here — plain Prettier already handles `.ts`/`.tsx` files.

### 5.13 Windows Execution Policy Fix / npm Recovery

Same fix as in Astro (see [4.9](#49-windows-execution-policy-fix) and [4.10](#410-recovering-from-an-npm-install-mistake)):

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

```bash
rm -rf node_modules package-lock.json
pnpm install
```

### 5.14 Running the Dev Server

```bash
pnpm dev
```

### 5.15 Project Structure & Architecture

Typical folder layout for a Vite + React site:

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

**`public/`** — Static assets served as-is; same role as in Astro (see [4.12](#412-project-structure--architecture)), including `robots.txt` (see [5.10](#510-robotstxt-reference) for allow/deny variants):

```
User-agent: *
Allow: /

Sitemap: https://mysite.com/sitemap-index.xml
```

**`src/components/`** — Reusable UI pieces (`Hero.tsx`, `Navbar.tsx`, `Footer.tsx`) shared across pages.

**`src/layouts/`** — Shared page shells rendered via a layout route with `<Outlet />` (see [5.7](#57-layout-route-with-outlet)), equivalent to Astro's `Layout.astro`.

**`src/pages/`** — One component per route, registered manually in `App.tsx` (React Router doesn't do file-based routing out of the box like Astro does):

- `Home.tsx` → `/`
- `About.tsx` → `/about`
- `Contact.tsx` → `/contact`
- `TermsOfService.tsx` → `/terms-of-service`
- `PrivacyPolicy.tsx` → `/privacy-policy`
- `NotFound.tsx` → catch-all `*` route

**`src/global.css`** (or `index.css`) — Where Tailwind is imported and font/theme tokens are defined (see [5.4](#54-tailwind-theme--custom-fonts)).

**`index.html`** — The single HTML entry point; holds the `<head>` meta tags and Open Graph tags (see [5.9](#59-open-graph-in-vite)), and the `#root` mount point for React.

---

## 6. Deployment

### 6.1 Google Search Console

1. Go to [Google Search Console](https://search.google.com/search-console) and add a new property using the site's domain or URL prefix.
2. Verify ownership — via DNS TXT record (domain property) or an HTML file/meta tag (URL-prefix property), depending on the method chosen.
3. Once verified, submit the sitemap under **Sitemaps** using the sitemap URL generated by the project (e.g. `https://mysite.com/sitemap-index.xml` for Astro, or the path configured for `vite-plugin-sitemap`).
4. Use the **URL Inspection** tool to request indexing for key pages after the first deploy.

### 6.2 Cloudflare Pages

1. In the [Cloudflare dashboard](https://dash.cloudflare.com/), go to **Workers & Pages → Create → Pages**, and connect the GitHub repository.
2. Configure the build settings:
   - **Framework preset**: Astro or Vite (Cloudflare has presets for both).
   - **Build command**: `pnpm build` (or `npm run build`).
   - **Build output directory**: `dist` (default for both Astro and Vite).
3. Add any required environment variables under **Settings → Environment variables**.
4. Every push to the connected branch (e.g. `main`) triggers an automatic deploy; other branches get preview deployments.
5. Under **Custom domains**, attach the production domain once it's ready.

### 6.3 Cloudflare Domains & Rules

- **DNS**: if the domain is registered with Cloudflare (or just uses Cloudflare as DNS), add/verify the records under **DNS → Records**. Pages projects usually just need a `CNAME` pointing to the `*.pages.dev` deployment, added automatically when attaching a custom domain.
- **SSL/TLS**: keep the encryption mode set to **Full** or **Full (strict)** for Pages projects.
- **Redirect rules**: under **Rules → Redirect Rules**, common basics are forcing `www` → apex (or the reverse) and forcing `https`.
- **Page Rules / Cache Rules**: useful for basics like always redirecting `http://` to `https://`, or setting cache behavior for static assets under `/images/*` or `/assets/*`.

---

## 7. Git and GitHub

### 7.1 Initial Setup (First-Time Project)

Use these commands when starting a brand-new project locally and connecting it to a GitHub repository.

| Command | Description |
|---|---|
| `git init` | Initializes a new, empty Git repository in the local project folder |
| `git add .` | Stages all modified and new files, preparing them to be saved |
| `git commit -m "initial commit"` | Saves staged changes locally with a descriptive message |
| `git branch -M main` | Renames the default local branch to `main` |
| `git remote add origin <repository-URL>` | Links the local repository to the remote repository on GitHub |
| `git push -u origin main` | Uploads local commits to the `main` branch on GitHub for the first time |

### 7.2 Daily Workflow

Use these steps every time files are edited and need to be pushed to GitHub.

| Command | Description |
|---|---|
| `git status` | Shows which files have been modified or added (safe to run anytime) |
| `git add .` | Stages the latest changes |
| `git commit -m "describe your changes here"` | Saves changes locally with a message explaining what was done |
| `git push` | Uploads newly saved local commits to GitHub |

### 7.3 Branching

Branches allow working on new features safely without breaking the live site.

| Command | Description |
|---|---|
| `git branch` | Lists all local branches and shows the current one |
| `git branch <branch-name>` | Creates a new branch |
| `git checkout <branch-name>` (or `git switch <branch-name>`) | Switches to the specified branch |
| `git checkout -b <branch-name>` (or `git switch -c <branch-name>`) | Creates a new branch and switches to it immediately |
| `git merge <branch-name>` | Merges changes from the specified branch into the current branch |

### 7.4 Other Useful Commands

| Command | Description |
|---|---|
| `git pull` | Downloads and integrates the latest changes from GitHub into the local project (essential when working with others) |
| `git clone <repository-URL>` | Downloads an existing GitHub repository onto the local machine |
| `git log` | Displays the history of all commits made in the repository |
