# Prism Run

A tilt-and-roll puzzle game made for **js13kGames 2026** (theme: Unicorns and
Rainbows). Code, graphics and sound fit in a **10,360-byte zip** — no images,
no fonts, no libraries, no external requests.

▶ **[Play](https://gp01002-code.github.io/prism-run/)** ·
🏆 **[js13k entry](https://js13kgames.com/2026/games/prism-run)** ·
✨ **[Director's Cut](https://prismrun.netlify.app/)** ·
📝 **[Post-mortem](POSTMORTEM.md)**

## How it plays

You are a unicorn made of light on a slab in the dark. Your number mod 7 is the
colour you glow. Reach the light column glowing its colour and the level opens.

You never have to do the arithmetic. Prisms scatter light, and **every beam is
the colour you would become if you hit that face** — a beam outlined in white
wins the level, a grey one would take you negative. So you read colours and
pick a route.

Each prism has two faces and the operator depends on which side you hit it
from. Order doesn't commute (`+3` then `×2` is not `×2` then `+3`), so a level
is a route rather than a sum, and momentum makes both harder than they look.
Prisms come back a few seconds after you take one, so a mistake costs time,
not the run.

## Controls

| | |
|---|---|
| Desktop | Drag anywhere to tilt the board, or use the arrow keys |
| Mobile | Tilt the phone. Your posture at start counts as level; ⌖ re-centres |
| VR | Push the thumbstick, or tilt a controller. Trigger confirms, grip re-centres |

## Build

```bash
npm install terser roadroller
pip install zopflipy
./build.sh
```

`dist/packed.html` is the playable single file, `dist/packed.zip` is the
submission. The pipeline is: concat → terser → Roadroller self-extraction →
inline into the HTML shell → zopfli zip.

## Files

| File | |
|---|---|
| `game.js` | Game logic, 2D canvas renderer, audio, levels |
| `xr3d.js` | WebGL scene used in VR — real geometry, per-eye matrices |
| `index.html` | Shell; `/*GAME*/` is the injection point |
| `build.sh` | Minify, pack, zip |
| `POSTMORTEM.md` | What worked, what broke, and the numbers |

## Notes

The non-VR 3D is a hand-rolled perspective projection on a 2D canvas rather
than WebGL — tilting the board is a per-vertex height, and depth sorting, the
light the unicorn casts on the floor and the rainbow trail all fall out of the
same few hundred bytes. VR is a separate raw-WebGL scene.

Audio is synthesised at runtime; each pickup is pitched by your new remainder
against a major scale, so sound carries the colour too. Every colour is
mirrored in text for colourblind players.

## Authors

[gp01002-code](https://github.com/gp01002-code) ·
[Teddy2010119](https://github.com/Teddy2010119)
