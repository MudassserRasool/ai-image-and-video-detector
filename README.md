# AI Image & Video Detector

A client-side web application foundation for analyzing images and video in the browser. The repository ships a **React 18** single-page application scaffolded with **Vite 6**, ESLint 9 (flat config), and an initial `FileUploader` module reserved for future upload and detection flows.

---

## Table of contents

1. [Overview](#overview)
2. [System requirements](#system-requirements)
3. [Quick start](#quick-start)
4. [NPM scripts](#npm-scripts)
5. [Project structure](#project-structure)
6. [Technology stack](#technology-stack)
7. [Development guidelines](#development-guidelines)
8. [Production build](#production-build)
9. [Repository status](#repository-status)

---

## Overview

This project is a **frontend-only** SPA intended to host image and video inspection workflows (for example, model-assisted or heuristic detection). The current codebase provides:

- A Vite-powered dev server with Hot Module Replacement (HMR)
- React 18 in strict mode via the modern JSX runtime
- ESLint with React, React Hooks, and React Refresh plugins
- A placeholder `FileUploader` component under `src/components/FileUploader/` (not yet integrated into `App.jsx`)

There is **no backend service** in this repository; any future inference or storage must be integrated explicitly (separate services, edge functions, or third-party APIs).

---

## System requirements

| Requirement | Notes |
|-------------|--------|
| **Node.js** | Current LTS (e.g. 20.x or 22.x) recommended. Vite 6 expects a reasonably recent runtime. |
| **npm** | Used for dependency installation and scripts (ships with Node). |

Verify versions:

```bash
node --version
npm --version
```

---

## Quick start

Clone the repository, install dependencies, and start the development server:

```bash
git clone https://github.com/MudassserRasool/ai-image-and-video-detector.git
cd ai-image-and-video-detector
npm install
npm run dev
```

By default, Vite serves the application at `http://localhost:5173`. The terminal prints the exact URL and port if they differ.

---

## NPM scripts

| Script | Command | Purpose |
|--------|---------|---------|
| **Development** | `npm run dev` | Starts the Vite dev server with HMR. |
| **Production build** | `npm run build` | Emits an optimized static bundle to `dist/`. |
| **Preview** | `npm run preview` | Serves the contents of `dist/` locally (use after `build`). |
| **Lint** | `npm run lint` | Runs ESLint across the JavaScript/JSX source tree. |

---

## Project structure

```
.
├── public/                 # Static assets copied as-is to the build output
├── src/
│   ├── assets/             # Images and other bundled assets
│   ├── components/
│   │   └── FileUploader/   # Placeholder uploader UI (extend for media input)
│   ├── App.jsx             # Root application component
│   ├── App.css
│   ├── main.jsx            # React root and StrictMode entry
│   └── index.css           # Global styles
├── index.html              # HTML shell; mounts `#root`
├── vite.config.js          # Vite configuration (@vitejs/plugin-react)
├── eslint.config.js        # ESLint flat config (browser globals, React rules)
├── package.json
└── README.md
```

---

## Technology stack

| Layer | Choice | Rationale |
|-------|--------|-----------|
| **UI** | React 18 | Component model, ecosystem, and concurrent-ready APIs. |
| **Build / dev** | Vite 6 | Fast cold start, native ESM in dev, sensible defaults for SPAs. |
| **Transpilation** | `@vitejs/plugin-react` | Babel-based Fast Refresh for `.jsx` files. |
| **Linting** | ESLint 9 + flat config | Centralized quality gates aligned with current ESLint guidance. |

---

## Development guidelines

1. **Run lint before pushing** — `npm run lint` must pass unless you are explicitly disabling a rule with team agreement and documentation.
2. **Prefer functional components and hooks** — Matches React 18 defaults and existing entry (`StrictMode` in `main.jsx`).
3. **Keep environment-specific configuration out of source** — Use Vite env files (`.env`, `.env.local`) for keys and endpoints; never commit secrets.
4. **Integrate new UI at the app root** — Wire new components through `App.jsx` (or a future router) rather than ad-hoc script tags.

---

## Production build

```bash
npm run build
```

Artifacts are written to `dist/`. Deploy that directory to any static host (CDN, object storage with website mode, or a reverse proxy). For local verification:

```bash
npm run preview
```

---

## Repository status

The package name (`ai-image-and-video-detector`) reflects the **product direction**. The **default `App.jsx`** still matches the upstream Vite + React template (counter demo). Media upload and detection logic are **not yet implemented**; `FileUploader.jsx` is a stub intended as the integration point for file selection and subsequent processing.

When you extend the app, update this section (and add API or model documentation) so operators and contributors share a single source of truth.

---

## License

This repository does not include a `LICENSE` file at the root. Add one before external distribution or clarify terms with the repository owner.
