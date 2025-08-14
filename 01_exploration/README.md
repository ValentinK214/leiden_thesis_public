# Exploration Phase Code Overview

**The objective of the exploration phase was to identify the key drivers for rank instability. To ensure that the results were clearly interpretable,
we opted for a main-effects analysis instead of a factorial design.**

**Our results suggest that signal type and noise proportion change are the main drivers.**

Under the exploration phase, we conducted six experiments:
1. Signal type change
2. Noise proportion change
3. Covariate distribution change
4. Removing covariates
5. Sample size change
6. Adding correlated features

Each of the six experiments follows the following structure:
1. Global parameters
2. Helper functions
    1. Generate data and visualize
    2. Train-Test algorithms
    3. Rank correlation
    4. Sanity check using 1 reference and 1 non-reference dataset
3. Main simulation loop over B Monte Carlo iterations
4. Visualize
    1. Individual algorithm performance
    2. Relative difference between reference and non-reference level
    3. Rank stability
5. Binomial proportion test

We provided additional comments within each `.Rmd` file for the following functions and code sections:
1. Global parameters
2. `generate_data`
3. `generate_summary_table` -> Train-test algorithms
4. `get_rank_cor` -> Compute rank correlation
5. Main simulation loop


A quick explanation of a couple of quirks:
* For the **global parameters**, `NL` is the reference level and `DE` is the non-reference level. This is a historic artifact.
* I evaluated 9 normalized metrics. 6 are well known: MSE, NSE, RSE, RRMSE, NRMSE and MAPE. 3 I developed myself to include a null model: PR, Min-Max and NDRMSE.
* The `relative_difference` function is a historic artifact before we formalized the EPE lower bound. I kept it for the `01_signal_type_change.Rmd` code but removed it for all other experiments as it does not contributed to the final analysis.