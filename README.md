# Spider Walk Atlas

A standalone preview tool for **8-leg spider walk cycle animation**, built with Vite + TypeScript + Phaser 3.

Adapted from the humanoid walk system in [nexus_phaser](https://github.com/dymek84/nexus_phaser) — same architecture, extended to support 8-legged creatures with a tripod-style gait.

## Features

- 🕷️ **8-frame walk cycle** — procedurally drawn from body part images
- 🦵 **8 legs** — 4 left (behind body) + 4 right (in front), tripod-gait phasing
- 🎛️ **Live controls panel** — adjust everything in real-time:
  - Animation speed, body sway, leg swing amplitude
  - Per-leg attachment points (X/Y), base angles, segment sizes
  - Body/head scale and offsets
  - Debug bounds & skeleton visualisation
- **⬇ Export JSON** — copy the full pose definition ready to paste into `nexus_phaser`

## Atlas Image Layout

The spider atlas (single PNG, 300×400px) uses this layout:

| Part       | x | y   | w   | h   |
|------------|---|-----|-----|-----|
| body       | 0 | 0   | 188 | 200 |
| head       | 0 | 200 | 160 | 100 |
| upper_leg  | 0 | 300 | 140 | 42  |
| lower_leg  | 0 | 342 | 160 | 32  |

Drop your atlas PNG into `public/assets/spider_atlas.png` and update `spiderAtlasParts.ts` to load it.

## Getting Started

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

## Build

```bash
npm run build
```

## Tests

```bash
npx vitest run
```

## Exporting to nexus_phaser

1. Tune everything to your liking using the controls
2. Click **⬇ Export JSON**
3. The JSON is copied to clipboard automatically
4. Paste it into `nexus_phaser` as the spider character config

## Project Structure

```
src/
  walkcycle/
    spiderAtlasParts.ts        — frame definitions for body/head/upper_leg/lower_leg
    generateSpiderSheet.ts     — 8-leg animation renderer (adapted from generateWalkerSheet.ts)
    spiderPlaceholderAtlas.ts  — procedural placeholder atlas (no image needed)
    spiderPreviewScene.ts      — Phaser scene + UI wiring
  main.ts                      — Phaser game bootstrap
  __tests__/                   — vitest unit tests
```
