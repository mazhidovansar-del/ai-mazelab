# AI Fundamentals (AIF1303) — syllabus topic map

Source: supplied 2026–2027 AI Fundamentals syllabus PDF. The syllabus schedules the following topics across ten weeks.

| Week | Topic in syllabus | Example activity in syllabus |
|---:|---|---|
| 1 | Introduction to AI: agents and environments | Analyze agents/environments and formulate AI problems |
| 2 | Uninformed search, A* and heuristics | Implement/compare DFS, BFS, UCS, A*; analyze heuristics |
| 3 | Local search and constraint satisfaction | Hill climbing, random restart, simulated annealing |
| 4 | Adversarial search and game trees | Minimax, alpha-beta pruning, expectimax |
| 5 | Markov decision processes and reinforcement learning | Value iteration and basic Q-learning in grid-worlds |
| 6 | Probability and Bayesian networks | Conditional probability, Bayes' rule, inference |
| 7 | Hidden Markov models and sequential inference | Forward inference and filtering in sensor tracking |
| 8 | Rational decisions and classical machine learning | Decision making, Naive Bayes, linear models, evaluation |
| 9 | Perceptrons and neural networks | Implement/evaluate a perceptron or guided neural-network model |
| 10 | LLMs, generative AI, AI safety and final project | Integrate concepts and present/defend an AI solution |

## Selected project scope

MazeLab implements selected material from weeks 1–3, 5 and 6: agent/environment modeling; BFS/UCS/A*/Greedy search; a zone-coloring CSP solved with backtracking, MRV and forward checking; a two-state Clear/Blocked MDP compared with value iteration; and Bayesian updating of corridor-blockage probability from a sensor report. The MDP is a small discounted-cost teaching model, not full reinforcement learning. Week 3's hill climbing, random restart and simulated annealing are not implemented; neither are game-tree search (week 4), Q-learning (week 5), HMMs (week 7), classical ML (week 8), neural networks (week 9), or generative AI/safety (week 10).

This distinction keeps the project aligned with the course while avoiding an inaccurate claim that every syllabus topic is present in the application.
