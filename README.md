# QR Code Alchemist

A sleek, fully client-side QR code generator and customizer built with React. Type any text or URL, style the code with your brand colors, embed a logo, add a caption, and download a crisp high-resolution PNG — no account, no server, everything happens in your browser.

## Features

- **Instant QR generation** — encode any URL or plain text as a QR code with one click (Enter key supported)
- **Brand customization** — set foreground/background colors, adjust quiet-zone margin, and pick error-correction level (L / M / Q / H)
- **Logo embedding** — overlay your own logo image at the center of the code (auto-sized with a safe margin so the code stays scannable)
- **Caption text** — add a text line rendered below the code on export
- **Resolution control** — export up to high-resolution PNG (e.g. 1000px+) for print-quality downloads
- **Copy + download** — copy the encoded value to the clipboard or download the rendered PNG
- **Modern UI** — polished shadcn/ui components, Tailwind CSS styling, toast notifications

## Tech Stack

- **Framework:** React 18 + Vite 5
- **UI:** shadcn/ui, Tailwind CSS, lucide-react icons
- **QR rendering:** `qrcode.react` (SVG) + canvas compositing for PNG export
- **Routing/State:** react-router-dom, @tanstack/react-query

## Quick Start

```bash
# install dependencies
npm install

# start the dev server (http://localhost:8080)
npm run dev

# build for production (outputs to dist/)
npm run build

# preview the production build locally
npm run preview
```

Node.js 18+ recommended.

## Project Structure

```
QR-Code-Alchemist/
├── index.html                  # entry HTML
├── src/
│   ├── main.jsx                # React entry point
│   ├── App.jsx                 # providers + router setup
│   ├── pages/Index.jsx         # main page
│   ├── components/
│   │   ├── QRCodeGenerator.jsx # core generator UI + PNG export logic
│   │   ├── AdvancedOptions.jsx # colors, margin, error correction, logo
│   │   └── ui/                 # shadcn/ui components
│   └── lib/utils.js            # helpers
├── public/                     # static assets (favicon, og image)
├── tailwind.config.js
└── vite.config.js
```

## How it works

The QR code is rendered as an SVG via `qrcode.react`. On download, the SVG is serialized and drawn onto a `<canvas>` at the selected resolution, the logo and caption are composited, and the canvas is exported as a PNG file. No data ever leaves the browser.

## Deploy

The app is a static SPA. After `npm run build`, serve the `dist/` directory from any static host:

- **GitHub Pages:** build output is committed to the repo root; Pages is enabled on the `main` branch
- Any static host (Cloudflare Pages, Vercel, Netlify) works — just point it at `dist/`

Because this is deployed as a project page under a sub-path, the Vite `base` is set to `"./"` so asset URLs resolve relatively.

---

Built by Girish Lade — https://ladestack.in
