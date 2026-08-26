# NEXUS DEFENSE

A browser-based tower defense game with a cyberpunk/sci-fi aesthetic. No installation required — just open `index.html` in your browser and play.

## How to Play

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. On the **cover screen**, choose your **Boss Mode** (Enhanced or Classic).
3. Select a tower from the **SHOP** panel on the right.
4. Place towers on the grid (not on the enemy path).
5. Click **LAUNCH WAVE** to send enemies — survive all waves to win.
6. Earn credits from kills and wave clears to buy and upgrade towers.
7. Use the **DISASTER** panel for powerful one-time abilities during tough waves.

**You lose if the amount of lives you have hits zero.**

## Boss Mode (Cover Screen)

Choose before starting a new game:

| Mode | Description |
|------|-------------|
| **Enhanced** | Bosses gain special powers at higher waves (see Boss section below) |
| **Classic** | All bosses have standard stats only — no immunities or special abilities |

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
| Spinning Laser Rod | 200cr | Rotating laser beams around a central axis; upgrades add beams and length |
| Sawblade | 120cr | Rotating physical sawblades on arms; damages enemies touching the blade only |
| Cannon | 150cr | Slow, explosive; requires bombs as ammo |
| Crossbow | 150cr | Extreme-range sniper (10.5 cells) |
| Flamethrower | 300cr | Close-range AOE cone (2 cells), rapid fire |
| Minigun | 300cr | High fire rate with rotating barrel animation |
| Laser Turret | 300cr | Instant hitscan beam with visual retract effect |
| Boomerang | 100cr | Projectile flies out and returns, piercing all enemies twice |
| Nuke | 500cr | One-time board-wide clear (5000 damage) |
| Missile Launcher | 1000cr | Homing missiles with massive AOE (10000 damage, 20-cell range) |
| Super Turret | 2000cr | Fires bullets across the entire board |
| Tazor | 5000cr | Continuous 500 dmg/frame electric arcs to all enemies in range; bypasses all immunities |
| Energy Launcher | 6000cr | Fires a continuous beam to the board edge toward nearest enemy; 1000 dmg/frame, bypasses all immunities |

All towers can be upgraded up to **level 5** by clicking on a placed tower. Right-click to delete and receive a partial refund.

### Spinning Laser Rod & Sawblade Upgrades

Both towers share the same upgrade progression:

| Level | Arms/Blades | Arm Length |
|-------|-------------|------------|
| 1 | 1 | 4 cells |
| 2 | 2 | 5 cells |
| 3 | 3 | 6 cells |
| 4 | 4 | 7 cells |
| 5 | 6 | 8 cells |

## Disasters

Accessed via the **DISASTER** panel. Instant disasters (Lightning, Tsunami, Earthquake, Blizzard, Hailstorm) arm on click and fire each time you click the board — you can rapid-fire them. Placement disasters (Volcano, Tornado, Meteor, Black Hole, Void) prompt you to click a location on the board.

| Name | Cost | Description |
|------|------|-------------|
| Lightning | 150cr | Strikes 3 random enemies for 8000 dmg (3000 to bosses) |
| Tsunami | 200cr | Wave sweeps the entire board, stunning and damaging all enemies |
| Earthquake | 200cr | Stuns all enemies and cracks the ground |
| Volcanic Eruption | 1000cr | Place a lava pool that deals continuous damage for 60s |
| Tornado | 500cr | Place a tornado that slows and damages enemies for 60s |
| Meteor | 250cr | Aim a column — a meteor falls and hits up to 5 enemies for 8000 dmg each |
| Blizzard | 250cr | Freezes all enemies in place for 3 seconds |
| Black Hole | 700cr | Place a gravitational well — slows enemies to 8% speed and deals 1000 dmg/0.5s for 30s |
| Hailstorm | 300cr | 8 seconds of random hail pellets raining across the board, 1500 dmg per hit |
| Void | 5000cr | Place a void rift dealing 500 dmg/frame to all enemies in range for 2 minutes; bypasses all immunities |

## Enemies

- **Regular enemies**: HP scales with wave number and tier. Speed 1.2. Reward 10–50cr.
- **Boss enemies** (every 10th wave): 8× HP of the prior wave's max, speed 0.6. Reward 50–150cr.
- Boss enemies have splash damage resistance (bomb/cannon AOE deals 1/8 damage).

Enemies follow two branching paths (upper and lower) that share entry and exit corridors, and randomly pick a path each spawn.

## Boss Powers (Enhanced Mode)

| Wave | Boss Type | Special Abilities |
|------|-----------|-------------------|
| 30+ | Standard Boss | Crushes adjacent towers while moving; explodes on death destroying structures within 3 cells |
| 60+ | Armored Boss | Immune to bullets (turret, super turret, boomerang, crossbow, minigun) |
| 80+ | Fortress Boss | Immune to bullets AND explosives (missile launcher, bomb, nuke, cannon) |
| 120, 150, 180… | Siege Boss | Bullet + explosive immune; fires homing missiles at nearest tower every 5 seconds |

Use **Tazor**, **Energy Launcher**, or the **Void** disaster to damage immune bosses — they bypass all immunities.

## Economy

- Start with **150 credits**.
- Earn credits from enemy kills and +25cr per wave cleared.
- The economy is tight — plan your tower placements carefully before spending.

## Tips

- Laser Rods are powerful but require two aligned rods to activate.
- Spinning Laser Rod and Sawblade are great for covering path intersections.
- Sawblades only deal damage when the spinning blade itself touches an enemy — position carefully.
- Missile Launchers are expensive but devastate large clusters of enemies.
- Tazor and Energy Launcher bypass all boss immunities — essential for late-game Siege Bosses.
- Save credits before boss waves (wave 10, 20, 30, …) for emergency purchases.
- In Classic mode, any tower combination can handle all bosses.

## Technical Details

- Single-file game: all logic, CSS, and Canvas rendering in `index.html` (~6800 lines).
- No external dependencies, no build step.
- Vanilla JavaScript (ES6+) with `requestAnimationFrame` game loop.
- Fixed-timestep accumulator for consistent speed across different display refresh rates.
- All graphics are procedurally drawn on Canvas — no image assets.
