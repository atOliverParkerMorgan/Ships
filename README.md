# Ships

A browser-based 2D naval combat game built with JavaScript and p5.js. You command a pirate ship, manage wind-based movement, capture islands, fight enemy ships, and spend coins on upgrades to survive and progress.

## Project Overview

**Ships** is an arcade-style single-player game running on an HTML canvas via p5.js. The game loop centers on navigating a large generated world, balancing movement and combat, and capturing islands while managing core resources (crew, ship health, coins, and score).

The objective is to reach a target score by conquering islands and surviving enemy pressure.

## Features

- Wind-influenced ship movement and rotation
- Broadside-style cannon firing on both sides of the ship
- Procedural island placement with multiple island shapes
- Island capture system with score and coin rewards
- Enemy ship spawning, pursuit, and ranged attacks
- Upgrade/trading screen at captured islands
- Soundtrack playback and themed game screens (loading/tutorial/game over/win)

## Architecture / Structure

### Tech Stack

- JavaScript (plain ES5-style scripts)
- p5.js for rendering, game loop, input, and audio loading
- Static assets (images, fonts, sounds)

### Directory Layout

- `SHIP.html` — application entry point (loads scripts and p5 libraries)
- `jsfiles/MAIN.js` — global state, setup/draw loop, input handling, world updates
- `jsfiles/Ship.js` — player ship behavior and movement model
- `jsfiles/enemy.js` — enemy ship AI movement and combat behavior
- `jsfiles/island.js` — island rendering and hit/collision points
- `jsfiles/shot.js` — projectile movement and lifetime
- `jsfiles/wind.js` — wind direction simulation and compass rendering
- `jsfiles/mission_map.js` — trading/mission map screen
- `jsfiles/collision.js` — lightweight collision helper
- `images/`, `sounds/`, `Fonts/` — game assets
- `libraries/` — bundled p5.js and addons

### Runtime Flow

1. `SHIP.html` loads game scripts and p5.js.
2. `preload()` loads images/fonts, then `setup()` initializes world objects.
3. `draw()` runs every frame and switches between loading, intro, gameplay, and trading/map views.
4. `update()` handles spawning, movement, collisions, scoring, upgrades, and win/lose logic.

## Build & Run Instructions

This project is static and does not require a build step.

### Requirements

- A modern desktop browser (Chrome, Firefox, Edge)
- Local HTTP server (recommended for reliable asset/audio loading)

### Run Locally

1. From the project root, start a local server:
   - Python 3: `python3 -m http.server 8000`
2. Open:
   - `http://localhost:8000/SHIP.html`

### Controls

- `Space` — start from intro/tutorial screen
- `A` / `D` — rotate ship
- `W` — paddle (forward thrust)
- `S` — anchor (slow down)
- `R` — toggle cannon-ready mode
- `Q` / `E` — fire broadsides
- At trading screen:
  - `Z` buy crew
  - `X` repair health
  - `C` increase shot range
  - `V` increase max speed
  - `N` exit trading screen

## Testing

There is currently no automated test suite.

### Manual Smoke Test

1. Launch the game and confirm loading/intro screens display.
2. Start gameplay and verify movement (`A/D/W/S`) responds correctly.
3. Toggle firing mode (`R`) and fire (`Q/E`) to confirm projectiles spawn and expire.
4. Approach islands and verify damage/capture progression updates score and coins.
5. Enter trading screen near a captured island and confirm upgrade keys (`Z/X/C/V/N`) work.
6. Confirm enemy ships can spawn, move, and fire.
7. Verify win/lose states render and stop gameplay flow.

## Project Context

This repository appears to be a standalone game prototype/portfolio-style project focused on gameplay programming fundamentals: real-time loop management, entity behavior, collision handling, and input-driven mechanics using p5.js.

It is intentionally lightweight (no framework or bundler), making it easy to run, inspect, and iterate on directly in the browser.