# 6CCSAPRA — Principles of Robot Autonomy (AY 25/26, Sem 2)

This folder contains compact, exam-focused LaTeX revision notes built from the module slides and past/exam questions.

## Module Leaders

- **Dr. Khen Elimelech** — khen.elimelech@kcl.ac.uk (Office hours: Thu 1-2pm, BH5.09(S))
- **Dr. Matteo Leonetti** — matteo.leonetti@kcl.ac.uk (Office hours: Wed 1:30-2:30pm, BH5.10(S))

## Build

- Compile `main.tex` with your preferred LaTeX toolchain (e.g. `latexmk -pdf main.tex`).

## Notes structure

- `main.tex`: assembles the document.
- `preamble.tex`: shared packages + note environments.
- `topics/00-module-overview.tex`: module overview.
- Add `topics/week-XX-<topic>.tex` when slides/questions are provided.

## Key Topics (from module description)

1. **Robot Kinematics** — fundamental language for modelling robot movement
2. **Motion Planning** — algorithms for robots to move to desired positions in challenging environments
3. **Object Grasping** — handling object manipulation
4. **Task and Motion Planning (TAMP)** — complex, interactive task execution
5. **Localization and Mapping** — understanding robot position and environment
6. **Handling Uncertainty** — probabilistic methods
7. **Machine Learning for Robotics** — leveraging ML in autonomous systems
