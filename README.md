# 🔴 PokéCraft

A blocky, Minecraft-style voxel sandbox running entirely in the browser — with a **Pokémon mode** baked in. You're the Trainer. Every animal is a Pokémon. The items are Pokémon-flavored. Built to play on an **iPhone** (or any phone / desktop).

No build step, no install, **no external dependencies** — it's plain HTML + CSS + JavaScript with a hand-rolled WebGL voxel renderer. Just open it in a browser.

## ✨ Features

- **Voxel world** with hills, water, sand beaches, and Berry trees (procedurally generated each load).
- **Mine & build** — break blocks and place them to build whatever you want.
- **Pokémon mobs** roaming the world:
  - 🐑 Sheep → **Wooloo**
  - 🐷 Pig → **Tepig**
  - ⚡ Bonus → **Pikachu**
- **Catch them!** Aim at a Pokémon and throw a Poké Ball. Your Pokédex count is tracked in the HUD.
- **Pokémon-themed blocks**: Thunder Stone Ore, Fire Stone Block, Water Stone Block, Potion Brick, Berry Logs/Leaves, Water (HM03).
- **Full iPhone touch controls**: on-screen joystick, drag-to-look, jump / mine / place buttons, fly toggle.
- **Fly mode** for creative building.

## 📱 How to play on your iPhone

The game is a static website, so you just need to open `index.html` in Safari. Easiest options:

**Option A — GitHub Pages (recommended)**
1. Push this branch and merge to your default branch.
2. In your repo: **Settings → Pages → Build from branch → `main` / root**.
3. Open the published URL (e.g. `https://<you>.github.io/whatever/`) in Safari on your iPhone.
4. Tap **Share → Add to Home Screen** for a full-screen, app-like experience.

**Option B — Run a quick local server (same Wi-Fi)**
```bash
cd whatever
python3 -m http.server 8000
```
Then on your iPhone (same Wi-Fi) open `http://<your-computer-ip>:8000`.

> Tip: it also works opened directly as a `file://` path, but a local server matches how it'll run on GitHub Pages.

## 🎮 Controls

### iPhone / touch
| Action | Control |
| --- | --- |
| Move | Left joystick |
| Look around | Drag anywhere on the right side |
| Jump | ⤴ button |
| Mine block | ⛏ button |
| Place block | ▣ button |
| Throw Poké Ball | Double-tap the right side |
| Select item | Tap a hotbar slot |
| Fly | ✈ Fly button (top-right) |

### Desktop
| Action | Control |
| --- | --- |
| Move | WASD |
| Look | Mouse (click to lock pointer) |
| Jump | Space |
| Mine | Left click |
| Place | Right click |
| Throw Poké Ball | Q (or middle click) |
| Select item | 1–9 |
| Fly | F |

## 🧱 Project structure
```
index.html   — markup, HUD, loading + menu screens
style.css    — all styling, including the touch UI
game.js      — the whole engine: world gen, meshing, physics, mobs, controls
```

Everything is intentionally dependency-light and in one place so it's easy to hack on. Want a new Pokémon? Add an entry to `MOB_TYPES` in `game.js`. Want a new block? Add it to `BLOCKS`.

Have fun, Trainer! 🔴

---

# 🏰 Creep Keep — Tower Defense

A second, completely separate game lives in this repo: **`towerdefense.html`**. Open that
one file in any browser (or `python3 -m http.server 8000` and visit `/towerdefense.html`).
Like PokéCraft it's dependency-free — one self-contained HTML file, canvas 2D.

Creeps march the dirt road from the left edge to the right. Build towers on the grass,
spend the gold they drop, and don't let 20 lives run out before wave 20 is broken.

## 🗼 Towers

| Tower | Cost | Range | Damage | Rate | Special |
| --- | --- | --- | --- | --- | --- |
| Arrow Nest | 70g | 3.1 | 14 | 1.80/s | Cheap, fast single-target shots |
| Bombard | 135g | 2.7 | 36 | 0.62/s | Lobbed shells, 1.2-tile splash |
| Frost Spire | 110g | 2.5 | 9 | 1.00/s | Pulses; slows every creep in range 45% for 1.8s |
| Arcane Beam | 240g | 5.4 | 95 | 0.50/s | Long reach, hitscan beam, ignores armor |

Every tower has two upgrade tracks, four levels each: **damage** (+35% per level) and
**fire rate** (+20% per level). Upgrade cost scales with the level; selling refunds 65%
of everything invested in that tower. Each tower also has a targeting mode —
first / strongest / closest.

## 👾 Creeps

Grunts, fast Runners, armored Wraiths, heavy Brutes, and a Warlord boss on waves 10, 15
and 20 (three of them on the last wave). Health scales with the wave number; armor
subtracts flat damage from every hit, so armored waves want Arcane Beams or bigger hits.

## 🎮 Controls

| Action | Control |
| --- | --- |
| Pick a tower | Click a shop card, or `1`–`4` |
| Build | Click a grass tile (hold Shift to keep building the same type) |
| Inspect / upgrade | Click a built tower |
| Upgrade damage / fire rate | `U` / `I` |
| Sell tower | `X` |
| Cancel selection | `Esc` or right-click |
| Send the next wave early | `Enter` (early call pays a gold bonus) |
| Pause | `Space` |
| Fast-forward 2× | `F` |

Clearing a wave pays a bonus, and calling a wave in early pays 3g per second of prep time
you skip. Survive all 20 waves for the victory screen; lose all 20 lives and it's game
over — either way the end screen restarts with one button.
