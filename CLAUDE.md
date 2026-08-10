# NEXUS DEFENSE — Tower Defense Game

## Overview

Browser-based tower defense game with a cyberpunk/sci-fi aesthetic. Single-file (`index.html`, ~3200 lines) with no external dependencies — open in browser to play.

**Objective:** Survive waves of enemies by placing defensive structures. Lose when 20 enemies reach the exit. 10 waves per tier; wave 10, 20, 30, etc. are boss fights.

## Architecture

Everything lives in `index.html`: embedded CSS, Canvas-based rendering, and all game logic in vanilla JavaScript (ES6+). No build step.

**Key global state:**
- `towers[]`, `enemies[]`, `projectiles[]`, `particles[]`, `spikes[]`, `muds[]`, `laserRods[]`, `armyTanks[]`
- `lives` (20 start), `credits` (150 start), `currentWave`, `waveActive`, `gameOver`
- `selectedTool`, `deleteMode`, `autoLaunch`

**Class hierarchy:**
```
Enemy → Boss
Tower → Flamethrower, Minigun, Crossbow, OmniCannon, Cannon
Standalone: Spike, Mud, LaserRod, Projectile, CannonBall, ArmyTank
```

**Main loop:** `loop()` → `requestAnimationFrame`. Wave spawning via `updateSpawning()`, completion via `checkWaveEnd()`.

## Grid

40 columns × 24 rows. Two branching enemy paths (upper + lower) that share entry/exit corridors. Enemies randomly pick a path each spawn. Cell size auto-scales to window.

## Towers & Structures

| Type | Cost | Notes |
|------|------|-------|
| Spike | 25cr | On-path only; passive tile damage |
| Mud | 25cr | On-path only; slows enemies 50–87.5% |
| Turret | 50cr | Basic, cyan, 3.5-cell range |
| Bomb | 50cr | Detonatable or loadable into Cannons |
| Tank | 40cr | Mobile AI unit that rams enemies |
| Laser Rod | 150cr | Beams between aligned rods on same row/col |
| Cannon | 150cr | Slow, explosive; requires bombs as ammo |
| Crossbow | 150cr | Extreme range (10.5 cells) |
| Flamethrower | 300cr | Close-range AOE (2 cells), rapid fire |
| Minigun | 300cr | Rapid fire, rotating barrels |
| Nuke | 500cr | One-time board clear |
| Super Cannon | 2000cr | Fires across entire board |

All towers upgradable to level 5 via click. Right-click or DELETE mode refunds 25cr (37cr for laser rods).

## Enemies

- Regular: HP = `(60 + wave×20) × 2^tier`, speed 1.2, reward 10–50cr by tier
- Boss (every 10th wave): 8× HP of prior wave's max, speed 0.6, reward 50–150cr
- Boss immunity: bomb/cannon splash deals only 1/8 damage

## Economy

- Wave clear: +25cr
- Kills: tier-scaled credit rewards
- Tight economy — plan tower placement before buying

## Controls

- Left-click: place selected tower
- Right-click: delete tower (refund)
- DELETE/Backspace: toggle delete mode
- Escape: cancel selection
- LAUNCH WAVE: start/resume wave
- AUTO: auto-launch waves

## Rendering

All graphics are procedurally drawn on Canvas — no image assets. Includes star field, glow effects, particle explosions, animated tower barrels, and a subtle CRT scanline overlay.

## Making Changes

- All code is in `index.html`. Search for class names or function names to navigate.
- Game balance (costs, HP scaling, wave counts) is in the class constructors and `startWave()`/`updateSpawning()`.
- Path coordinates are hardcoded arrays near the top of the script section.
- To add a new tower type: add a class, register it in the shop UI array, add placement/update/draw handling in the main loop.
