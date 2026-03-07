# ⚔ AlgoQuest — Algorithm Visualization Game

A dark arcade-themed browser game that teaches **sorting algorithms** and **pathfinding algorithms** through interactive play. No installation required — runs entirely in the browser as a single HTML file.

🎮 **[Play Now](https://shakil281.github.io/algoquest/)**

---

## What Is This?

AlgoQuest makes computer science algorithms fun and visual. Instead of reading about Bubble Sort or A* on a whiteboard, you **play** them:

- In **Monster Sorter**, you drag monsters into order and watch sorting algorithms animate in real time
- In **Dungeon Escape**, you build maze walls and watch pathfinding algorithms navigate around them

---

## Game Modes

### 👾 Monster Sorter

Two sub-modes:

**🎮 PLAY Mode** — You sort the monsters manually
- Drag and drop monsters to swap their positions
- Sort them from lowest to highest HP
- A **hint system** (yellow glow) shows the optimal next swap
- Build a **COMBO** by following hints consecutively
- Earn **1–3 stars** based on how close you are to the optimal number of swaps
- Your score is compared against the minimum possible swaps (inversion count)

**👁 WATCH Mode** — Watch the algorithm sort automatically
- Choose between **Bubble Sort**, **Quick Sort**, or **Merge Sort**
- Live **pseudocode highlighter** shows the current line executing
- Step forward/backward one move at a time
- Adjust animation speed from very fast to very slow
- Live counters for comparisons, swaps, and steps

**Difficulty levels:**
| Level | Monsters |
|-------|----------|
| 🌱 Easy   | 6  |
| ⚔️ Medium | 8  |
| 💀 Hard   | 10 |

---

### 🗺 Dungeon Escape

Watch **A\*** and **Dijkstra's algorithm** navigate a randomly generated dungeon maze.

**Features:**
- Toggle between **A\*** (uses heuristic) and **Dijkstra** (no heuristic) to compare behavior
- **Paint walls** by clicking and dragging on the grid
- **Erase walls** with the erase tool
- **Move the start and end points** anywhere on the grid
- Watch the **open set** (blue), **visited nodes** (dim), and **current node** (yellow) update live
- The final **path glows cyan** when found
- Live **priority queue panel** shows the top candidates being evaluated
- Live counters: visited nodes, queue size, path length, frame count
- Adjustable animation speed
- **New Maze** button generates a fresh random dungeon

---

## Algorithms Covered

### Sorting
| Algorithm | Time Complexity | Space | Notes |
|-----------|----------------|-------|-------|
| Bubble Sort | O(n²) | O(1) | Simple, great for visualization |
| Quick Sort  | O(n log n) avg | O(log n) | Pivot-based partitioning |
| Merge Sort  | O(n log n) | O(n) | Divide and conquer |

### Pathfinding
| Algorithm | Heuristic | Finds Optimal Path |
|-----------|-----------|--------------------|
| A*        | Manhattan distance | Yes |
| Dijkstra  | None (h = 0) | Yes |

---

## Scoring System (Monster Sorter — PLAY Mode)

Stars are awarded based on **swap efficiency**:

| Stars | Condition |
|-------|-----------|
| ⭐⭐⭐ | Swaps used ≤ 130% of optimal |
| ⭐⭐  | Swaps used ≤ 200% of optimal |
| ⭐    | Sorted, but more swaps than 2× optimal |

**Optimal swaps** = number of inversions in the original array (minimum adjacent swaps needed to sort).

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI framework | React 18 (via CDN, no build step) |
| Transpiler | Babel Standalone |
| Styling | Pure CSS (no framework) |
| Font | Press Start 2P (Google Fonts) |
| Hosting | GitHub Pages |
| Language | JavaScript (JSX) |

Everything lives in a **single `index.html` file** — no Node.js, no npm, no bundler.

---

## How to Run Locally

Just open the file in any browser:

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

## Project Structure

```
algoquest/
└── index.html      # Entire game — HTML + CSS + React JSX
```

### Component Architecture

```
<App>
  ├── <GameMenu />          — Mode selector with animated title
  ├── <LevelSelect />       — Easy / Medium / Hard difficulty picker
  ├── <SortingGame />
  │   ├── PLAY mode         — Drag-to-swap with hint + combo + stars
  │   ├── WATCH mode        — Auto-animation with pseudocode sync
  │   └── <ResultsOverlay/> — Star rating + efficiency score
  └── <PathfindingGame />
      ├── <DungeonGrid />   — Interactive 18×24 cell grid
      ├── <AlgoPanel />     — Algorithm description + priority queue
      └── Controls          — Speed slider, tool picker, run/reset
```

---

## Development Notes

- Sorting steps are **pre-computed** as an array of snapshots, then played back frame-by-frame using `setTimeout`
- Pathfinding runs the **full algorithm first**, records every frame, then animates the replay
- The **hint system** uses bubble sort logic on the current player array: find the first adjacent pair out of order
- **Inversion count** is used as the par value — it represents the theoretical minimum adjacent swaps
- Drag-and-drop uses `mousedown` / `mouseenter` / `mouseup` events with a `stateRef` to avoid stale closures in global event listeners

---

## Screenshots

| Monster Sorter — PLAY | Monster Sorter — WATCH | Dungeon Escape |
|---|---|---|
| Drag monsters, follow hints | Live pseudocode + step controls | A* vs Dijkstra comparison |

---

## License

MIT — free to use, share, and modify.

---

Built with ❤️ using React + vanilla CSS. Designed to make algorithms click.
