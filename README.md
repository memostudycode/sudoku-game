# Sudoku‑Web
> Pure‑frontend infinite‑generation Sudoku puzzle web app. Zero backend, single‑file, deployable on GitHub Pages.

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](#)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](#)
[![JavaScript‑ES6+](https://img.shields.io/badge/JavaScript‑ES6%2B-F7DF1E?logo=javascript&logoColor=black)](#)

## 📖 About
A fully‑featured browser‑based Sudoku game built with vanilla HTML / CSS / JavaScript.
Designed for open‑source release and supports GitHub Pages static deployment.

Instead of static pre‑stored puzzle banks, this project implements a native Sudoku generation algorithm:
generate a valid full solution board, then perform hole‑digging with uniqueness verification to guarantee every puzzle has **exactly one valid solution**. Unlimited fresh puzzles are computed locally inside browser with no network requests.

Two gameplay modes:
- **Practice Mode**: casual play without timer pressure.
- **Time Mode**: speed‑challenge mode. Timer **does not auto‑start**, manually control via Start / Pause buttons.

Game progress, fastest record, total plays and unfinished game state persist via browser `localStorage`. Re‑opening the page triggers a modal to either continue previous game or restart.

### Core Features
- 6 difficulty levels: `Easy` / `Medium` / `Hard` / `Expert` / `Master` / `Extreme`
- Infinite unique‑solution puzzles (client‑side algorithm, no API calls)
- Dual game modes: Practice & Time Mode with manual Start / Pause timer
- Auto‑save unfinished game; resume / restart popup on launch
- Pencil note mode for candidate digits
- Undo stack (max 50 steps)
- Limited hint system
- In‑board conflict check & final submit validation
- Mistake counter (max 5 mistakes)
- Local statistics: fastest time, total play count, solved records
- Row / column / 3×3 box cell highlight
- Fully responsive layout (desktop & mobile)
- Zero dependencies, single HTML file, ready for GitHub Pages

## 🚀 Quick Start
### Local run
1. Copy the complete HTML source and save as `index.html`
2. Open it with any modern browser.
> No npm, no build tools, no server required.

### GitHub Pages Deployment
1. Create repository on GitHub.
2. Put `index.html` in repository root.
3. Go to repo → **Settings → Pages**
4. Source: `Deploy from a branch`; select `main` branch, folder `/ (root)`
5. Save, wait for deployment, your Sudoku website is live.
6. please visit https://memostudycode.github.io/sudoku-game/ .
> Because everything runs client‑side, Pages works perfectly without backend.

## 🎮 Usage Guide
### Difficulty Switch
Click difficulty label on top bar, new puzzle will generate instantly.

### Game Modes
1. **Practice Mode**: default, timer disabled.
2. **Time Mode**: switch mode, then click `▶ Start` to begin timing. Use `⏸ Pause` to freeze timer. Timer will **not auto‑run after mode switch**.

### Operations
- Click cell for selection; related row / column / box gets highlighted.
- Number panel for input; `⨯` clears cell content.
- `✏️ Pencil`: toggle note mode for candidate numbers.
- `↩ Undo`: revert last operation.
- `💡 Hint`: fill correct value for selected cell (limited count).
- `✅ Check`: scan board and mark conflict cells.
- `🚀 Submit`: final validation, requires full board filled.

### Persistent Behaviour
- Unfinished game auto‑saved to browser localStorage.
- Re‑open page shows modal: `Continue` / `Restart`.
- Statistics persist across browser sessions.
- Clearing browser storage wipes all local progress.

## ⚙️ Algorithm Brief
1. **Full board generation**: DFS backtracking with random shuffle to build complete valid 9×9 solution.
2. **Hole‑digging**: randomly remove cells. After each removal run solution counting check.
3. **Uniqueness guarantee**: accept hole only when puzzle keeps exactly one solution; restore cell if multiple solutions appear.
4. Different difficulty maps to different hole quantity.

> Higher difficulty (Master / Extreme) brings heavier computation; tiny browser freeze during generation is expected.

## 📂 Project Structure
sudoku‑web/

└── index.html # All source: HTML + CSS + JS
