# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a browser-based Tic Tac Toe game implemented as a single HTML file with inline CSS and JavaScript. It supports two-player gameplay (X vs O) with persistent score tracking across multiple games.

## Running the Game

Open `tictactoe.html` directly in any web browser. No build process or dependencies are required.

## Architecture

The entire game is contained in a single file (`tictactoe.html`) with three layers:

### HTML Structure (lines 121–144)
- 3×3 grid of cells with `data-i` attributes (0–8 for board indexing)
- Score display showing X wins, O wins, and draws
- Status text showing current player or game result
- Reset button to start a new game

### CSS Styling (lines 7–119)
- Dark theme with red (#e94560) for X and cyan (#a8dadc) for O
- Hover effects and smooth transitions
- Pulse animation on winning cells
- Responsive cell layout using CSS Grid

### JavaScript Game Logic (lines 146–211)

**Game State:**
- `board`: 9-element array representing grid state (0–8 indexed, empty string = unplayed)
- `current`: Current player ('X' or 'O')
- `gameOver`: Boolean flag
- `score`: Object tracking wins for X, O, and draws

**Win Detection:**
- `WINS` array (line 147): All 8 winning combinations as index triplets
- `checkWin()`: Returns the winning triplet or null

**Game Flow:**
1. Click handler on cells validates move, updates board/UI, checks for win or draw
2. If win: highlight winning cells with `.win` class, update score, set gameOver
3. If draw: no winning cells, just update score and gameOver
4. If game continues: switch current player and update status text
5. Reset button calls `init()` to clear board and reset state

## Extending the Game

When modifying the game:
- **Changing board size**: Update grid dimensions in CSS (`grid-template-columns: repeat(3, ...)`) and `WINS` array with new winning combinations
- **Adding difficulty levels**: Implement an AI player function and add player mode selection
- **Persisting scores**: Use localStorage to save the `score` object across browser sessions
- **Styling changes**: All colors and animations are in the `<style>` block; reuse existing CSS variables for consistency

## Git Workflow

All changes must be committed locally and pushed to the GitHub repository: https://github.com/minhajafser/tictactoe

**Commit Practices:**
- Commit work frequently after completing meaningful units of functionality to avoid losing progress
- Write clean, descriptive commit messages that explain *what* changed and *why*
- Push commits to GitHub regularly (ideally after each significant piece of work)
- Never accumulate uncommitted changes for extended periods—regular commits are your safety net

**Example workflow:**
1. Make a small, focused code change
2. Test the change locally
3. Commit with a clear message (e.g., "Add win detection for diagonal matches")
4. Push to GitHub immediately

This ensures work is never lost and the repository always reflects the current state of the project.
