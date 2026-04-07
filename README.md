# Unblocked

Generative art series using the blockquote vertical bar `|` as the sole visual motif.

**[Live →](https://unblocked.vercel.app)**

## About

Unblocked is a string-seeded generative design system. Each unique text input produces a unique, deterministic composition of vertical bars — monochrome, structured, minimal.

The aesthetic draws from Tyler Hobbs' line-based compositional sensibility and Jack Butcher's monochrome discipline. Every output is white background, black/grey bars, nothing else.

## How it works

1. **Seed** — Enter any text string or use a numeric seed. The same input always produces the same output.
2. **Clusters** — The algorithm places 1–6 groups of uniform-height vertical bars across a 16:9 canvas.
3. **Scale variation** — Clusters range from tiny accent marks to full-bleed bars taller than the canvas.
4. **Separation** — Overlap prevention ensures clean negative space between groups.
5. **Shade** — Most clusters are near-black; occasional grey "whisper" clusters provide contrast.
6. **Export** — Download as 3840×2160 PNG (2x resolution for crisp web display).

### Sweet spot

The best outputs tend to come from **2 clusters, scale 2–4, high darkness** — producing compositions with one large edge-bleeding group and one smaller accent cluster with generous white space between them.

## Technical details

- **p5.js** (v1.7.0) — canvas rendering
- **SFC32 PRNG** — deterministic pseudorandom number generation from dual-hash string seeds
- **No dependencies** — single self-contained HTML file
- **16:9 output** — 1920×1080 canvas, exported at 3840×2160 (pixelDensity 2)

### String-to-seed pipeline

```
Input string → dual hash (MurmurHash-style) → SFC32 PRNG → macro parameters → composition
```

The first PRNG calls determine cluster scale tiers, positions, shades, and alignment. All subsequent bar placement is derived from these — same string, same piece, every run.

## Parameters

| Parameter | Range | Default | Effect |
|-----------|-------|---------|--------|
| Clusters | 1–6 | 2 | Number of bar groups |
| Scale | 0.6–4.0 | 2.0 | Overall size multiplier |
| Darkness | 0.5–1.0 | 0.9 | How dark the bars are |

## Project structure

```
unblocked/
├── index.html    # Complete self-contained app
└── README.md     # This file
```

## Development

No build step. Open `index.html` in a browser or deploy to any static host.

```bash
# Local development
open index.html

# Or serve with any static server
npx serve .
```

## Deployment

Deployed on Vercel as a static site. Any push to `main` auto-deploys.

## Algorithm lineage

This is **Algorithm 1** of the Unblocked series. The creative journey:

- v1–v3: Flow field experiments (bars following noise-driven paths)
- v4–v5: Shift to design-driven approach (structured clusters, not particle systems)
- v6–v7: Scale increase, edge bleed, black-dominant palette
- v8: Overlap prevention, enforced scale tiers
- v9: Uniform bar height within clusters, generous spacing for blockquote readability

## License

MIT

