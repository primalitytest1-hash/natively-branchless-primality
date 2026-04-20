# Artifact Evaluation (Theory): High-Efficiency Natively Branchless Primality Testing against Structural Leakage

This repository contains the mathematical and theoretical artifact for our paper. It provides a comprehensive **SageMath notebook** designed to empirically verify the theorems, statistical simulations, and optimization algorithms underlying our natively branchless primality tests.

> **Note:** The C-language implementations, OpenSSL benchmarks, and side-channel leakage assessments (dudect) are hosted in a separate repository. This repository is dedicated strictly to theoretical verification.

## 1. Environment & Prerequisites

To execute the notebook successfully, please ensure your environment meets the following requirements:
* **SageMath Version:** 10.7
* **Required Tools:** Jupyter Notebook (bundled with SageMath) or the SageMath Interactive Shell.

## 2. Notebook Contents

The core of this artifact is the `PrimalityTest-Vtest.ipynb` notebook, which is divided into three primary sections corresponding to the theoretical claims in our paper:

### A. Theorem 4.4 Verification
* **Objective:** Verifies the exact cardinality formula for the V-set ($|TSL(D,n)|$) and the total cryptographic sample space ($|\mathcal{Z}(D,n)|$).
* **Method:** The script calculates the theoretical counts using our derived mathematical formulas and compares them against empirical counts obtained by exhaustively evaluating composite numbers. It asserts that the theoretical and empirical values match perfectly, thereby validating the soundness bounds.

### B. Empirical Distribution of Parameter $D$ Search Depth
* **Objective:** Evaluates the efficiency and completeness of the fixed-iteration search for parameter $D$ (where $(\frac{-D}{n}) = -1$).
* **Method:** Simulates high-speed prime generation to track the search depth required to find a valid quadratic non-residue $D$ across a massive dataset of prime candidates. It outputs the exact statistical distribution (raw counts and percentages) to validate our fixed-iteration threshold.

### C. Optimal Parameter Selection via Integer Programming
* **Objective:** Provides a direct implementation of the Bivariate Integer Linear Programming (ILP) solvers (**Algorithms 10 and 11**).
* **Method:** Calculates the optimal number of computationally intensive iterations ($I_{CSL}$ or $I_{SS}$) and trace-based iterations ($I_{CV}$) required to minimize the total arithmetic cost while strictly satisfying a target security level (e.g., $\kappa = 128, 192, 256$).

## 3. Execution Instructions

To run the verification scripts, execute the following commands in your terminal:

1. Clone this repository and navigate to the directory:

    git clone https://github.com/primalitytest1-hash/natively-branchless-primality.git
    cd natively-branchless-primality

2. Launch the Jupyter Notebook via SageMath:

    sage -n jupyter PrimalityTest-Vtest.ipynb

3. Once the notebook opens in your web browser, you can run the cells sequentially (using Shift + Enter) to observe the mathematical proofs, parameter distributions, and ILP solver outputs in real-time.