# Gothic Lockpick — Plate Alignment Puzzle Engine & Solver

<p align="center">
<img width="554" height="554" alt="image" src="https://github.com/user-attachments/assets/a2f5e0f6-1639-488f-9bf5-ab067ae87d44" />
</p>

A browser-based lockpicking mini-game and solver inspired by the **Gothic 1 Remake**. No installation required — just open the HTML file in any modern browser.

> **[Live Demo / Source](https://gaonmaor.github.io/gothic_lockpick_solver/gothic_lockpick_solver.html)**

## Features

### Game Modes

| Mode | Description |
|------|-------------|
| **Game** | Skill-based play with limited picks and mistake tolerance. Mimics the in-game experience. |
| **Free Practice** | Unlimited attempts with no penalties. Experiment freely. |
| **Hint** | Shows directional hints and remaining moves for each plate. |
| **Solution Viewer** | Step through the optimal BFS-computed solution one move at a time, or auto-solve. |

### Puzzle Sources

- **Generate** — Random solvable puzzles based on difficulty presets.
- **Visual Set** — Interactive wizard to copy a lock from the game:
  1. Set pin positions bar by bar (← →, Enter to confirm).
  2. Set dependencies bar by bar (↑ ↓ to navigate, → same-dir link, ← inverse link).
  3. Press Enter to finalize — the solver immediately checks solvability.
- **Manual (JSON)** — Paste/load a puzzle in JSON format for sharing or archiving.

### Difficulty & Configuration

| Preset | Plates | Connection Density | Min Steps |
|--------|--------|--------------------|-----------|
| Easy | 4 | Low (0.4×) | 3 |
| Medium | 5 | Moderate (0.8×) | 8 |
| Hard | 6 | Heavy (1.5×) | 18 |
| Very Hard | 7 | Maximum (2.0×) | 30 |
| Custom | 2–10 | User-defined | — |

Additional options:
- **Channel Width**: 3–13 positions (always odd; center is the target).
- **Varied Targets**: Toggle per-plate unique target positions (off = Gothic-style center alignment).
- **Skill Level**: Controls mistake tolerance (2 / 4 / 6) and reset severity.
- **Picks**: 1–20 lockpicks per attempt.

### Core Mechanics

- **Directed connections**: Moving one plate can drag linked plates — same direction or inverse.
- **Chain reactions**: Connections compound through chains (A→B→C).
- **Wall collisions**: Moving a plate (or any dragged plate) beyond its channel bounds triggers a mistake.
- **Pick breaks**: Exceeding the mistake tolerance breaks the pick. Skill level 0 fully resets all plates; levels 1–2 preserve progress.
- **BFS solver**: Finds the shortest solution path. Verifies solvability for generated and manual puzzles.

## Controls

### Game / Free / Hint Modes

| Key | Action |
|-----|--------|
| **W / ↑** | Select previous plate |
| **S / ↓** | Select next plate |
| **A / ←** | Move plate left |
| **D / →** | Move plate right |
| **R** | Reset to initial state |
| **Space** | Step through solution (Solution Viewer) |

### Visual Set — Dependency Phase

| Key | Action |
|-----|--------|
| **↑ / ↓** | Navigate between bars |
| **→** | Add/toggle same-direction link |
| **←** | Add/toggle inverse-direction link |
| **Enter** | Confirm & advance to next bar |
| **Esc** | Cancel setup |

## JSON Format

Puzzles can be exported and shared as JSON:

```json
{
  "plates": [
    { "initial_pos": 0, "target_pos": 3, "min_pos": 0, "max_pos": 6 },
    { "initial_pos": 5, "target_pos": 3, "min_pos": 0, "max_pos": 6 }
  ],
  "connections": {
    "0": [{ "target": 1, "dir": 1 }]
  }
}
```

- `dir: 1` — same direction (dragged plate moves with source).
- `dir: -1` — inverse direction (dragged plate moves opposite).

## Usage

1. Open `gothic_lockpick.html` in any modern browser.
2. Select a difficulty and click **New Lock**.
3. Play, practice, or use the solver to study the optimal solution.

To copy a lock from the game:
1. Set Source to **Visual Set** and click **New Lock**.
2. Follow the on-screen wizard to position pins and define dependencies.
3. Switch to **Solution Viewer** mode and click **Solve All** to see the answer.

## Technology

Single self-contained HTML file. No build tools, no dependencies, no server required.

- Vanilla JavaScript (ES6 class)
- CSS custom properties with a dark medieval theme
- BFS pathfinding for optimal solutions
- Responsive layout (mobile-friendly)

## Disclaimer

This project is a fan-made tool and is **not affiliated with, endorsed by, or connected to** Piranha Bytes, THQ Nordic, or any official Gothic franchise entity. "Gothic" is a trademark of its respective owners. This tool is intended for personal use, education, and community enjoyment.

## License

[MIT](LICENSE) — Copyright (c) 2026 Maor Gaon

## Author

**Maor Gaon** — [github.com/gaonmaor](https://github.com/gaonmaor)
