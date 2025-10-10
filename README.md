# Guitar Store (React + TypeScript)

A small e-commerce demo for guitars built with **React 19**, **TypeScript**, and **Vite**. It features a product catalog, a client-side shopping cart with quantity controls, and **localStorage** persistence. The UI is styled with a **custom-compiled Bootstrap 5** CSS build (CSS-only; no Bootstrap JS runtime), keeping dependencies minimal and loads fast.

<p align="left">
  <a href="https://guitar.missaelr.com"><img alt="Live Demo" src="https://img.shields.io/badge/Live-Demo-1f6feb?style=flat-square"></a>
  <a href="https://github.com/zpymis/guitar"><img alt="GitHub Repo" src="https://img.shields.io/badge/GitHub-Repository-24292e?logo=github&logoColor=white&style=flat-square"></a>
  <img alt="React" src="https://img.shields.io/badge/React-19-61dafb?logo=react&logoColor=000&style=flat-square">
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-5.x-3178c6?logo=typescript&logoColor=white&style=flat-square">
  <img alt="Vite" src="https://img.shields.io/badge/Vite-7.x-646cff?logo=vite&logoColor=white&style=flat-square">
  <img alt="Bootstrap" src="https://img.shields.io/badge/Bootstrap-5.2-7952B3?logo=bootstrap&logoColor=white&style=flat-square">
  <a href="./LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-brightgreen?style=flat-square"></a>
</p>

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Accessibility](#accessibility)
- [Performance Notes](#performance-notes)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Available Scripts](#available-scripts)
- [Usage Notes](#usage-notes)
- [Roadmap](#roadmap)
- [License](#license)
- [Author](#author)

---

## Overview

This project showcases a **React + TypeScript** cart flow with clean state modeling and derived values. Products are loaded from a local dataset, the cart is persisted in **localStorage**, and quantity controls are guarded with min/max rules. The app ships as a static site (no backend), making it easy to host on any CDN. Styling comes from a **compiled Bootstrap 5.2** stylesheet baked into `src/index.css`, using grid/utilities and a small set of custom rules.

---

## Features

- Product catalog grid with image, name, description, and price.
- Shopping cart:
  - Add/remove items, increment/decrement quantity.
  - Min/Max quantity guard (1–5 per item).
  - Derived state via `useMemo` (`isEmpty`, `cartTotal`).
  - Persistence in `localStorage`.
- Bootstrap-based UI (CSS-only):
  - Compiled grid/utilities for responsive layout.
  - No Bootstrap JS or third-party UI runtime.
- Lean dependency footprint and fast static hosting.

---

## Accessibility

- Informative `alt` attributes on images.
- Native `button` elements for all actions (not divs), ensuring keyboard and assistive tech support.
- Predictable focus order and semantic HTML structure (header/main/footer).
- Clear copy for empty states (e.g., “El carrito está vacío”).
- Benefits from Bootstrap’s baseline focus/typography defaults in the compiled CSS.

Tip: If you expand the UI, consider adding `aria-live` updates for cart changes and `aria-label`/`aria-controls` for complex widgets.

---

## Performance Notes

- Built with **Vite** and **SWC** for fast dev/preview and optimized production builds.
- Single-page static hosting; no blocking third-party JS.
- Images are served from `/public/img`; keep explicit dimensions and prefer modern formats (AVIF/WebP) when available.
- The Bootstrap stylesheet is **compiled into a single CSS file**; if you need smaller bundles, consider purging unused utilities.

---

## Tech Stack

- React 19 + React DOM 19
- TypeScript 5.x
- Vite 7 with `@vitejs/plugin-react-swc`
- Bootstrap 5.2 (CSS-only, custom compile)
- ESLint 9 (React Hooks + Refresh configs)

---

## Project Structure

    .
    ├─ public/
    │  └─ img/                  # product images
    ├─ src/
    │  ├─ components/
    │  │  ├─ Guitar.tsx         # product card
    │  │  └─ Header.tsx         # logo + cart dropdown/table
    │  ├─ data/
    │  │  └─ db.ts              # local product dataset
    │  ├─ hooks/
    │  │  └─ useCart.ts         # cart state, guards, persistence, totals
    │  ├─ types/
    │  │  ├─ index.ts           # Guitar, CartItem types
    │  │  └─ css.d.ts           # CSS module typing
    │  ├─ App.tsx
    │  ├─ index.css             # compiled Bootstrap + small custom rules
    │  └─ main.tsx              # React root
    ├─ index.html               # Vite entry
    ├─ eslint.config.js
    ├─ tsconfig.*.json
    ├─ vite.config.ts
    └─ package.json

---

## Getting Started

Prerequisite: Node.js 18+

    # 1) Install
    pnpm i         # or: npm i  |  yarn

    # 2) Run dev server
    pnpm dev       # or: npm run dev  |  yarn dev

    # 3) Build for production
    pnpm build     # or: npm run build

    # 4) Preview the production build locally
    pnpm preview   # or: npm run preview

The app is fully static—deploy the `dist/` folder to any static host (Netlify, Vercel, GitHub Pages, Nginx, etc.).

---

## Available Scripts

- `dev` — Vite dev server with HMR
- `build` — Type-check + production build
- `preview` — Preview the production build locally
- `lint` — ESLint over the project

---

## Usage Notes

- Quantity bounds: edit `MIN_ITEMS` and `MAX_ITEMS` in `src/hooks/useCart.ts` if you need different limits.
- Cart key: the cart persists under the `localStorage` key `"cart"`.
- Currency/formatting: prices are stored as numbers; adapt formatting/intl as needed.
- Assets: product images live in `/public/img`. Keep `width`/`height` (or CSS `aspect-ratio`) to avoid layout shifts.
- Styling / Bootstrap:
  - The project uses a **compiled Bootstrap 5** CSS bundle inside `src/index.css`.
  - If you want to customize theme colors/spacing at the source, recompile Bootstrap with your Sass variables (SCSS sources are not included here).
  - Alternatively, override CSS variables/utilities or add small custom rules on top of the compiled CSS.

---

## Roadmap

- Add currency formatting with `Intl.NumberFormat`.
- Extract cart UI into a modal/drawer with focus trapping and `aria-live` for updates.
- Replace JPGs with AVIF/WebP and add `srcset/sizes` for responsive images.
- Optionally purge unused Bootstrap utilities (e.g., PurgeCSS/LightningCSS) for smaller CSS payloads.

---

## License

MIT — see [LICENSE](./LICENSE) for details.

---

## Author

**Missael Rangel** — Frontend Developer (React/TypeScript)  
🔗 [missaelr.com/en](https://missaelr.com/en) · [LinkedIn](https://www.linkedin.com/in/missaelrangel) · [GitHub](https://github.com/zpymis)
