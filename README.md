# Metaheuristic Optimization Benchmark: DE vs. SA

A rigorous statistical comparative analysis between population-based and trajectory-based metaheuristic optimization algorithms. This project evaluates **Differential Evolution (DE)** and **Simulated Annealing (SA)** across extensive hyper-parameter sensitivity matrices on classic non-linear benchmark functions.

---

## 🚀 Key Features and Enhancements
*   **Stochastic Bias Elimination (N = 30 Runs):** Decoupled static random seeds (`seed=run`) across 30 independentized execution steps per configuration to extract medians, variances, and fault-tolerant true success metrics.
*   **Unified Computational Workload Baseline:** Equalized total evaluation budgets strictly at **5,000 Objective Function Evaluations** (100 pop\_size × 50 generations for DE vs. 50 cycles × ≈ 100 internal steps for SA) to guarantee a scientifically fair benchmark comparison.
*   **Advanced Convergence Visualization:** Custom-built convergence charts implementing automated multi-dimensional NumPy processing to render **Min-Max Envelopes (Variance Bands)** alongside statistical mean descent trajectories on log-scale axes.

---

## 🗺️ Benchmark Environments

### 1. Ackley Function (Highly Multi-Modal)
*   **Search Bounds:** \([-32.768, 32.768]\) for both dimensions.
*   **Topography Traps:** Thousands of symmetric local minima.
*   **Optimization Challenge:** Extreme global exploration capabilities required to evade premature stagnation outside the primary basin.

### 2. Rosenbrock Function (Unimodal / Curved Valley)
*   **Search Bounds:** \([-2.0, 2.0]\) for both dimensions.
*   **Topography Traps:** A very long, narrow, and sharply parabolic "banana" valley.
*   **Optimization Challenge:** High-precision local exploitation and coordinate correlation management to advance continuously down a nearly flat valley floor.

---

## 🛠️ Hyper-parameter Sensitivity Grid

The optimization suite tests the algorithms' resilience across a dense grid of configurations:
*   **Differential Evolution Grid:** Analyzes spatial intelligence across population scales of `population_sizes = [5, 10, 25, 50, 100]`.
*   **Simulated Annealing Grid:** Examines thermodynamic phase transitions across initial energy thresholds of `temperature_variants = [5, 10, 25, 50, 100]` leveraging SciPy's hybrid `dual_annealing` solver equipped with an internal L-BFGS-B local optimizer.

---

## 📈 Executive Summary of Findings

| Benchmark | Winning Paradigm | Primary Architectural Explanatory Factor |
| :--- | :--- | :--- |
| **Ackley Function** | **Differential Evolution** | Parallelized genetic memory and vector mutations seamlessly eliminate local traps. |
| **Rosenbrock Function** | **Differential Evolution** *(Efficiency)*<br>**Simulated Annealing** *(Final Precision)* | DE maps out the banana valley 4x faster due to cloud dispersion. SA achieves a deep final numerical dive (10⁻¹¹) via quasi-Newtonian local optimization. |

---

## 💻 Prerequisites & Setup

This repository is built and optimized for modern environments, demonstrating lightning-fast, hardware-accelerated matrix processing on Apple Silicon (tested on **MacBook Air M2** with total simulation execution steps rendering in sub-5 seconds).

### Installation
The project utilizes the ultra-fast, Rust-backed `uv` package manager. You can spin up the full optimization environment directly inside your Jupyter Notebook using the following commands:

```bash
!uv pip install matplotlib
!uv pip install scipy
!uv pip install numpy
```

### Execution
Open the primary analysis notebook via Jupyter or your preferred IDE (e.g., PyCharm Professional):

```bash
jupyter notebook msi-2-heuristics-analysis.ipynb
```

---

## 📐 Project Structure
```text
├── README.md                           # Project description and engineering insights
└── heuristics-analysis.ipynb           # Main Jupyter Notebook containing the full experiment suite
```

---

## 📜 License
This optimization suite is compiled as an academic research prototype. Feel free to clone, scale the dimension boundaries, or plug in your own objective functions to further analyze metaheuristic sensitivity boundaries.
