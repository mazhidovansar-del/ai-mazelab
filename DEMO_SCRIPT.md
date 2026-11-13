# Demo video script (about 3 minutes)

Keep the final video between 2 and 3 minutes; trim the narration or actions to fit. Record the browser at 1080p, with the maze and telemetry visible. Replace the bracketed names with the actual team members. Show the real run; do not use fabricated metrics.

| Time | Screen / action | Narration |
|---|---|---|
| 0:00–0:15 | Title and full app | “We built MazeLab, an interactive project for AI Fundamentals. It makes an agent's search through a maze visible.” |
| 0:15–0:35 | Point to grid, S, G, controls | “The maze is a deterministic environment. Cells are states, moves are actions, walls block transitions, and the agent's goal is to reach G from S.” |
| 0:35–0:55 | Select A*, Manhattan; Find best path | “A* combines the cost already paid, g, with an estimate to the goal, h. We use Manhattan distance for this four-direction grid. Blue cells show explored states; orange shows the final route.” |
| 0:55–1:15 | Explain telemetry | “The dashboard reports expanded states, number of moves, weighted route cost, and local runtime. Runtime depends on the device, so we use it as an observation rather than a universal speed claim.” |
| 1:15–1:35 | Draw a wall; solve again | “The user can change the environment. This wall changes which transitions are legal, so the agent has to search the updated state space.” |
| 1:35–1:55 | Add a weighted cell; compare algorithms | “Purple cells cost two to enter. UCS and A* account for that cost. BFS minimizes moves only, while Greedy follows the heuristic and is not guaranteed to return the cheapest route.” |
| 1:55–2:12 | Step-through; show compare table | “Step-through exposes the expansion order, and the comparison view runs all four strategies on the same maze. This connects to weeks one and two of the syllabus.” |
| 2:12–2:30 | Choose Bayesian in the method picker; change the prior or sensor report and run it | “The Bayesian lab begins with a prior chance that the corridor is blocked. Bayes' rule combines that belief with the sensor's reliability and updates the posterior. The sliders make the effect of the prior and evidence visible.” |
| 2:30–2:48 | Choose MDP in the method picker; vary blocked belief and run it | “The MDP lab has Clear and Blocked states. Value iteration compares the discounted expected costs of Proceed and Detour, including transition risk and the cost of being blocked. This is a simplified teaching model.” |
| 2:48–3:00 | Click **Try the constraint puzzle**; show assignment | “For week three, six zone variables receive one of three modes. Backtracking uses minimum-remaining-values ordering and forward checking to satisfy adjacency and domain constraints. [Name] worked on [actual contribution], and [Name] worked on [actual contribution].” |

## Recording checklist

- Use the final browser build and show a successful real solve.
- Capture the compare table on the actual maze for real result values.
- Include every teammate's specific contribution and the required AI-use disclosure.
- Keep the finished recording between 2 and 3 minutes.
