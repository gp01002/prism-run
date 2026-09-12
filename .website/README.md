---
directors_cut: https://prismrun.netlify.app/
video: https://youtu.be/_54od1dG_Gw
post: https://gp01002-code.github.io/miss01/
---

Your number is your colour.

You are a unicorn made of light, rolling across a slab in the dark. Take your number mod 7 — that remainder is the colour you glow. Reach the light column glowing its colour and the level opens.

To change your number you roll into prisms. A prism has two faces, and which operator you get depends on the side you hit it from: clip it from the left and it might add 5; come at the same prism from the right and it multiplies by 2.

The light each prism scatters is not decoration. Every beam is the colour you would become if you hit that face — so the arithmetic is still yours to plan, but you never have to do it blind. A beam outlined in white means that face wins the level. A grey beam means it would take you negative, and your light goes out.

So a level is a route, not a sum. Order matters (+3 then ×2 is not ×2 then +3), approach angle matters, and momentum makes both harder than they look. Prisms return a few seconds later, so a mistake costs time, not the run.

Controls

Desktop: drag anywhere to tilt the board, or use the arrow keys.
Mobile: tilt the phone itself. Whatever posture you are holding counts as level; ⌖ re-centres it.
VR: hold out a controller and tilt your hand — the board follows it. Trigger confirms.

The first five levels are hand-built and each introduces one idea. After that levels are generated, always with a guaranteed solution plus decoy prisms.

Technical notes

One canvas, drawn entirely in code — no images, no fonts, no external requests. The 3D is not WebGL: it is a hand-rolled perspective projection, so tilting the board is just a per-vertex height, and depth sorting, the light the unicorn casts on the floor and the seven-band rainbow trail all fall out of the same few hundred bytes. VR reuses that canvas as a texture on a floating panel.

Audio is synthesised at runtime. Each pickup is pitched by your new remainder against a major scale, so sound carries the colour too — as does text everywhere hue appears.