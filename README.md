# SFINet v2
## Synthetic Failure Injection Framework for Robustness Analysis in Multi-Robot Communication Networks

SFINet v2 is a lightweight, Python-native research framework for analyzing communication robustness, failure propagation, anomaly detection, and adaptive recovery in multi-robot communication systems.

The framework simulates realistic communication failures inside distributed robot networks and studies how failures propagate through different network topologies under dynamic conditions.

This project was developed as a research-oriented benchmark framework suitable for:
- IEEE student conferences
- Scopus-indexed conference submissions
- Robotics communication research
- Network robustness analysis
- Synthetic benchmarking studies

---

# Research Motivation

Modern multi-robot communication systems are vulnerable to:

- Packet loss
- Network congestion
- Malicious routing behavior
- Delay propagation
- Communication noise
- Bandwidth collapse
- Intermittent node failures

Most existing student research focuses heavily on prediction accuracy while ignoring communication robustness and failure propagation behavior.

SFINet focuses on:
- Reliability
- Failure cascade modeling
- Trust-aware communication
- Robustness evaluation
- Adaptive recovery mechanisms

Unlike NS-3 or OMNET++, SFINet is fully Python-based and designed for accessibility, reproducibility, and research experimentation.

---

# Key Features

## Core Framework Features

- Synthetic multi-robot communication simulation
- Failure injection engine with 8 failure types
- Sparse mesh, star, and hybrid topology analysis
- Trust score evolution modeling
- Failure cascade propagation
- Isolation Forest anomaly detection
- Proactive cascade prediction
- Adaptive recovery mechanisms
- Publication-grade synthetic dataset generation
- Fully reproducible Python implementation

---

# Novel Contributions

SFINet v2 introduces four major research contributions:

## 1. Trust Score Evolution
Robot communication trust evolves dynamically under failures and adversarial behavior.

Trust update equation:

T_i(t+1) = αT_i(t) + (1−α)R_i(t)

Where:
- α = decay factor
- R_i(t) = successful delivery ratio

---

## 2. Failure Cascade Modeling

SFINet models communication degradation propagation across graph topologies using graph diffusion.

Failures spread through neighboring nodes based on:
- topology structure
- edge connectivity
- failure severity

---

## 3. Proactive Cascade Prediction

SFINet predicts cascade failures 2–3 events before major communication collapse occurs.

Prediction uses:
- delta_PDR
- delta_CSI
- delta_Trust
- delta_Delay
- rolling statistics

---

## 4. Multi-Topology Comparative Analysis

The framework compares:
- Star topology
- Sparse mesh topology
- Hybrid topology

Metrics compared:
- Packet Delivery Ratio (PDR)
- Failure Cascade Impact (FCI)
- Throughput degradation
- Latency increase

---

# System Architecture

## Phase 1 — Sparse Network Creation
- Multi-robot communication graph generation
- Sparse k-regular graph topology
- NetworkX-based topology modeling

## Phase 2 — Synthetic Dataset Generation
Generated communication events include:
- source node
- destination node
- packet delay
- throughput
- trust score
- packet loss
- routing behavior

## Phase 3 — Failure Injection Engine
Eight synthetic communication failures are injected:

1. Packet Drop
2. Artificial Delay
3. Bandwidth Collapse
4. Malicious Node
5. Communication Noise
6. Intermittent Failure
7. Fake Routing
8. Congestion

## Phase 4 — Robustness Monitoring
Continuous monitoring of:
- PDR
- CSI
- throughput
- latency
- trust evolution
- cascade impact

## Phase 5 — Anomaly Detection
Isolation Forest detects abnormal communication behavior.

## Phase 6 — Proactive Cascade Prediction
Predicts future cascades before severe degradation occurs.

## Phase 7 — Recovery Mechanisms
Three adaptive recovery mechanisms:
- Dynamic rerouting
- Trust-based isolation
- Channel switching

## Phase 8 — Multi-Topology Experiment
Comparative evaluation across multiple topologies.

## Phase 9 — Final Evaluation
Publication-grade metrics and analysis generation.

---

# Mathematical Foundations

## Packet Delivery Ratio (PDR)

PDR(t) = (Packets Received / Packets Sent) × 100

Interpretation:
- High PDR → healthy communication
- Low PDR → severe degradation

---

## Communication Stability Index (CSI)

CSI(t) = 1 − [σ_delay(t) / μ_delay(t)]

CSI interpretation:
- CSI > 0.70 → Stable
- 0.40–0.70 → Degraded
- < 0.40 → Unstable

