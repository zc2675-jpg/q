# Direct Potential-q Learning in Entropy-Regularized Stochastic Differential Games

Simulation code accompanying the paper *"Direct Potential-q Learning in Entropy-Regularized Stochastic Differential Games"* (Zihan Chen, Xin Zhang). This repository contains the single Jupyter notebook that generates every simulated dataset, table, and figure reported in the paper (Section 3.5 and Appendix A).

## Contents

- `potentialq_dynamic_lq_experiment.ipynb` — the complete, self-contained simulation notebook. No external data files are used; every experiment is generated from the models and random seeds documented in the notebook itself.

## Requirements

- Python ≥ 3.10
- `numpy`, `scipy`, `matplotlib`

No GPU is required. Install with:

```bash
pip install numpy scipy matplotlib jupyter
