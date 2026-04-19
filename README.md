AlgoTransit
Hybrid MMAS-ABC Algorithm for Sustainable Bus Route Optimization

An AI-driven system that optimizes BMTC bus driving cycles using Swarm Intelligence to reduce fuel consumption and CO₂ emissions across Bengaluru's urban transit network.

Live Dashboard →

The Problem
Urban buses in Bengaluru follow erratic driving cycles — aggressive acceleration, unnecessary idling, and traffic-induced stop-start patterns. This leads to excess fuel burn and avoidable CO₂ emissions. Existing scheduling systems don't account for eco-driving principles at the route level.
The Approach
AlgoTransit uses a two-stage hybrid swarm intelligence model:
Stage 1 — Max-Min Ant System (MMAS)
Models each bus trip as a graph traversal problem. Ants explore velocity sequences and pheromone trails converge on smoother, lower-noise driving profiles, filtering out erratic acceleration spikes caused by traffic.
Stage 2 — Artificial Bee Colony (ABC)
Refines the MMAS output using eco-driving logic: speed capping at optimal thresholds, idle time reduction, and regenerative coasting windows. Bees exploit and explore around the best candidate profiles to further minimize energy proxy (v²).
The result is an optimized driving cycle that a real bus can follow — reducing energy consumption without compromising route timing.

Results
Tested across 7 datasets (BMTC routes + simulated sets):
DatasetEnergy ReductionEmission ReductionCongestion ScoreBMTC Set 1~18–22%SignificantImprovedBMTC Set 2~15–19%SignificantImprovedSets 1–5ConsistentConsistentConsistent
Validation plots confirm convergence and statistical consistency across runs.

Repository Structure
AlgoTransit/
│
├── index.html          # Home — project overview
├── problem.html        # Problem statement and objectives  
├── findings.html       # Live simulation dashboard (main visualization)
├── outcomes.html       # Results and impact analysis
├── tools.html          # Tech stack and methodology
├── about.html          # Team and references
├── style.css           # Global styling
│
├── files/              # Python core scripts
│   ├── process_data.py # GPS JSON/CSV → velocity profile converter
│   ├── main.py         # Hybrid MMAS-ABC algorithm runner
│   └── *.csv           # Processed bus cycle datasets
│
├── bmtc1_*.png         # BMTC dataset 1 output graphs
├── bmtc2_*.png         # BMTC dataset 2 output graphs
└── set1_*.png          # Synthetic dataset output graphs (sets 1–5)
Each *_line.png, *_noline.png, *_congestion.png, *_emission.png, and *_validation.png represents a different analysis view for that dataset.

Tech Stack
Data Processing & Algorithm (Python)

pandas / numpy — data manipulation and matrix operations
geopy — converting GPS coordinates (lat/lon) to distances in metres
matplotlib — generating output graphs

Dashboard (Web)

HTML5 / CSS3 — responsive layout
JavaScript (ES6) / Chart.js — interactive velocity profile charts and simulation


How It Works — Step by Step
Raw GPS Logs (Lat/Lon + Timestamp)
        ↓
  process_data.py
  [Geodesic distance → Speed profile (m/s)]
        ↓
  main.py — Stage 1: MMAS
  [Graph construction → Pheromone convergence → Smooth baseline cycle]
        ↓
  main.py — Stage 2: ABC
  [Eco-driving refinement → Speed capping + Idle reduction]
        ↓
  Optimized Driving Cycle
  [Saved as CSV + Visualized as PNG + Rendered on Dashboard]

Running Locally
Prerequisites
bashpip install pandas numpy geopy matplotlib
Process raw GPS data
bashcd files/
python process_data.py
Run the optimization
bashpython main.py
Output graphs will be saved to the project root. Open index.html in a browser to view the dashboard.

Related Repository
The raw GPS data collection and preprocessing pipeline is maintained separately:
el-phase-2-data-and-dataprocessing

Context
This project was developed as part of Experiential Learning (EL) Phase 2 at RV College of Engineering, Bengaluru, under the Urban Development, Mobility & Smart Cities track (Project #49).

Authors
K. Karthik Pai — @k-karthik-pai
