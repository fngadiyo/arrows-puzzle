# Arrows Puzzle (Guaranteed-Solvable Generation)

This project now uses a **reverse-construction generator** so each new puzzle is guaranteed solvable by design.

## How solvability is guaranteed

1. Start from an empty board.
2. Add one arrow at a time.
3. Each newly added arrow is forced to have a completely clear ray to the edge in its pointing direction (in the current partial board).
4. Therefore, in the final board, arrows can always be removed in reverse insertion order.
5. A dependency-elimination solver verifies solvability (`DAG`-style elimination of blockers).

## Difficulty knobs (easy to tweak)

In `index.html` inside `generateReverseSolvedLayout()`:

- `targetCount`: number of arrows.
- `maxSnakeLength`: max arrow path length.
- turn probability (`Math.random() < 0.35`): controls curvature.
- number of candidate attempts in `generateAsync` loop.

## Run locally

Open `index.html` directly in a browser, or serve with a simple local server.

```powershell
Set-Location "c:\Users\fadly\Documents\work\home\arrows"
python -m http.server 8000
```

Then visit `http://localhost:8000`.
