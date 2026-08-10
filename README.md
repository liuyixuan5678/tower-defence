# NEXUS DEFENSE

A browser-based tower defense game with a cyberpunk/sci-fi aesthetic. No installation required — just open `index.html` in your browser and play.

## How to Play

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. Select a tower from the shop panel on the right.
3. Place towers on the grid (not on the enemy path).
4. Click **LAUNCH WAVE** to send enemies — survive all waves to win.
5. Earn credits from kills and wave clears to buy and upgrade towers.

**You lose if 20 enemies reach the exit.**

## Controls

| Action | Control |
|--------|---------|
| Place tower | Left-click on grid |
| Delete tower (refund) | Right-click on tower |
| Toggle delete mode | DELETE or Backspace |
| Cancel selection | Escape |
| Launch wave | LAUNCH WAVE button |
| Auto-launch waves | AUTO toggle |

## Towers & Structures

| Name | Cost | Description |
|------|------|-------------|
| Spike | 25cr | Placed on-path; deals passive tile damage |
| Mud | 25cr | Placed on-path; slows enemies up to 87.5% |
| Turret | 50cr | Basic tower, cyan, 3.5-cell range |
| Bomb | 50cr | Deals 1000 damage in area; load into Cannons |
| Tank | 40cr | Mobile AI unit that rams and damages enemies |
| Laser Rod | 150cr | Pairs with aligned rods to beam enemies on same row/col |
| Cannon | 150cr | Slow, explosive; requires bombs as ammo |
| Crossbow | 150cr | Extreme-range sniper (10.5 cells) |
| Flamethrower | 300cr | Close-range AOE cone (2 cells), rapid fire |
| Minigun | 300cr | High fire rate with rotating barrel animation |
| Laser Turret | 300cr | Instant hitscan beam with visual retract effect |
| Boomerang | 100cr | Projectile flies out and returns, piercing all enemies twice |
| Nuke | 500cr | One-time board-wide clear (5000 damage) |
| Missile Launcher | 1000cr | Homing missiles with massive AOE (10000 damage, 20-cell range) |
| Super Cannon | 2000cr | Fires explosive shells across the entire board |

All towers can be upgraded up to **level 5** by clicking on a placed tower. Right-click to delete and receive a partial refund.

## Enemies

- **Regular enemies**: HP scales with wave number and tier. Speed 1.2. Reward 10–50cr.
- **Boss enemies** (every 10th wave): 8× HP of the prior wave's max, speed 0.6. Reward 50–150cr.
- Boss enemies have splash damage resistance (bomb/cannon AOE deals 1/8 damage).

Enemies follow two branching paths (upper and lower) that share entry and exit corridors, and randomly pick a path each spawn.

## Economy

- Start with **150 credits**.
- Earn credits from enemy kills and +25cr per wave cleared.
- The economy is tight — plan your tower placements carefully before spending.

## Tips

- Place Spikes and Mud traps on the path first for cheap early control.
- Laser Rods are powerful but require two aligned rods to activate.
- Missile Launchers are expensive but devastate large clusters of enemies.
- Boomerang towers are cost-efficient — each projectile hits enemies twice.
- Save credits before boss waves (wave 10, 20, 30, …) for emergency purchases.

## Technical Details

- Single-file game: all logic, CSS, and Canvas rendering in `index.html` (~3200 lines).
- No external dependencies, no build step.
- Vanilla JavaScript (ES6+) with `requestAnimationFrame` game loop.
- Fixed-timestep accumulator for consistent speed across different display refresh rates.
- All graphics are procedurally drawn on Canvas — no image assets.
