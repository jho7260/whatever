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
