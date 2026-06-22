# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the app

Open `tictactoe.html` directly in a browser — no build step, no server required:

```powershell
Start-Process "tictactoe.html"
```

## Architecture

Everything lives in a single self-contained file: `tictactoe.html`.

- **CSS** (lines 7–101): dark-theme styles. Color palette: `#1a1a2e` background, `#e94560` for X/accent, `#4fc3f7` for O.
- **HTML** (lines 103–137): static board of 9 `.cell` divs with `data-i` attributes (0–8), a scoreboard, a status line, and a reset button.
- **JS** (lines 139–217): plain vanilla JS, no frameworks.
  - `WINS` — the 8 winning index triples, checked on every move.
  - `board` — flat `Array(9)` of `null | 'X' | 'O'`.
  - `scores` — `{ X, O, Draw }` object; persists across rounds (reset only on page reload).
  - `render()` — single source of truth for DOM state; call it after every state mutation.
  - `checkWinner()` — returns `{ winner, line }` on win, `{ winner: 'Draw' }` on full board, `null` otherwise.
  - Click handling uses event delegation on `#board`; winning cells get the `.winner-cell` class added after `render()`.

## Git workflow

After every meaningful change:
1. Stage specific files by name.
2. Commit with an imperative message describing *why* the change was made.
3. Push to keep GitHub in sync: `git push origin master`.

Remote: `https://github.com/casiopeia2/ClaudeCodeTest`
