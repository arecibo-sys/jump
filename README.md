# 🎮 JUMP — Vertical Arcade Platformer

Climb. Steer. Collect. Rise again.

A Doodle-Jump-style vertical arcade platformer. Control a cartoon creature that climbs continuously upward — steer it onto platforms, chain coins, grab power-ups, and dodge enemies. Don't fall off the bottom!

## ▶ Play it live

**https://arecibo-sys.github.io/jump/**

## ✨ Features

- **8 interchangeable retro heroes** — Blip, Pixel, Mario, Ghost, Serpent, Knight, Nova, Frog — each with distinct stats (jump/steer/size), selectable in the menu
- **4 themed worlds** — Fantasy, Forest, Mines, Clouds — with parallax backgrounds, reached by altitude
- **10 power-ups** — magnet, balloon, jump boots, shield, anti-gravity, fireball, supernova, jetpack, 2x score
- **Enemies & hazards** — monsters, anvils, ball-chains, lightning, potions, spikes
- **Coin trails, stars & combos** — coins guide your route and boost the climb
- **Falling-window rescue** — the defining mechanic: miss a platform and you get a brief chance to catch one below before the run ends
- **Procedural electronic soundtrack** — modern, non-intrusive, layered (constant 112 BPM)
- **Cross-platform** — keyboard (desktop), touch-drag (smartphone/iPad), optional accelerometer

## 🛠 Tech

- Single-file HTML (self-contained, no external assets, no network calls)
- Canvas 2D rendering
- Procedural WebAudio (no audio files)
- Fixed 60fps timestep with swept collision (no tunneling)
- Responsive canvas scaling for desktop + mobile

## 🎨 Design

Bright, exaggerated, playful. Characters have large facial features and highly readable silhouettes. Backgrounds are colorful, multilayered parallax scenery that makes the creature feel like it's traveling through increasingly fantastical environments.

## 🎯 How to play

- **Desktop:** ← → / A D keys to steer
- **Mobile/iPad:** drag left/right to steer
- Land on platforms, chain coins, grab power-ups, dodge enemies. Don't fall off the bottom!

## 🤖 Built by the Nexus engineering team

Coordinated by Hermes (orchestrator) with the rapid systems engineer, reasoning engineer, and long-horizon systems engineer. See `report.md` for the full team report.
