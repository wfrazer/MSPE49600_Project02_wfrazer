# MSPE49600-Project02-wfrazer

**Name:** YOUR FULL NAME
**Course:** MSPE 49600 – Data Analytics for Motorsports, Purdue University, Fall 2026

## Project 2: Predictive Modeling and Engineering Optimization

### Overview
A setup study at the IMS road course tested rear-wing angle (5–13°) and rear ride height (35–45 mm), with 27 setups run for 5 laps each. The laps were averaged to one row per setup, and quadratic response surfaces were fitted for mean Sector 3 time and mean top speed:

ŷ = b₀ + b₁x₁ + b₂x₂ + b₃x₁² + b₄x₂² + b₅x₁x₂

The models were fitted with the Moore-Penrose pseudoinverse and validated on 7 unseen setups:
- Sector 3 time: RMSE ≈ 0.026 s, R² ≈ 0.998
- Top speed: RMSE ≈ 0.16 kph, R² ≈ 0.986

### Optimization problem
Minimize predicted Sector 3 time, subject to:
- predicted top speed ≥ 284.0 kph
- 5° ≤ rear-wing angle ≤ 13°, 35 mm ≤ rear ride height ≤ 45 mm

The problem was solved without the top-speed constraint (L-BFGS-B) and with it (SLSQP). Both were verified with a 101 × 101 grid search and checked from multiple starting points. A quadratic penalty-function formulation was also tested.

### Final recommended candidate
| Rear-wing angle | Rear ride height | Predicted Sector 3 time | Predicted top speed |
|---|---|---|---|
| ≈ 9.54° | ≈ 38.3 mm | ≈ 31.269 s | 284.0 kph (constraint active) |

This is a model-based recommendation. It should be verified with back-to-back track runs against a baseline setup and/or higher-fidelity simulation before being used.

### Files
- `wfrazer_pr02_notebook.ipynb`, `.pdf`, `.py`: analysis notebook
- `wfrazer_pr02_grouped.csv`, `_validation.csv`, `_optimization_runs.csv`, `_penalty.csv`, `_recommendation.csv`: results
- `wfrazer_pr02_validation.png`, `_unconstrained.png`, `_constrained.png`: figures
