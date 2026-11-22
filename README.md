# CSAI4014: Algorithms for Intelligent Systems and Robotics

**Laboratory Work, Experiments 1 to 8**

| | |
|---|---|
| **Student** | Priyal Sharma |
| **SAP ID** | 500122041 |
| **Roll No.** | `<your roll number>` |
| **Programme** | B.Tech CSE (AI & ML), Semester VII, Autumn 2026–27 |
| **Batch** | `<your batch>` |
| **Course teacher** | `<teacher name>`, School of Computer Science, UPES Dehradun |
| **Lab partner(s)** | `<name and SAP ID, or "none">` |

This repository holds the code, results and figures for the laboratory experiments of the course, written to accompany the lab report. Every experiment is self-contained in its own folder and can be re-run independently.

---

## Table of Contents
1. [Repository structure](#repository-structure)
2. [Experiments at a glance](#experiments-at-a-glance)
3. [Getting started](#getting-started)
4. [Reproducing the results](#reproducing-the-results)
5. [Experiments 7 and 8 (simulation)](#experiments-7-and-8-simulation)
6. [Reproducibility notes](#reproducibility-notes)
7. [Sources and references](#sources-and-references)
8. [AI tools disclosure](#ai-tools-disclosure)

---

## Repository structure

```
.
├── README.md
├── .gitignore
├── exp01-signals/       # notebook, script, results.json, figs/
├── exp02-queens/
├── exp03-search/
├── exp04-hillclimb/
├── exp05-rl/
├── exp06-neural/
├── exp07-webots/        # run + analysis scripts, figs/, NOTES.md
└── exp08-xembody/       # results/, exercises/, figs/, NOTES.md
```

Experiments 1 to 6 follow the same layout: `expNN.ipynb` (executed notebook), `expNN.py` (the same code as a script, cells marked `# %%`), `results.json` (numbers quoted in the report) and `figs/` (figures used in the report).

## Experiments at a glance

| # | Folder | Topic | Key idea |
|---|---|---|---|
| 1 | `exp01-signals/` | Time and frequency domain, the pendulum | Sampling, FFT spectrum, aliasing, damping, phase and period |
| 2 | `exp02-queens/` | Eight queens | Backtracking vs generate-and-test, runtime comparison |
| 3 | `exp03-search/` | BFS and DFS on a grid maze | Uninformed search, path quality, frontier growth |
| 4 | `exp04-hillclimb/` | Hill climbing and random restarts | Local optima and how restarts escape them |
| 5 | `exp05-rl/` | Tabular Q-learning | Learning curves and the learned policy |
| 6 | `exp06-neural/` | NumPy neural network for XOR | Forward/backward pass, loss curve, decision boundary |
| 7 | `exp07-webots/` | Webots swarm and lidar navigation | Reactive control, path length, stuck time, coverage |
| 8 | `exp08-xembody/` | Cross-embodiment transfer (PyBullet) | Joint-space vs task-space transfer across robots |

## Getting started

**Requirements**
- Python 3.11 or newer
- NumPy, SciPy, Matplotlib, Jupyter (Experiments 1 to 6)
- PyBullet, scikit-learn, Pillow (Experiment 8)
- Webots R2025a (Experiment 7 only)

**Setup**
```bash
git clone <your-repo-url>
cd <repo-folder>

python -m venv .venv
source .venv/bin/activate            # Windows: .venv\Scripts\activate
pip install numpy scipy matplotlib jupyter
```

## Reproducing the results

### Experiments 1 to 6
Run any experiment as a script or open its notebook:

```bash
# as a script
python exp01-signals/exp01.py

# or as a notebook
jupyter notebook exp01-signals/exp01.ipynb
```

Each script regenerates `results.json` and the figures in its `figs/` folder. Repeat for `exp02-queens/exp02.py` through `exp06-neural/exp06.py`.

### Version details
Fill in the versions you actually used:

| Package | Version |
|---|---|
| Python | `<x.y.z>` |
| NumPy | `<x.y.z>` |
| SciPy | `<x.y.z>` |
| Matplotlib | `<x.y.z>` |

## Experiments 7 and 8 (simulation)

### Experiment 7: Webots
- `run_all.sh` launches the swarm and Pioneer runs with the parameter settings used in the report.
- `analyse_runs.py` computes the metrics from the logged poses:
  - **Path length**: sum of distances between consecutive logged poses
  - **Mean speed**: path length divided by duration
  - **Stuck %**: share of samples slower than 1 cm/s
  - **Coverage**: share of grid cells visited
- `figs/` contains the screenshots and plots used in the report. See `NOTES.md` for the run conditions.

```bash
bash exp07-webots/run_all.sh
python exp07-webots/analyse_runs.py
```

### Experiment 8: Cross-embodiment transfer
- `results/` holds the CSVs and plots for the default runs (setup check, embodiment exploration, joint-space transfer, task-space transfer, learn-once-deploy-many, multi-embodiment).
- `exercises/` holds the exercise runs (E2: fewer demonstrations, E4: smallest robot scale that still succeeds). `run_exercises.sh` runs them and `plot_exercises.py` produces the summary figure.
- See `NOTES.md` for the exact commands and environment.

## Reproducibility notes
- Random seeds are fixed in every experiment, so re-running gives the same numbers.
- Figures are saved to each experiment's `figs/` folder; numeric outputs go to `results.json` or CSV.
- `.gitignore` excludes virtual environments, notebook checkpoints and cache folders.

## Sources and references
- Course Laboratory Manual (Experiments 1 to 6)
- Experiment 7 and 8 project guides provided for the course
- Textbooks and papers are listed in the References section of the lab report

## AI tools disclosure
`<Describe honestly how you used AI tools, for example: "Claude (Anthropic) was used to help write this README and to clarify concepts. The experiments, code and results are my own.">`

---

*Submitted by Priyal Sharma (SAP ID 500122041), School of Computer Science, UPES Dehradun.*
