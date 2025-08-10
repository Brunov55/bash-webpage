# Bash Programming (Astro)

Beginner‑friendly Bash and Linux guide with interactive, authentic terminal components. Built with Astro.

### Badges
[![Astro](https://img.shields.io/badge/Astro-5-FF5D01?logo=astro&logoColor=white)](https://astro.build) [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE) 

## Table of Contents
- Features
- Requirements
- Quick Start
- Scripts
- Project Structure
- Components (usage)
- Styling and Theming
- Mobile UX
- Deploy
- Troubleshooting
- Contributing
- License

## Features
- Realistic terminal card (`CodeCard`) with prompt and per‑command output
- Authentic GNU nano UI (`NanoCard`) with line numbers and cursor
- Responsive header with mobile dropdown (Sections) and slide‑in aside
- Global theme via CSS variables; accessible color contrasts

## Requirements
- Node.js 18.17+ (Node 20 LTS recommended)
- Bun 1.x, npm, or pnpm

## Quick Start
```bash
# with Bun
bun install
bun dev

# or with npm
npm i
npm run dev

# or with pnpm
pnpm i
pnpm dev
```

Build and preview:
```bash
bun build && bun preview
# npm run build && npm run preview
# pnpm build && pnpm preview
```

## Scripts
| Script     | Description                      |
|------------|----------------------------------|
| dev        | Start local dev server           |
| build      | Production build to `dist/`      |
| preview    | Preview the production build     |

## Project Structure
```
/
├─ public/
├─ src/
│  ├─ components/
│  │  ├─ header.astro      # Top nav + mobile dropdown
│  │  ├─ aside.astro       # Sidebar + mobile close button
│  │  ├─ footer.astro
│  │  ├─ codecard.astro    # Terminal UI
│  │  └─ nanocard.astro    # GNU nano UI
│  ├─ pages/
│  │  ├─ index.astro
│  │  ├─ commands.astro
│  │  ├─ fsScript.astro
│  │  └─ contact.astro
│  └─ styles/
│     └─ global.css        # Theme and layout
└─ package.json
```

## Components
### CodeCard
- Props: `command?: string | string[]`, `output?: string | string[]`
- Mobile: full‑width with compact padding
```astro
---
import CodeCard from "../components/codecard.astro";
---
<CodeCard command={["pwd", "echo 'hi'"]} output={["/home/user", "hi"]} />
```

### NanoCard
- Props: `filename?: string`, `content?: string | string[]`, `modified?: boolean`
- Mobile: full‑width; shortcuts bar scrolls horizontally so all options are visible
```astro
---
import NanoCard from "../components/nanocard.astro";
---
<NanoCard filename="script.sh" content={["#!/usr/bin/env bash", "echo Hello"]} />
```

## Styling and Theming
- Central theme variables in `src/styles/global.css`
- Inline terms: `.bash-term` (commands) and `.bash-dir` (paths)
- Social icons: white by default, turn black on hover

## Mobile UX
- Header/footer full‑width; `body` has bottom padding so content never sits under the fixed footer
- Sidebar slides in; Close button inside aside; overlay aligns with panel
- Dropdown (Sections) has a Close area and auto‑closes on link, outside click, or Escape
- Terminal/Nano cards expand to near full width for readability

## Deploy
- Vercel/Netlify: zero‑config for Astro
- Static output: `bun build` → deploy `dist/`

## Troubleshooting
- Sidebar not opening on mobile: ensure each page contains `<input type="checkbox" id="toggle-menu" hidden>` before `<Aside />`
- Dropdown not opening: header injects its own `#toggle-sections`; ensure header is present
- Styles not updating: hard refresh (Ctrl/Cmd+Shift+R)

## Contributing
PRs welcome. Please keep code clear and follow the existing naming and formatting patterns.

## License
MIT
