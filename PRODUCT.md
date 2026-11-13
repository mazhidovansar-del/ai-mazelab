# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Students learning introductory artificial intelligence who need to see how AI search and decision methods behave on a shared maze problem.

## Product Purpose

MazeLab is an interactive educational application for exploring AI fundamentals. Students choose a method, adjust inputs, and observe how the agent searches or reasons about corridor risk. Success means students can compare the methods' behavior and interpret the displayed route and metrics.

## Positioning

MazeLab makes algorithm behavior visible on a common, editable maze: students can compare search methods and inspect uncertainty-aware Bayesian and MDP decisions in the same environment.

## Operating Context

The project is associated with the AI Fundamentals course AIF1303. It runs in a modern web browser and can be opened directly or served as a static folder; no package installation or build step is required.

## Capabilities and Constraints

- The interface language is English.
- Students can edit the maze, change selected algorithm settings, animate or step through search, and inspect route cost, move count, explored cells, and search time.
- Implemented methods include A*, breadth-first search, uniform-cost search, greedy best-first search, a zone-coloring CSP, Bayesian corridor-risk inference, and a two-state MDP that compares proceeding with detouring.
- Bayesian and MDP models are simplified teaching examples, not real-world sensor or navigation systems.
- The search and decision algorithms run in the browser. No generative AI model is embedded in the runtime application.
- The project documents selected course topics and does not claim to implement the entire syllabus.

## Evidence on Hand

- `index.html`, `styles.css`, and `app.js` contain the runnable application.
- `README.md` documents setup, interactions, algorithm interpretations, course alignment, and manual checks.
- `TECHNICAL_REPORT.md`, `presentation/`, and `DEMO_SCRIPT.md` contain supporting project materials.

## Product Principles

- Make AI behavior observable through the maze, search steps, and decision outcomes.
- Let students compare methods on the same problem and inspect meaningful results.
- Keep inputs interactive so students can explore how parameter changes affect outcomes.
- Explain the limits of simplified models and describe only implemented course topics.
