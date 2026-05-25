# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file, browser-based Tic Tac Toe game with a North Carolina theme. No build step, no dependencies, no package manager — open `index.html` directly in any browser.

## Running the Project

```bash
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

## Architecture

Everything lives in `index.html` — inline CSS, inline JavaScript, and HTML markup in one file. No external assets except a Google Fonts import (`Playfair Display`, `Inter`).

**Key JS state:**
- `board` — 9-element array (`null | 'X' | 'O'`)
- `currentPlayer` — `'X'` or `'O'`
- `scores` — `{ X, O, tie }` persists across rounds

**Game loop:** `handleClick` → `checkWinner` (tests `WINNING_COMBOS`) → `endGame` or swap `currentPlayer`. `resetGame` clears the board but keeps scores.

## Version Control

Commit and push to GitHub regularly throughout any work session — after each meaningful change, not just at the end. This ensures no progress is ever lost.

- Use clear, descriptive commit messages (e.g. `Add AI opponent with difficulty levels` not `update stuff`)
- Push after every commit: `git add -A && git commit -m "..." && git push`
- Never batch unrelated changes into one commit

## NC Theme Details

- **Colors:** NC Navy `#13294B` (bg), Carolina Blue `#4B9CD3` (X), Old Gold `#C8A951` (O)
- **Win messages** are randomly picked from arrays in `WIN_MSGS`
- Pine tree footer strip is a CSS `body::after` pseudo-element with emoji
- NC state shape is an inline SVG path (rough silhouette, not geo-accurate)
