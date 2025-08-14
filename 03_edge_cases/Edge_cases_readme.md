# Edge Cases Phase Code Overview

**The objective of the edge cases phase was to identify scenarios under which our proposed framework fails.**

**As far as we were able to test, our framework fails when local patterns of the observable data change, while the global patten (i.e. deviation from linearity) remains constant.**

For this experiment we simulated cyclical data using a sin function with increasing frequency but constant amplitude.

The edge cases analysis mirrors the signal type change experiment from the exploration phase:
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
