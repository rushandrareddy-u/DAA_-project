# 🚌 College Bus Route Optimization — Algorithm Laboratory

Interactive DAA project: a college bus leaves the depot, visits every pickup, respects capacity, and returns — modelled as TSP with a capacity feasibility check.

## Run
Open `index.html` in any modern browser. No build step, no backend, no network, no libraries.

## Files
- `index.html` – structure · `style.css` – dark glass UI · `script.js` – everything else

## Architecture
`script.js` Part 1 (no DOM): validation → graph model → algorithms written as **generators** that yield state objects (`candidate`, `scan`, `select`, `move`, `dp-state`, `reconstruct`, `open`, `divide`, `base`, `merge`).
Part 2: the 3D canvas, telemetry, logs and panels only *consume* that stream, so visualization = execution.

| Algorithm | Time | Space | Optimal? |
|---|---|---|---|
| Brute force | O(n!) | O(n) | Yes (n ≤ 9 here) |
| Greedy nearest neighbor | O(n²) | O(n) | No |
| Held-Karp DP | O(n²·2ⁿ) | O(n·2ⁿ) | Yes (n ≤ 12 here) |
| Divide & Conquer heuristic | O(n²) | O(n) | No (heuristic) |

## Using it
Edit depot, capacity, speed, locations (add/edit/delete/reorder) and the distance matrix (symmetric mirroring). Pick an algorithm → START / PAUSE / NEXT STEP / RESTART / STOP, or 🚀 RUN ALL. 3D scene: drag = rotate, Shift-drag = pan, wheel / +− = zoom, arrows = rotate, click a node to inspect. 🎤 Presentation Mode simplifies the page.

## Notes
- Execution time = `performance.now()` around a headless run of each algorithm; it varies by hardware/browser.
- Estimated travel time = distance ÷ average speed (an estimate only).
- The code in the "How the program works" section is read from the running functions via `Function.toString()`.
- Engine verified against 200 random matrices: DP = brute force optimum; heuristics never beat it.
