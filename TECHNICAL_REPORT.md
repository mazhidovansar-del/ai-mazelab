# Technical Report — MazeLab: AI Search Studio

**Course:** AI Fundamentals (AIF1303), 2026–2027  
**Project type:** Interactive AI search visualization  
**Status:** Source and documentation prepared; run the manual checks before submitting.

## 1. Problem and objectives

The application models a maze as a deterministic, fully observable search problem. The agent starts in a cell and must reach a goal while avoiding blocked cells and accounting for cells with higher entry cost. Users can change the world and inspect the agent's search behavior.

The project implements three syllabus weeks: (1) intelligent agents and environments; (2) uninformed search, A* and heuristics; and (3) constraint satisfaction through an interactive zone-coloring CSP solved with backtracking, minimum-remaining-values ordering and forward checking. The maze's legal-cell rules add a second constraint example. The syllabus's hill-climbing, random-restart and simulated-annealing methods are outside this version's scope.

## 2. Problem formulation

- **State:** a coordinate `(x, y)` for one walkable grid cell.
- **Initial state:** user-positioned start cell `S`.
- **Actions:** move one cell north, east, south or west.
- **Transition model:** deterministic movement to an adjacent in-bounds, non-wall cell.
- **Goal test:** current coordinate equals goal `G`.
- **Step cost:** 1 for a normal cell, 2 to enter a weighted cell.
- **Environment:** observable, deterministic, discrete and static during one search.
- **Constraints:** stay in bounds; never cross walls; use only legal moves; reach the goal; start and goal must be distinct.

## 3. Design and implementation

The app uses plain HTML, CSS and JavaScript with no build system or third-party runtime library. The grid is rendered as an accessible CSS grid. Editing tools mutate the maze model, and a search produces an ordered list of expanded states plus a predecessor-derived route. Playback animates that search order. Metrics report explored states, moves, weighted path cost and local compute time.

The frontier is a simple array sorted by priority at each expansion. This makes the algorithm easy to read for a course demonstration, though a binary heap would scale better for much larger grids.

### Search methods

| Method | Frontier priority | Expected interpretation |
|---|---|---|
| BFS | Depth / accumulated unit steps | Fewest moves if every transition has equal cost |
| UCS | `g(n)` | Minimum cost when costs are nonnegative |
| A* | `g(n) + h(n)` | Minimum cost with an admissible heuristic and appropriate graph-search handling |
| Greedy best-first | `h(n)` | Goal-directed exploration; not guaranteed optimal |

The UI supports Manhattan and Euclidean estimates. For four-neighbor movement with a minimum step cost of 1, Manhattan distance is admissible. Euclidean distance is also a lower bound for this grid. Weighted entry costs are positive and at least 1.

## 4. Interface and outputs

Users can choose an algorithm/heuristic, set grid dimensions and playback speed, draw or erase walls, move S/G, and place weighted terrain. “Find best path” animates the run; “Step through” allows inspection of expansion; “Compare algorithms” computes each method on one unchanged maze. Export saves the maze specification as JSON; import validates dimensions, coordinates and cell arrays before replacing the current world.

The visualization distinguishes explored cells from the final route. The route cost includes high-cost entries; path length is displayed as number of moves. Search time is measured with the browser's `performance.now()` and should be treated as an approximate, device-dependent observation. The separate zone planner models six variables, operational-mode domains, binary adjacency constraints and unary restrictions, then solves them with backtracking, MRV and forward checking.

## 5. Testing and error handling

Before submission, complete and record these manual checks in the target browser:

| Check | Procedure | Expected result |
|---|---|---|
| Default solution | Load and solve initial maze | Agent reaches goal and metrics populate |
| Algorithm comparison | Run comparison without editing maze | Four rows show exploration, moves, cost and time |
| Wall constraint | Draw a wall on an open route and solve | Search respects the changed environment |
| Unreachable goal | Draw a complete barrier across the board | “No path” is shown; no invalid route is drawn |
| Weighted route | Add weight 2 in a corridor; compare methods | UCS/A* account for entry cost; BFS optimizes moves |
| Start/goal validation | Try to put S and G in the same cell | User receives an explanation; positions stay distinct |
| Terrain validation | Try to place a weight on a wall | User receives an explanation |
| Responsive controls | Change size, generate maze, step, export and import a valid/invalid JSON file | Controls operate; invalid data produces an error without corrupting the current maze |
| Zone CSP | Open the zone planner | It returns a satisfying assignment and reports checks/backtracks |

Random maze generation retries when generated barriers make the goal unreachable. For unusually constrained grids this retry approach can be slow; the default range is intentionally modest. This report does not claim these checks were already run.

## 6. Results and interpretation

No benchmark values are asserted here because run-time metrics depend on the exact maze and browser. Capture the app's comparison table on the submission machine and include actual values in the oral defense. In general, BFS can return the fewest moves on a unit-cost grid but ignores terrain penalties; UCS and A* optimize the defined cost; Greedy may reduce exploration while returning a costlier route. A*'s explored-node advantage depends on maze shape and heuristic.

## 7. Limitations and next steps

1. The array-sorted frontier is pedagogical, not optimized for large maps.
2. Search runs synchronously; very large user-created grids can temporarily block UI updates.
3. The environment is deterministic and fully observable; there is no sensor noise or dynamic obstacle model.
4. The CSP demo solves a fixed six-zone mode-assignment problem; users cannot edit its graph or domains.
5. Local-search algorithms, minimax, MDP/RL, Bayesian inference, HMM, ML/NN and generative AI/safety are outside this version's implemented scope.

## 8. AI-use declaration and team contributions

The supplied syllabus requires disclosure of tool/model, purpose, key prompts, contribution and verification. Complete this record with the actual facts before submission:

| Declaration field | Draft to verify and complete |
|---|---|
| AI tool/model and date | OpenAI Codex; record the model/version and actual dates used |
| Purpose | Interface/code drafting, explanations, README/report/presentation scaffolding |
| Key prompts | “Build an interactive AI Maze Solver with intelligent agents, A*, CSP; …” plus follow-up requests for syllabus alignment and the visual reference |
| AI contribution | Generated initial HTML/CSS/JavaScript and draft project documentation |
| Human verification | Run the app and all checks in Section 5; review algorithm behavior and wording |
| Participant contributions | Add each person's name and specific work completed; do not infer contributions |

The application does not call a generative AI service at runtime. The named team should review, understand and be prepared to explain every submitted algorithm and code path.

## 9. Reproduction

Open `index.html` directly or run `python3 -m http.server 8000` and visit `http://localhost:8000`. No external service is required for search computation. The optional font import uses Google Fonts; system fallbacks keep the interface usable without it.