---

## Failure Cascade Impact (FCI)

FCI = Σ [ΔPDR × node_centrality]

Interpretation:
- FCI = 0 → isolated failure
- FCI > 5 → systemic cascade propagation

---

# Technologies Used

- Python 3.10
- NumPy
- Pandas
- NetworkX
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

---

# Dataset Information

## SFINet v1
- Total events: 996
- Failure events: 296
- Topology: Full mesh

## SFINet v2
- Total events: 10,000
- Normal events: 7,000
- Failure events: 3,000
- Cascade events: 2,999
- Robots: 12
- Edges: 24
- Topology: Sparse mesh

---

# SFINet v2 Results Summary

## Robustness Metrics

| Metric | Normal | Failure |
|---|---|---|
| PDR | 98.87% | 40.57% |
| CSI | 0.1375 | 0.1137 |
| Avg Delay | 16.79 ms | 58.54 ms |
| Throughput | 480.22 kbps | 296.13 kbps |
| FCI Score | 0 | 76.9502 |

---

# Isolation Forest Results

| Metric | Value |
|---|---|
| Precision | 0.8020 |
| Recall | 0.9453 |
| ROC-AUC | 0.9227 |
| True Positives | 2836 |
| False Positives | 700 |
| False Negatives | 164 |

---

# Proactive Cascade Prediction Results

| Metric | Value |
|---|---|
| Prediction Horizon | 3 events ahead |
| Early Correct Flags | 279 |
| ROC-AUC | 0.6404 |

---

# Recovery Strategy Comparison

| Strategy | PDR (%) | Avg Delay (ms) |
|---|---|---|
| Baseline | 98.87 | 16.79 |
| Pre-Recovery Failure | 40.10 | 58.54 |
| Dynamic Rerouting | 93.90 | 48.77 |
| Trust Isolation | 75.27 | 40.30 |
| Channel Switching | 99.83 | 28.28 |

Best Strategy:
- Channel Switching

---

# Multi-Topology Experiment

| Topology | Density | FCI Score |
|---|---|---|
| Star | 0.1667 | 34.27 |
| Sparse Mesh | 0.3636 | 77.22 |
| Hybrid | 0.3333 | 71.35 |

Key Finding:
Sparse mesh topology produced the highest cascade impact because failures propagate more effectively through balanced node connectivity.

---

# Project Structure

```bash
SFINet/
│
├── sfinet-phase-1.ipynb
├── sfinet-phase-2.ipynb
├── SFINet_Research_Report.docx
├── results.txt
├── dataset/
│   ├── SFINet_Dataset.csv
│   └── SFINet_v2_Dataset.csv
│
├── visualizations/
│   ├── topology_graphs/
│   ├── cascade_analysis/
│   ├── performance_metrics/
│   └── anomaly_detection/
│
└── README.md
```

---

# Installation

```bash
git clone https://github.com/yourusername/SFINet.git

cd SFINet
```

Install dependencies:

```bash
pip install numpy pandas networkx matplotlib scikit-learn seaborn
```

---

# Running the Project

## Run Phase 1
```bash
jupyter notebook sfinet-phase-1.ipynb
```

## Run Phase 2
```bash
jupyter notebook sfinet-phase-2.ipynb
```

---

# Research Advantages

## Why This Project Is Strong

- Lightweight and reproducible
- Fully Python-native
- No GPU required
- Research-focused instead of accuracy-only
- Strong engineering contribution
- Realistic communication degradation analysis
- Suitable for IEEE student publications
- Easy reproducibility for future researchers

---

# Limitations

Current limitations include:
- Synthetic-only environment
- No real robotic hardware integration
- No real-time wireless interference modeling
- CSI still unstable under baseline synthetic conditions

---

# Future Work

Potential future extensions:
- Swarm robotics
- Drone communication networks
- Federated robot communication
- Reinforcement learning routing
- Cyberattack simulation
- Edge AI optimization
- Real robotic deployment

---

# Research Impact

SFINet provides:
- A reusable benchmark framework
- Communication robustness evaluation
- Failure cascade analysis
- Trust-aware recovery experimentation
- Synthetic reproducible datasets

The framework is designed to help students and researchers perform communication reliability research without requiring heavy network engineering tools.

---


# Author

Developed for:
- Multi-Robot Communication Research
- Network Robustness Analysis
- IEEE/Scopus Research Publication

---

# License

This project is intended for:
- Academic research
- Educational use
- Experimental benchmarking

