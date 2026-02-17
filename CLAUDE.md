# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Pixel-art browser games for a kindergarten presentation teaching children about different professions in a playful way. Two games available from a main menu.

## Architecture

**Multi-file, zero-dependency**: each game is a self-contained HTML file with inline CSS and JavaScript.

```
index.html      — main menu (choose a profession)
cashier.html    — "Король POSAPI" cashier game
backend.html    — "Бэкенд-инженер" server fixing game
```

Key technologies used inline:
- **Canvas API** for pixel-art rendering
- **Web Audio API** for sound effects (oscillator-based beeps)
- **CSS** with `Press Start 2P` Google Font for pixel aesthetic

## Games

### Cashier (cashier.html)
Player is a cashier. Customers approach with items, player must calculate the total and enter it on a terminal numpad. Game states: `start | playing | animating | processing | win`.

### Backend Engineer (backend.html)
Player is a backend engineer. Problems appear in 4 zones (top/left/right/bottom), player clicks/taps to fix them before they expire. 3 lives, game ends when all lives are lost. Game states: `start | playing | gameover`.

## Code Structure (per game file)

Each game file's JavaScript is organized into labeled sections:
- **GAME CONFIG** — constants, problem/product definitions
- **AUDIO** — Web Audio beep/success/error sounds
- **GAME STATE** — global state variables
- **PIXEL ART DRAWING** — Canvas drawing functions
- **SCENE RENDERING** — main `drawScene()` compositing all elements
- **ANIMATION LOOP** — `requestAnimationFrame` game loop
- **GAME LOGIC** — start, checking, win/lose conditions
- **EVENT LISTENERS** — clicks, keyboard input
- **RESPONSIVE SCALING** — viewport-based scaling of the 960x640 game wrapper

## Running Locally

Open `index.html` directly in a browser. No build step, no server required.

## Deployment

Hosted on GitHub Pages at `https://lllypuk.github.io/the-king-of-posapi/`.

## Design Docs

- `docs/CASHIER_GAME_PLAN.md` — cashier game concept, mechanics, product/pricing table
- `docs/BACKEND_GAME_PLAN.md` — backend engineer game concept, zones, mechanics
- `docs/TASKS.md` — development task breakdown by phase

## Key Conventions

- All UI text is in Russian
- Prices are intentionally small (1-5₽) so children aged 5-6 can do the mental arithmetic
- Games use a fixed 960x640 canvas that scales to fit the viewport
- Portrait mobile shows a "rotate phone" hint; landscape is required
- Each game has a "← МЕНЮ" button to return to the main menu
