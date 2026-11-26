# 🏭 Constraint Programming Heuristics for the Hybrid Flow Shop with Total Tardiness Minimization

This repository provides the benchmark instances and computational results associated with the research paper **"Constraint Programming heuristics for the hybrid flow shop with total tardiness minimization"**.

---

## 🧠 Problem Overview

The **Hybrid Flow Shop Scheduling Problem (HFSP)** with identical parallel machines and total tardiness minimization involves scheduling a set of jobs through a series of sequential production stages, where each stage consists of one or more identical parallel machines. All jobs follow the same processing sequence across stages, and the objective is to minimize the **total tardiness** ($\sum T_j$) relative to job due dates.

In the associated study, we evaluate:
1. A **Mixed-Integer Linear Programming (MILP)** baseline formulation.
2. A **Constraint Programming (CP)** formulation modeling each production stage as a **cumulative resource** whose capacity equals the number of identical parallel machines.
3. A **Capacity-Relaxation Decomposition with Warm Start (CRD-WS)** and its hybrid variant (**HCRD-WS**), which iteratively solve a sequence of subproblems with progressively tighter stage capacities—transferring lower bounds and incumbent solutions—before switching to the original model upon search stagnation.

---

## 📁 Repository Structure

### `Test_instances/`
Provides the complete set of **2,880 benchmark instances** evaluated in the study:
- Configurations scaling up to **100 jobs** and **10 production stages**.
- Varying machine layouts and due-date tightness factors (identified as the primary driver of instance difficulty).
- `README.md`: Description of instance formats, generation parameters, and directory organization.

### `Results/`
Contains the consolidated experimental outputs comparing MILP (CPLEX & Gurobi), standalone CP, CRD-WS, and HCRD-WS across all 2,880 instances:
- `Results_HFSP_Total_Tardiness.xlsx`: Detailed performance metrics (objective values, lower bounds, optimality gaps, proven optima, and runtimes).

---

## 📊 Key Highlights & Findings

- **Cumulative CP vs. MILP:** Across 2,880 benchmark instances, standalone CP finds feasible solutions for **100%** of the instances and proves optimality for **495**, whereas MILP (CPLEX/Gurobi) fails to find feasible solutions in ~30% of the cases (including all largest instances) and proves optimality for only **3**.
- **Superiority of HCRD-WS:** The hybrid capacity-relaxation decomposition achieves the highest number of proven optima, best primal solutions, and strongest lower bounds, significantly enhancing search robustness on large-scale instances.
- **Reproducibility:** Full access to the 2,880 benchmark datasets and detailed experimental results for benchmarking future algorithms.

---

## 👥 Authors

- **Francisco Yuraszeck** *(Corresponding Author)* — Department of Engineering Sciences, Universidad Andrés Bello, Viña del Mar, Chile (`francisco.yuraszeck@unab.cl`)
- **Daniel Alejandro Rossit** — Department of Engineering, Universidad Nacional del Sur – INMABB CONICET, Bahía Blanca, Argentina (`daniel.rossit@uns.edu.ar`)
- **Bruno de Athayde Prata** — Department of Industrial Engineering / ENGINE - Group in Industrial Engineering and Computational Intelligence, Federal University of Ceará, Ceará, Brazil (`baprata@ufc.br`)
- **Débora Preti Ronconi** — Department of Production Engineering, University of São Paulo, São Paulo, Brazil (`dronconi@usp.br`)

---

## 📖 Citation

If you use the benchmark instances or computational results from this repository in your research, please cite:

```bibtex
@article{yuraszeck2026hfsp,
  title   = {Constraint Programming heuristics for the hybrid flow shop with total tardiness minimization},
  author  = {Yuraszeck, Francisco and Rossit, Daniel Alejandro and Prata, Bruno de Athayde and Ronconi, D{\'e}bora Preti},
  year    = {2026},
  note    = {Manuscript submitted for publication}
}
