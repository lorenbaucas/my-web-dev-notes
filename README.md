# Developer Notes

Personal reference notes for setting up a web development environment, scaffolding a website, and working with Git/GitHub. The framework/styling examples below use Astro + Tailwind CSS, but the tags, classes, and commands can be swapped for any generic stack.

## Index

- [1. Required Programs](#1-required-programs)
- [2. VS Code Extensions](#2-vs-code-extensions)
- [3. VS Code Keyboard Shortcuts](#3-vs-code-keyboard-shortcuts)
- [4. Website Development (Astro + Tailwind)](#4-website-development-astro--tailwind)
  - [4.1 Project Setup](#41-project-setup)
  - [4.2 Tailwind CSS Setup](#42-tailwind-css-setup)
  - [4.3 Sitemap Integration](#43-sitemap-integration)
  - [4.4 404 Page](#44-404-page)
  - [4.5 Main Layout with Open Graph and Transitions](#45-main-layout-with-open-graph-and-transitions)
  - [4.6 Open Graph Quick Guide](#46-open-graph-quick-guide)
  - [4.7 Prettier Setup](#47-prettier-setup)
  - [4.8 Windows Execution Policy Fix](#48-windows-execution-policy-fix)
  - [4.9 Recovering from an npm Install Mistake](#49-recovering-from-an-npm-install-mistake)
  - [4.10 Running the Dev Server](#410-running-the-dev-server)
  - [4.11 Project Structure & Architecture](#411-project-structure--architecture)
- [5. Git and GitHub](#5-git-and-github)
  - [5.1 Initial Setup (First-Time Project)](#51-initial-setup-first-time-project)
  - [5.2 Daily Workflow](#52-daily-workflow)
  - [5.3 Branching](#53-branching)
  - [5.4 Other Useful Commands](#54-other-useful-commands)

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

### General

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

### Editing

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

### Navigation

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

## 4. Website Development (Astro + Tailwind)

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

### 4.3 Sitemap Integration

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

### 4.4 404 Page

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

### 4.5 Main Layout with Open Graph and Transitions

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

### 4.6 Open Graph Quick Guide

Open Graph controls how the site looks when shared on social media, WhatsApp, Slack, etc.

| Meta tag | Purpose |
|---|---|
| `og:title` | Title of the preview card |
| `og:description` | Short description (~155 characters max) |
| `og:image` | Preview image — minimum 1200×630px, publicly accessible |
| `og:url` | Canonical URL of the page |
| `og:type` | `website` for regular pages, `article` for blog posts |

The `og:image` must be uploaded to the server and accessible via an absolute URL — relative paths do not work. Tools to preview: [opengraph.xyz](https://www.opengraph.xyz/) and Meta's official sharing debugger.

### 4.7 Prettier Setup

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

### 4.8 Windows Execution Policy Fix

If `pnpm create astro@latest` or `pnpm install` throws a script execution error in PowerShell, open a new terminal in VS Code and run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

Confirm with `Y` and re-run the command.

> During Astro's setup, the CLI may ask about ESLint or other tools — press Enter to confirm the default selection and continue.

### 4.9 Recovering from an npm Install Mistake

If the project was installed with `npm` by mistake and needs to be reset:

```bash
# Remove node_modules and lockfiles
rm -rf node_modules package-lock.json

# Reinstall with pnpm
pnpm install
```

### 4.10 Running the Dev Server

```bash
pnpm dev
```

### 4.11 Project Structure & Architecture

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

**`src/layouts/`** — Page wrappers that define the shared HTML shell (head, meta tags, Open Graph, `<Navbar />` / `<Footer />`, `<slot />` for page content). See [4.5 Main Layout with Open Graph and Transitions](#45-main-layout-with-open-graph-and-transitions). Most projects only need one `Layout.astro`, but additional layouts can be added for different page types (e.g. a blog post layout).

**`src/pages/`** — File-based routing: each file becomes a route.

- `index.astro` → homepage (`/`)
- `terms-of-service.astro` → `/terms-of-service`
- `privacy-policy.astro` → `/privacy-policy`
- `contact.astro` → `/contact`
- `404.astro` → custom not-found page (see [4.4 404 Page](#44-404-page))

**`src/styles/`** — Global stylesheets. `global.css` is where Tailwind is imported (see [4.2 Tailwind CSS Setup](#42-tailwind-css-setup)) and where any base/reset styles live.

---

## 5. Git and GitHub

### 5.1 Initial Setup (First-Time Project)

Use these commands when starting a brand-new project locally and connecting it to a GitHub repository.

| Command | Description |
|---|---|
| `git init` | Initializes a new, empty Git repository in the local project folder |
| `git add .` | Stages all modified and new files, preparing them to be saved |
| `git commit -m "initial commit"` | Saves staged changes locally with a descriptive message |
| `git branch -M main` | Renames the default local branch to `main` |
| `git remote add origin <repository-URL>` | Links the local repository to the remote repository on GitHub |
| `git push -u origin main` | Uploads local commits to the `main` branch on GitHub for the first time |

### 5.2 Daily Workflow

Use these steps every time files are edited and need to be pushed to GitHub.

| Command | Description |
|---|---|
| `git status` | Shows which files have been modified or added (safe to run anytime) |
| `git add .` | Stages the latest changes |
| `git commit -m "describe your changes here"` | Saves changes locally with a message explaining what was done |
| `git push` | Uploads newly saved local commits to GitHub |

### 5.3 Branching

Branches allow working on new features safely without breaking the live site.

| Command | Description |
|---|---|
| `git branch` | Lists all local branches and shows the current one |
| `git branch <branch-name>` | Creates a new branch |
| `git checkout <branch-name>` (or `git switch <branch-name>`) | Switches to the specified branch |
| `git checkout -b <branch-name>` (or `git switch -c <branch-name>`) | Creates a new branch and switches to it immediately |
| `git merge <branch-name>` | Merges changes from the specified branch into the current branch |

### 5.4 Other Useful Commands

| Command | Description |
|---|---|
| `git pull` | Downloads and integrates the latest changes from GitHub into the local project (essential when working with others) |
| `git clone <repository-URL>` | Downloads an existing GitHub repository onto the local machine |
| `git log` | Displays the history of all commits made in the repository |
