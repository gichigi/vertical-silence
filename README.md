# Unblocked

Generative art series using the blockquote vertical bar `|` as the sole visual motif.

**[Live →](https://unblockedbymooch.vercel.app)**

## What it is

I needed a system for generating article banners — something high quality, quick to produce, visually consistent, and distinctly ours. Not stock photos. Not Canva templates.

The result: a text-seeded generative art tool. Type anything in, get a unique composition of vertical bars. Same input always produces the same output. One motif, monochrome, 16:9.

Built across nine iterations in one late-night session with Claude.

## How it works

1. **Seed** — Enter any text string or use a numeric seed. Same input always produces the same output.
2. **Clusters** — The algorithm places 1-6 groups of uniform-height vertical bars across a 16:9 canvas.
3. **Scale** — Clusters range from small accent marks to full-bleed bars taller than the canvas.
4. **Separation** — Overlap prevention keeps clean negative space between groups.
5. **Shade** — Most clusters are near-black; occasional grey whispers provide contrast.
6. **Export** — Download as 3840x2160 PNG.

### Sweet spot

2 clusters, scale 2-4, high darkness. One large group bleeding off an edge, one smaller accent cluster. Generous white space between them.

## Technical details

- **p5.js** (v1.7.0) — canvas rendering
- **SFC32 PRNG** — deterministic pseudorandom number generation from dual-hash string seeds
- **No dependencies** — single self-contained HTML file
- **16:9 output** — 1920x1080 canvas, exported at 3840x2160

### String-to-seed pipeline

```
Input string → dual hash (MurmurHash-style) → SFC32 PRNG → macro parameters → composition
```

## Parameters

| Parameter | Range | Default | Effect |
|-----------|-------|---------|--------|
| Clusters | 1-6 | 2 | Number of bar groups |
| Scale | 0.6-4.0 | 2.0 | Overall size multiplier |
| Darkness | 0.5-1.0 | 0.9 | How dark the bars are |

## Project structure

```
unblocked/
├── index.html    # Complete self-contained app
└── README.md     # This file
```

## Development

No build step. Open `index.html` in a browser or deploy to any static host.

```bash
open index.html
```

## Algorithm history

Nine versions to get here:

- v1-v3: Flow field experiments — bars following noise-driven paths. Looked like static or tree branches, not composition.
- v4-v5: Switched from thinking "generative art" to "design tool". Structured clusters. Closer, but ascending bar heights looked like a finance chart.
- v6-v7: Scaled up. Edge bleed. Black-dominant palette. Fewer clusters, more conviction.
- v8: Added overlap prevention and enforced scale tiers. Compositions started feeling designed.
- v9: Uniform bar height within clusters (blockquote, not bar chart). Generous spacing. This is the one.

## License

MIT
