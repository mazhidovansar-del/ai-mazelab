# MazeLab — AI Search Studio

An interactive, browser-based AI project for **AI Fundamentals (AIF1303)**. It visualizes intelligent-agent problem formulation, search, constraint satisfaction, Bayesian probability updates and two-state MDP decisions.

## Run locally

No package installation or build step is needed. Open `index.html` in a modern browser, or serve the folder with Python:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Interactions

- Choose A*, BFS, uniform-cost search (UCS), or Greedy best-first search.
- Change the heuristic (Manhattan or Euclidean) and grid size.
- Draw/remove walls, reposition start and goal, and add high-cost cells (entry cost 2).
- Animate the search, inspect it step by step, compare all search algorithms, solve a zone CSP with backtracking/MRV/forward checking, and export/re-import maze JSON. The expandable **Compare methods and learn AI** section also includes two interactive labs: Bayesian corridor-risk updating and an MDP decision between Proceed and Detour.
- Use keyboard shortcuts: **W** wall, **E** eraser, **S** start, **G** goal, **T** weighted cell.

## Course-topic alignment

The official syllabus covers ten weeks. This project implements a focused subset rather than claiming to implement every course topic:

| Week | Syllabus topics | Where represented |
|---|---|---|
| 1 | Introduction to AI: agents and environments | Agent, goal, observable deterministic grid environment, legal actions |
| 2 | Uninformed search, A* and heuristics | BFS, UCS, A*, Greedy, Manhattan/Euclidean heuristics, explored-state visualization |
| 3 | Local search and constraint satisfaction | Interactive zone-coloring CSP with backtracking, minimum-remaining-values ordering and forward checking; editable maze constraints (hill climbing, random restart and simulated annealing are not implemented) |
| 5 | Markov decision processes and reinforcement learning | Two-state Clear/Blocked MDP; value iteration compares discounted expected costs for Proceed vs Detour |
| 6 | Probability and Bayesian networks | Bayesian corridor demo updates a prior blocked probability with an alert/clear sensor report using Bayes' rule |

The app implements selected topics from weeks 1–3, 5 and 6. The MDP and Bayesian labs are simplified teaching models, not real-world navigation or sensor systems. Other syllabus topics remain outside scope: adversarial search/game trees (week 4), reinforcement learning/Q-learning beyond the MDP example (week 5), HMMs (week 7), classical ML (week 8), neural networks (week 9), and LLMs/generative AI/AI safety (week 10).

## Algorithms and interpretation

- **A\*** ranks a frontier state with `f(n) = g(n) + h(n)`. With nonnegative costs and Manhattan distance on this four-neighbor grid, it returns a minimum-cost path.
- **BFS** minimizes the number of moves when all steps have equal cost; it does not account for weighted cells.
- **UCS** prioritizes accumulated path cost and finds the minimum-cost route with the supplied positive cell-entry costs.
- **Greedy best-first** prioritizes estimated distance only and is not guaranteed to find an optimal route.
- **Bayesian inference lab:** computes `P(blocked | report)` from a user-set prior, sensor sensitivity, false-alarm rate and alert/clear observation.
- **Two-state MDP lab:** models Clear and Blocked states, action-specific transitions and costs; value iteration estimates discounted long-term cost, then compares Proceed and Detour at the user-set initial belief.

The search is synchronous JavaScript in the browser. The displayed runtime measures algorithm computation only and varies by device/browser. Animation speed affects playback, not the computed route.

## Error handling and manual checks

The interface prevents start/goal overlap and prevents a weighted tile from being placed over a wall. If no route exists, it reports that state and shows explored cells without drawing a solution path. Random maze generation checks reachability and retries if the goal is blocked off.

Suggested manual checks:

1. Load the page and solve the default maze; confirm the route reaches G from S.
2. Compare algorithms on the same maze and inspect explored nodes, moves, cost and time.
3. Add a wall and confirm the route changes; build a full barrier and confirm “No path”.
4. Place a high-cost cell on a corridor and compare UCS/A* with BFS/Greedy.
5. Change grid size, generate a maze, use step-through, export JSON and import that export.
6. Import malformed JSON and confirm the app shows an error without changing the current maze.
7. Open the Bayesian lab; change the prior and sensor report and confirm the posterior and formula update.
8. Open the MDP lab; vary blockage belief and costs and confirm the expected costs and recommended action update (higher risk can favor Detour).

## Project files

- `index.html`, `styles.css`, `app.js` — application.
- `TECHNICAL_REPORT.md` — technical report, evaluation approach and AI-use declaration draft.
- `presentation/` — editable 6-slide PowerPoint deck, browser presentation source (HTML), and a print-to-PDF guide.
- `DEMO_SCRIPT.md` — 2–3 minute video narration and shot list.
- `COURSE_MAP.md` — all topics listed in the supplied syllabus.

## Responsible AI use and contribution

The supplied course syllabus says substantive GenAI assistance must be declared with tool/model, purpose, key prompts, contribution, and verification. This implementation was drafted with OpenAI Codex assistance for interface/code generation and documentation. The student/team must review the source, run the checks, replace this draft with the actual tool/model/date and prompts used, and document each participant's real contribution before submission. Do not claim unperformed testing or authorship.

No generative AI model is embedded in or used at runtime by the maze-solving algorithms.
