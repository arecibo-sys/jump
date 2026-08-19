# Jump

Jump is a single-file, Doodle Jump-inspired arcade game for iPhone, iPad, and desktop browsers. Guide a hero upward across platforms, collect power-ups, avoid hazards, and build a high score.

▶ **[Play the live game](https://arecibo-sys.github.io/jump/)** — steer with touch, keyboard, mouse, or optional device tilt.

## Play

Open `index.html` in a modern browser. No build step, server, account, or external dependency is required.

### Controls

On touch devices, drag left or right on the game screen to steer. On desktop, use the arrow keys or A and D. Optional device tilt steering is available after the browser grants motion access.

## Mobile rendering fix

This version keeps gameplay in a fixed logical canvas while scaling only the displayed canvas. The prior renderer combined backing-store scaling with a second context scale. On smaller high-density screens, that caused frame clearing to miss part of the canvas, leaving stale pixels visible during jumps.

The renderer now resets the device-pixel transform after every resize and clears the complete logical frame on every animation frame. This keeps the game sharp and prevents visual trails or pixel buildup on iPhone and iPad.

## Features

- Eight playable retro heroes
- Procedural platforms, collectibles, hazards, and power-ups
- Four visual worlds
- Touch, keyboard, mouse, and optional motion controls
- Local high-score storage
- No analytics, network requests, credentials, or server-side components

## Privacy

The game runs entirely in the browser. It stores only the selected hero and high score in the browser's local storage. It does not send gameplay or personal data anywhere.

## License

No license has been specified for this project yet.
