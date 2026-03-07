# ⚔ AlgoQuest — Algorithm Visualization Game

A dark arcade-themed browser game that teaches **sorting**, **searching**, and **graph algorithms** through interactive play. No installation required — runs entirely in the browser as a single HTML file.

🎮 **[Play Now](https://shakil281.github.io/algoquest/)**

---

## What Is This?

AlgoQuest makes computer science algorithms fun and visual. Instead of reading about Bubble Sort or A* on a whiteboard, you **play** them — with 8-bit music, animated planet backgrounds, and local multiplayer.

---

## Game Modes

### 👾 Monster Sorter

**🎮 PLAY Mode** — Sort the monsters yourself
- Drag and drop monsters to swap their positions (mouse and touch supported)
- Sort from lowest to highest HP
- **Hint system** (yellow glow) shows the optimal next swap
- Build a **COMBO** by following hints consecutively
- Optional **count-up timer** — toggle it on or off before you start
- Earn **1–3 stars** based on swap efficiency vs. the theoretical minimum

**👁 WATCH Mode** — Watch the algorithm sort automatically
- Choose **Bubble Sort**, **Quick Sort**, or **Merge Sort**
- Live **pseudocode highlighter** tracks the current line executing
- Step forward/backward one move at a time
- Adjustable animation speed
- Live counters: comparisons, swaps, steps

**⚔ VS MODE (Multiplayer)** — Up to 4 players compete on one device
- Enter names for 1–4 players on the setup screen
- Everyone sorts **the same monster arrangement** (fair start)
- Turn-based: after each player finishes, pass the device to the next
- Final **leaderboard** with 🥇🥈🥉 medals, ranked by stars → swaps → time

**Difficulty & Unlock System:**
| Level | Monsters | Unlock Requirement |
|-------|----------|--------------------|
| 🌱 Easy   | 6  | Always available |
| ⚔️ Medium | 8  | Beat Easy (≥ 1 star) |
| 💀 Hard   | 10 | Beat Medium (≥ 1 star) |

High scores (stars + best time) are saved per difficulty and shown on the level select screen.

---

### 🗺 Dungeon Escape

Watch **A\*** and **Dijkstra's algorithm** navigate a randomly generated dungeon maze.

- Toggle between **A\*** (Manhattan heuristic) and **Dijkstra** (no heuristic)
- **Paint walls** by clicking/dragging, **erase** with the erase tool
- **Move the start and end points** anywhere on the grid
- Live visualisation: open set (blue), visited nodes (dim), current node (yellow)
- The final **path glows cyan** when found
- **Priority queue panel** shows top candidates being evaluated
- Live counters: visited nodes, queue size, path length, frame count
- Touch supported on mobile
- **New Maze** button generates a fresh random dungeon

---

### 🔍 Binary Search

Pick a number from a sorted array and watch Binary Search home in on it.

- Click any number in the sorted array to set it as the target
- Watch LO, MID, HI pointers animate step by step
- Live **pseudocode highlighter** synced to each step
- Step forward/backward or run automatically
- Complexity display: O(log n) time, O(1) space

---

### 🕸️ BFS / DFS Graph

Explore a 10-node graph with **Breadth-First Search** or **Depth-First Search**.

- Click any node to set it as the start point, then hit **RUN**
- Watch nodes light up in traversal order
- Live **queue** (BFS) or **stack** (DFS) panel shows what's next
- Traversal order badges animate at the bottom
- Compare BFS (level-by-level) vs DFS (deepest branch first)

---

## Algorithms Covered

### Sorting
| Algorithm | Time Complexity | Space | Notes |
|-----------|----------------|-------|-------|
| Bubble Sort | O(n²) | O(1) | Simple, great for step-by-step visualization |
| Quick Sort  | O(n log n) avg | O(log n) | Pivot-based partitioning |
| Merge Sort  | O(n log n) | O(n) | Divide and conquer |

### Searching
| Algorithm | Time Complexity | Space | Notes |
|-----------|----------------|-------|-------|
| Binary Search | O(log n) | O(1) | Requires sorted array |

### Pathfinding
| Algorithm | Heuristic | Finds Optimal Path |
|-----------|-----------|--------------------|
| A*        | Manhattan distance | Yes |
| Dijkstra  | None (h = 0) | Yes |

### Graph Traversal
| Algorithm | Data Structure | Characteristic |
|-----------|---------------|----------------|
| BFS | Queue | Shortest path, level-by-level |
| DFS | Stack | Deep exploration first |

---

## Scoring System (Monster Sorter — PLAY Mode)

Stars are awarded based on **swap efficiency**:

| Stars | Condition |
|-------|-----------|
| ⭐⭐⭐ | Swaps used ≤ 130% of optimal |
| ⭐⭐  | Swaps used ≤ 200% of optimal |
| ⭐    | Sorted, but used more than 2× optimal swaps |

**Optimal swaps** = inversion count of the original array (theoretical minimum adjacent swaps to sort).

---

## Features

| Feature | Details |
|---------|---------|
| 🎵 8-bit Music | Original looping melody (C major, 144 BPM, I–V–vi–iii–I–IV–V–I) with square wave melody + triangle bass. Toggle on/off, persists across sessions. |
| 🔊 Sound Effects | Web Audio API: swap, compare, combo, sorted fanfare, path found, unlock jingle, and more. |
| 🌌 Planet Worlds | 7 animated backgrounds — Deep Space, Moon, Earth, Mars, Jupiter, Saturn (with ring), Neptune. Each tints the UI and spins a CSS 3D sphere. |
| ☀️ Dark / Light Theme | Full theme toggle with CSS custom properties. Saved to localStorage. |
| 📱 Mobile Support | Touch drag-and-drop for Monster Sorter; touch painting for Dungeon Escape. |
| 🏆 High Scores | Best stars + time saved per difficulty, shown on level select. |
| 🔒 Difficulty Unlock | Medium and Hard are locked until you clear the previous difficulty. |
| ⏱ Optional Timer | Count-up timer in Monster Sorter PLAY mode — user-toggleable. |
| ⚔ Multiplayer | Local 1–4 player VS mode with name entry and final leaderboard. |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI framework | React 18 (via CDN, no build step) |
| Transpiler | Babel Standalone |
| Audio | Web Audio API (procedural, no audio files) |
| Styling | Pure CSS with custom properties |
| Font | Press Start 2P (Google Fonts) |
| Hosting | GitHub Pages |
| Language | JavaScript (JSX) |

Everything lives in a **single `index.html` file** — no Node.js, no npm, no bundler.

---

## How to Run Locally

```bash
# Clone the repo
git clone https://github.com/Shakil281/algoquest.git

# Open in browser
open algoquest/index.html       # macOS
start algoquest/index.html      # Windows
xdg-open algoquest/index.html   # Linux
```

No server needed. No dependencies to install.

---

## Component Architecture

```
<App>
  ├── <GameMenu />           — Mode selector, planet picker, theme/music/mute toggles
  ├── <LevelSelect />        — Easy / Medium / Hard with unlock locks and high scores
  ├── <MultiSetup />         — 1–4 player name entry for VS mode
  ├── <MultiResults />       — Final leaderboard after all players finish
  ├── <SortingGame />
  │   ├── PLAY mode          — Drag-to-swap, hint glow, combo counter, optional timer
  │   ├── WATCH mode         — Auto-animation with pseudocode sync and step controls
  │   └── <ResultsOverlay /> — Stars, efficiency %, pass-to-next-player (multiplayer)
  ├── <PathfindingGame />
  │   ├── 18×24 dungeon grid — Interactive wall painter with touch support
  │   ├── Priority queue panel
  │   └── A* / Dijkstra controls
  ├── <BinarySearchGame />   — Sorted array with animated LO/MID/HI pointers
  └── <GraphGame />          — SVG graph with BFS/DFS animation and queue/stack panel
```

---

## Development Notes

- Sorting steps are **pre-computed** as snapshots, then played back frame-by-frame via `setTimeout`
- Pathfinding and graph traversal run the **full algorithm first**, record every frame, then animate the replay
- Binary Search records every step (lo, hi, mid, phase) and replays them
- The **hint system** finds the first adjacent out-of-order pair in the current player array
- **Inversion count** is the par value — it's the theoretical minimum adjacent swaps to sort
- Drag-and-drop uses `mousedown` / `mouseenter` / `mouseup` with a `stateRef` to avoid stale closures
- Touch support uses `document.elementFromPoint` to detect which card the finger is over
- Music uses the Web Audio **lookahead scheduler** pattern: schedules notes 300ms ahead, re-runs every 80ms
- Planet backgrounds use CSS `background-position` animation on `radial-gradient` to simulate a rotating sphere
- All user preferences (theme, planet, mute, music, scores) persist via `localStorage`
- In multiplayer, `key={playerIndex}` on `<SortingGame>` forces a full remount between turns so each player gets a fresh state with the same initial monster arrangement

---

## License

MIT — free to use, share, and modify.

---

Built with ❤️ using React + vanilla CSS + Web Audio API. Designed to make algorithms click.
