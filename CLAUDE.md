# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Retro top-down 2D shooter game and other HTML5 browser games built with vanilla JavaScript and Canvas API. No build tools, frameworks, or package manager — files run directly in the browser.

## Running

```bash
open shooter-game.html    # Main game
open tic-tac-toe.html     # Tic Tac Toe
```

No build step, no dependencies to install, no dev server required.

## Architecture

Each game is a self-contained single HTML file with embedded CSS and JavaScript.

### Shooter Game (`shooter-game.html`)

- **Single `Game` class** encapsulates all logic: state management, input, physics, rendering
- **Game state machine**: `MENU → PLAYING ↔ PAUSED → GAME_OVER`
- **Game loop**: `requestAnimationFrame` with delta-time for frame-rate-independent physics
- **Entity model**: player, bullets, enemies, and particles are plain objects stored in arrays
- **Collision detection**: AABB (axis-aligned bounding box)
- **Rendering order**: particles → player → bullets → enemies (z-order)
- **Progression**: level-ups every `100 * level` points; spawn rate and enemy stats scale with level
- **Input**: arrow keys for movement, mouse aim + click to shoot, spacebar to pause

### Tic Tac Toe (`tic-tac-toe.html`)

- Single `TicTacToe` class with 9-element array board, DOM event handling, 8 win-pattern checks

## Conventions

- **Naming**: camelCase for variables/functions, PascalCase for classes, SCREAMING_SNAKE for state constants
- **Retro aesthetic**: neon green (#00ff00) on dark background, "Press Start 2P" Google Font
- **Game config values** (spawn rates, speeds, health) are inline constants — no config file

## Git Workflow

- **Remote**: `origin` → `https://github.com/aparnabivera/retro-shooter-game.git`
- **Branch**: `main`
- **Commit early and often**: As you work, commit changes regularly — not just at the end of a task. Every meaningful step (new feature, bug fix, refactor, config change) should get its own commit with a clean, descriptive message.
- **Always push to GitHub**: After each commit, run `git push origin main` so the work is saved remotely. We should never lose progress — if something breaks, we can always revert to a previous commit.
- **Clean commit messages**: Each commit message should clearly describe what was changed and why. Keep them concise but informative.
