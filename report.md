# JUMP — Team Build Report

**Team:** Nexus engineering
**Date:** 2026-08-19
**Location:** `/Volumes/Satechi 1TB/nexus-engineer/`
**Artifacts:** `jump.md` (spec), `jump.html` (game, ~47KB single-file)

---

## What was built

A Doodle-Jump-style vertical arcade platformer as a single-file HTML game. The player controls a cartoon creature that climbs continuously upward, steering it onto platforms, chaining coins, grabbing power-ups, and avoiding enemies — with the defining **falling-window rescue mechanic** (a brief chance to catch a platform below before the run ends).

**Features:**
- **8 interchangeable retro heroes** (Blip, Pixel, Mario, Ghost, Serpent, Knight, Nova, Frog) — selectable in the menu, each with distinct stats (jump/steer/size)
- **4 themed worlds** (Fantasy, Forest, Mines, Clouds) with parallax backgrounds, reached by altitude
- **10 power-ups** with a one-override-at-a-time economy (magnet, balloon, boots, shield, anti-grav, fireball, supernova, jetpack, 2x score)
- **Enemies + hazards** (monsters, anvils, ball-chains, lightning, potions, spikes)
- **Coin trails, stars, combos** — coins guide the route and boost the climb
- **Falling-window rescue** — the defining mechanic
- **Procedural non-intrusive electronic soundtrack** (constant 112 BPM, conservative gains, layered)
- **Cross-platform:** keyboard (desktop), touch-drag (mobile/iPad), optional accelerometer
- **Fixed 60fps timestep** with 3-step clamp, swept CCD collision (no tunneling), responsive canvas scaling

---

## Per-agent contributions

### Hermes (leader/orchestrator)
- Set up the project directory, wrote `jump.md` spec
- Wrote the full game (`jump.html`) incorporating all team feedback
- Applied the physics tuning fixes
- Independently verified the game headlessly (syntax + 20k-step gameplay simulation)
- **Strong:** orchestration, integration of team feedback, verification discipline
- **Weak:** initially wrote the platform generator in the wrong direction (downward instead of upward), which caused the climb-stall bug

### Rapid systems engineer (deepseek-v4-flash-731-rapid)
- Produced the technical architecture brief (fixed timestep, physics, entity system, worlds, input, audio)
- Diagnosed the first climb-stall bug: the auto-assist only targeted platforms above, steering away from the landing platform during descent
- Applied the phase-aware assist fix
- **Strong:** fast, precise root-cause diagnosis with exact line references and math
- **Weak:** hit a tool-call guardrail on a later iteration (repeated non-progressing attempts)

### Reasoning engineer (deepseek-v4-pro---up)
- Independently reviewed the architecture and caught that the **falling-window rescue mechanic** (the defining feature) was missing — blocked the build until it was added
- Flagged power-up economy (redundant upward-movement power-ups) and visual size budget
- Diagnosed the manual-vs-assist steering conflict with 5 concrete tuning values
- **Strong:** independent verification (didn't trust rapid's report), caught the core design gap, precise tuning math
- **Weak:** none significant

### Long-horizon systems engineer (glm-5-2-long-horizon-systems-engineer)
- Validated the overall architecture and build sequence
- Flagged **collision tunneling at high-velocity power-up states** as the top integration risk, and re-sequenced the build to front-load it (CCD collision first)
- **Strong:** systems-level thinking, identified the cross-cutting risk
- **Weak:** none significant

### Creative product engineer (fable-5-creative-product-engineer)
- **Unavailable** — HTTP 429 (no usage credits for the model). The hero roster and visual direction were designed by the orchestrator instead.

---

## Key lessons

1. **The platform generator direction bug** was the hardest to find — the game "worked" (no crash) but the player couldn't climb because platforms were generated downward instead of upward. This is a classic "runs but doesn't play" bug that only shows up in gameplay simulation, not syntax checks.
2. **The team's independent review caught the missing core mechanic** (falling-window rescue) before any code was written — the value of not trusting a single agent's report.
3. **Physics tuning is iterative** — jump height vs platform gap vs assist strength must be tuned together, not in isolation. The reasoning engineer's "tune together, not in isolation" advice was correct.

---

## Verification

- `node --check` passes (syntax clean)
- Headless gameplay simulation: 20,000 steps, no crash
- Player climbs to world 3 (Clouds) at 61,451 altitude in one run
- Hero switching, falling-window, enemies, power-ups all verified
- **Not yet browser-tested** (needs one-time Chrome remote-debugging approval) and **not yet pushed to GitHub** (awaiting user presentation/approval)
