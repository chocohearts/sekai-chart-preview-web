# sekai-mmw-preview-web

Project SEKAI-style SUS chart previewer (Web version).

![Preview](docs/preview.jpg)

Supports pure WASM rendering for song charts and Overlay HUD (score/health/combo/PERFECT/intro info card), Unity-style native AP ending animations, local file uploads, and PWA caching.

## Page Routing

- `/`: Home page
- `/upload`: Upload custom chart page
- `/preview`: Preview page
- `/about`: About page

Notes:

- If the URL contains preview parameters such as `sus`, `cfg`, or `config`, it will automatically redirect to `/preview` even if the URL is not `/preview`.

## Feature Overview

- SUS parsing and native WebAssembly rendering
- Synchronization of audio tracks and chart layout (supports `offset`)
- Pure WebAssembly overlay HUD, background generation, and opening information layer
- AP-style ending performance (rendered natively frame-by-frame using Unity animations and particle effects; does not rely on video)
- Optional custom chart info (displays the chart icon, chart title, and chart author below the original song information)
- Local upload of SUS/BGM/song art
- Background brightness adjustment (60%–100%)
- Optional lock screen component display for easy screen recording
- PWA + Service Worker on-demand caching
- High-DPR preview support for mobile devices

## Getting Started

Environment Requirements:

- Node.js 20+
- npm 10+
- Emscripten (`emcc` executable)
- sus2json source code: [watagashi-uni/Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)

Installation and Development:

```bash
npm install
npm run dev
```

Notes:

- For daily integration testing, we recommend using `npm run dev`.
- If you need to verify the WASM output, PWA, Service Worker, or deployment results, first run `npm run build`, then run `npm run preview`.

Production Build and Preview:

```bash
npm run build
npm run preview
```

### sus2json Build Dependencies

`npm run build` compiles `SusToJsonCpp` from [Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)
into WebAssembly for use in browsers. The default directory structure is:

```text
workspace/
├── sekai-mmw-preview-web/
└── Sekai-SUS-Parser/
    └── SusToJsonCpp/
```

You can run the following command in this project directory to set up the source code:

```bash
git clone https://github.com/watagashi-uni/Sekai-SUS-Parser ../Sekai-SUS-Parser
```

If the source code is not in the default location, you can set the `SEKAI_SUS_TO_JSON_ROOT` environment variable to point to the `SusToJsonCpp` directory:

```bash
SEKAI_SUS_TO_JSON_ROOT=/path/to/Sekai-SUS-Parser/SusToJsonCpp npm run build
