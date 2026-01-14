# Fast Estimation of Local Marginal Prices (LMP) — Final Year Project

**Dates:** Sept 2025 – May 2026 (in progress)  
**Type:** Final Year Project (Team / Academic)  
**Status:** Ongoing


## 1) Overview
This project develops a **fast estimation workflow** to predict how **Local Marginal Prices (LMPs)** change under system variations, reducing the need to rerun a full optimization-based computation for every “what-if” scenario. The goal is to enable faster screening, sensitivity analysis, and scenario exploration while maintaining acceptable accuracy.


## 2) Motivation (Why this matters)
LMP studies are often repeated across many scenarios, such as:
- load changes over time,
- generator availability/capacity/cost changes,
- network constraint changes (limits, congestion),
- contingencies and operating point shifts.

Running the full reference computation repeatedly can become slow when the scenario count is large. A fast estimator helps:
- speed up exploration and decision-making,
- prioritize “important” cases for full reruns,
- support large-scale sensitivity studies.


## 3) Objective
**Primary objective:**  
Estimate **ΔLMP** (change in LMPs) relative to a baseline operating point with high speed and reasonable accuracy.

**Secondary objectives:**
- validate across multiple operating points (not one static case),
- quantify the accuracy–speed tradeoff,
- build a reproducible evaluation pipeline (inputs → outputs → metrics → plots).


## 4) Scope (Public vs Private)
**Included publicly:**
- the workflow, evaluation strategy, and non-sensitive figures,
- high-level description of the estimation approach and benchmarking.

**Kept private (to protect work):**
- implementation details and code,
- full datasets / scenario generators,
- sensitive experiment configurations.

Detailed technical material and code can be shared upon request when appropriate.


## 5) High-Level Methodology
### A) Baseline and reference (“ground truth”)
1. Define a baseline network state and operating point.
2. Compute reference LMPs using an optimization-based method (reference solution).
3. Use this reference as the benchmark standard.

### B) Scenario generation
Create structured variations around the baseline, such as:
- load perturbations (bus/zone-level),
- generator parameter changes (limits/cost/availability),
- network constraint variations (line limits, congestion patterns),
- operating point sweeps.

### C) Fast estimation approach
Develop an estimator that maps:
**system modification → predicted ΔLMP**

Design focus:
- fast runtime per scenario,
- stable outputs under varying operating conditions,
- consistent behavior across different operating points.

### D) Benchmarking
For each scenario:
- compute estimated LMPs,
- compute reference LMPs,
- quantify error metrics and runtime improvements.


## 6) Time-Series Sampling Strategy (2-week + 1-week)
To avoid evaluating the estimator on only a single snapshot, experiments are performed on **time-series operating points**.

### Sampling Design
- A **2-week window** is used to capture realistic variability in operating conditions.
- A **1-week subset** is used for faster iteration during development (tuning, debugging, rapid testing).
- The remaining time in the 2-week window acts as **validation / holdout**, to check that performance generalizes beyond the development subset.

### Why this is important
This structure helps ensure the estimator is tested across:
- different demand levels and daily patterns,
- changing system states that affect congestion and pricing,
- multiple operating points rather than one “easy” case.

### Experiment Loop
- **Development loop:** iterate quickly on the **1-week subset** (short cycles, frequent changes).
- **Validation loop:** periodically evaluate on the full **2-week window** to confirm generalization and avoid overfitting to one segment.


## 7) Evaluation Framework
### Accuracy metrics
- **MAE** (mean absolute error) across buses
- **Max error** (worst-case bus)
- Error distribution (percentiles / histogram)
- Scenario-wise breakdown (error by scenario type)

### Runtime metrics
- Time per scenario (estimator vs reference)
- Speedup factor: **reference runtime / estimator runtime**
- Total runtime for N scenarios

### Robustness checks
- performance under different operating points,
- behavior under congested vs non-congested conditions,
- sensitivity to magnitude of perturbations.


## 8) Current Status (In progress)
- Baseline + scenario evaluation pipeline established.
- Estimation workflow implemented and being refined iteratively.
- Benchmarking plots and summary tables being expanded as scenario coverage grows.


## 9) Deliverables
- Fast estimation workflow (scenario → estimated LMP → metrics)
- Reproducible benchmarking pipeline
- Result package (plots + summary tables)
- Final report / thesis (upon completion)


## 10) Tools
- **Python** (experiments, benchmarking, plots, workflow automation)
- **MATLAB** (modeling/validation tasks as needed)
- **Excel**  (comparison and experiment results)


## 11) Media (Figures / Plots)



## 12) Notes
This page provides a public-safe summary only. Detailed implementation and sensitive material may be kept private and shared upon request when appropriate.

