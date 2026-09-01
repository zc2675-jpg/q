Direct Potential-q Learning in Entropy-Regularized Stochastic Differential Games
Simulation code accompanying the paper "Direct Potential-q Learning in Entropy-Regularized Stochastic Differential Games" (Zihan Chen, Xin Zhang). This repository contains the single Jupyter notebook that generates every simulated dataset, table, and figure reported in the paper (Section 3.5 and Appendix A).

Contents
potentialq_dynamic_lq_experiment.ipynb — the complete, self-contained simulation notebook. No external data files are used; every experiment is generated from the models and random seeds documented in the notebook itself.
Requirements
Python ≥ 3.10
numpy, scipy, matplotlib
No GPU is required. Install with:


pip install numpy scipy matplotlib jupyter
Running
Open the notebook and run all cells top to bottom, or execute headlessly:


jupyter nbconvert --to notebook --execute potentialq_dynamic_lq_experiment.ipynb --output executed.ipynb
All outputs (CSV/JSON result tables and PDF/PNG figures) are written to a notebook_output/ directory created alongside the notebook.

Runtime note. The notebook reruns the full multi-stream study described in the paper — 132 four-player LQ panel runs, 72 parameter-grid cells, 60 restart audits, 60 dependent-trajectory audits, 96 nonlinear-ball boundary starts, and the player-count scaling sweep — so a full end-to-end execution is computationally intensive and may take a considerable amount of time depending on hardware. Individual sections can be run independently once the shared setup cells (model definitions and feature maps) have been executed.

Notebook structure
Section (markdown header)	Produces
Context & Methods; Data-generating model and feature maps	Shared game/model definitions used by every experiment below
Simulation and martingale critic estimation; Analytic LQ benchmark and actor update	DPQSPI simulator and closed-form Riccati/Gibbs benchmark
Dynamic Nash-gap diagnostic and multi-critic baseline	Simultaneous soft Nash gap and the refitted four-critic baseline
Main traceable learning run	The single fully-traceable run reported at the start of Section 3.5
Multi-stream and parameter-stress engine	The 20-stream sampling study and the 9-cell (σ, off-diagonal coupling) parameter grid
Primitive rank, nonlocal contraction, nonlinear misspecification, and player scaling	Proposition 2 rank test, Theorem 11–12 LQ contraction certificates, the manufactured nonlinear diffusion, and the N ∈ {2,4,8,12} scaling study
Beyond the one-state manufactured design	The two-state non-manufactured nonlinear HJB benchmark (finite-difference oracle + learned sieves)
Finite-sample certificate from one dependent trajectory	Theorem 7 / Corollary 4 dependent-trajectory mixing certificate
Explicit primitive invariant ball for the nonlinear sieve	Theorem 9–10 implicit-Jacobian and residual-centered invariant-ball certificates
Results; Reproducibility checks; Takeaways	Summary tables and the reproducibility/coverage checks quoted in the paper
Mapping to paper figures and tables
Output file (notebook_output/)	Paper reference
fig_dynamic_lq_learning.{pdf,png}	Figure 1
fig_dynamic_lq_sampling_robustness.{pdf,png}	Figure 2
fig_dynamic_lq_parameter_stress.{pdf,png}	Figure 3
fig_dynamic_lq_audit_coverage.{pdf,png}	Figure 4
fig_dynamic_lq_contraction_baseline.{pdf,png}	Figure 5
fig_primitive_cohomology_global_contraction.{pdf,png}	Figure 6
fig_mixing_finite_sample_certificate.{pdf,png}	Figure 7
fig_nonlinear_primitive_invariant_ball.{pdf,png}	Figure 8
fig_three_front_validation.{pdf,png}	Figure 9
fig_nonlinear_and_scaling.{pdf,png}	Figure 10
dynamic_lq_summary.json, dynamic_lq_robustness_summary.json	Table 2 (primitive LQ contraction modulus)
nonlinear_primitive_invariant_ball_summary.json	Table 3 (invariant-ball certificate)
player_scaling_study.csv	Table 4 (player-count scaling)
primitive_cohomology_rank.csv	Proposition 2 rank-test residuals (Figure 6a)
mixing_finite_sample_certificate.csv, mom_finite_sample_certificate.csv	Theorem 6–7 finite-sample coefficient radii (Figure 7, Section 3.5 restart/mixing audits)
three_front_validation_summary.json, higher_order_validation_summary.json	Section 3.5 non-manufactured two-state benchmark
Reproducibility
Every stochastic experiment uses numpy.random.default_rng with an explicit integer seed fixed in the notebook source (base seeds and per-replicate offsets are visible at each simulation call site). Re-running the notebook without modification reproduces every number, table, and figure reported in the paper exactly.

Citation
If you use this code, please cite:

Z. Chen and X. Zhang, "Direct Potential-q Learning in Entropy-Regularized Stochastic Differential Games," [venue/year to be added upon publication].

License
See LICENSE.
