# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

"Король POSAPI" (The King of POSAPI) — a pixel-art browser game about accepting payments at a cash register. Built for a kindergarten presentation to teach children how payment terminals work in a playful way.

## Architecture

**Single-file application**: everything lives in `index.html` — HTML, CSS, and JavaScript with zero dependencies.

Key technologies used inline:
- **Canvas API** for pixel-art rendering (store scene, customers, items)
- **Web Audio API** for sound effects (oscillator-based beeps)
- **CSS** with `Press Start 2P` Google Font for pixel aesthetic

## Code Structure (all in index.html)

The JavaScript is organized into labeled sections:
- **GAME CONFIG** — product list (emoji + price), customer color palettes, constants (`TOTAL_CUSTOMERS`, `ITEMS_MIN/MAX`)
- **AUDIO** — Web Audio beep/success/error/keypress sounds
- **GAME STATE** — global state variables; game states: `start | playing | animating | processing | win`
- **TERMINAL DISPLAY** — numpad input handling and display updates
- **CUSTOMER GENERATION** — random customer/item generation
- **PIXEL ART DRAWING** — Canvas drawing functions (person, counter, items, floor, queue)
- **SCENE RENDERING** — main `drawScene()` compositing all elements
- **ANIMATION LOOP** — `requestAnimationFrame` game loop
- **GAME LOGIC** — start, payment checking, processing animation with progress bar, win condition
- **EVENT LISTENERS** — numpad clicks, keyboard input (digits, Enter, Backspace, Escape)
- **RESPONSIVE SCALING** — viewport-based scaling of the 960x640 game wrapper

## Running Locally

Open `index.html` directly in a browser. No build step, no server required.

## Deployment

Hosted on GitHub Pages at `https://lllypuk.github.io/the-king-of-posapi/`.

## Design Docs

- `docs/GAME_PLAN.md` — game concept, screen layouts, mechanics, product/pricing table
- `docs/TASKS.md` — development task breakdown by phase

## Key Conventions

- All UI text is in Russian
- Prices are intentionally small (1-5₽) so children aged 5-6 can do the mental arithmetic
- Game uses a fixed 960x640 canvas that scales to fit the viewport
- Portrait mobile shows a "rotate phone" hint; landscape is required
