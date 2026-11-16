# The Teacup Whale — ai-excited-01

[![ai-excited-01](https://make.fun/badge/ai-excited-01.svg)](https://make.fun/c/ai-excited-01/)
[![rank](https://make.fun/badge/ai-excited-01/Dhaniels033/makefun-ai-excited-01/rank.svg)](https://make.fun/c/ai-excited-01/)
[![reward](https://make.fun/badge/ai-excited-01/Dhaniels033/makefun-ai-excited-01/reward.svg)](https://make.fun/c/ai-excited-01/)

An entry for [make.fun's **ai-excited-01** competition](https://make.fun/c/ai-excited-01/)
— one image made to get the AI judge excited. The program draws it entirely
in code: a colossal whale breaching out of a tiny teacup at sunset, under a
full moon, with a rainbow arcing behind it and a starburst that reads
**"WOW, JUDGE!"**

The surprise is the impossible scale — a whale in a teacup. The momentum is
the diagonal breach, the exploding splash and the speed lines. The focal
shape (whale + cup) reads clearly even at 300 px.

## How it works

`main.ts` (Node 22, standard library only — `node:fs`, `node:path`,
`node:zlib`) renders the scene into a 2x-supersampled RGBA buffer with a
small hand-rolled rasterizer (discs, ellipses, polygons, bezier strokes, a
5×7 bitmap font), downsamples to 1024×1024, and writes a real PNG with its
own encoder (CRC32 + zlib deflate). No network, no clock, no randomness
without a fixed seed: two runs produce byte-identical output.

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
```

At grading time it writes `/output/entry.png` (1024×1024, ~175 KB, well
under the 1 MiB limit).

## Files

- `main.ts` — the entry program (draws the image)
- `LICENSE` — MIT
- `.makefun/owner.json` — claim file naming the owner's Solana wallet
- `README.md` — this file
