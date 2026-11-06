# Lower Bounds and Exact Search for Quantum Qubit Routing

*A theoretical and computational study of graph-based models, state-space search, and optimal SWAP sequences.*

## 1. Project Overview

Quantum qubit routing is an important problem in quantum computer architecture. Physical quantum processors have limited connectivity, meaning that not every pair of physical qubits can interact directly.

When two logical qubits need to interact but are not adjacent on the hardware architecture, SWAP operations may be required to rearrange their physical positions.

This project investigates a simplified mathematical formulation of qubit routing using graph theory, permutation groups, and combinatorial search.

The initial objective is to develop an exact search framework for determining the minimum number of SWAP operations required to transform an initial qubit configuration into a target configuration.

## 2. Research Question

The broader research question is:

**How informative are graph-based lower bounds for evaluating the optimality gap of heuristic quantum qubit-routing algorithms on small instances?**

The current implementation establishes the mathematical and computational foundations needed to investigate this question.

In particular, it focuses on constructing configuration state spaces and solving small routing instances optimally using Breadth-First Search (BFS).

## 3. Mathematical Model

The simplified routing problem is represented using three mathematical structures.

### 3.1 Hardware Graph

The quantum hardware topology is modeled as an undirected graph:

\[
G=(V,E)
\]

where:

- \(V\) represents physical qubit locations.
- \(E\) represents pairs of locations connected by an allowed SWAP operation.

### 3.2 Qubit Configurations

A qubit configuration is represented as a permutation:

\[
\pi \in S_n
\]

where \(S_n\) denotes the symmetric group of all permutations of \(n\) logical qubits.

Each configuration describes the placement of logical qubits across physical locations.

### 3.3 SWAP Operations

A SWAP operation exchanges the positions of two logical qubits occupying adjacent physical locations.

The objective is to find a sequence of legal SWAP operations that transforms an initial configuration into a target configuration while minimizing the total number of operations.

Formally:

\[
C^*=\min_{\mathcal{P}}|\mathcal{P}|
\]

where \(\mathcal{P}\) is a valid sequence of SWAP operations.

## 4. Methodology

The project uses a combination of mathematical modeling and computational search.

### 4.1 Permutation Theory

Configurations are represented using permutations. The symmetric group provides the mathematical framework for describing all possible arrangements of logical qubits.

### 4.2 Graph Theory

Hardware connectivity is represented using adjacency lists. Different hardware topologies can be modeled and analyzed through their graph structures.

### 4.3 State-Space Graph Construction

A state-space graph is constructed in which:

- Each vertex represents a complete qubit configuration.
- Each edge represents one legal SWAP operation.

This transforms the routing problem into a shortest-path search problem.

### 4.4 Exact Breadth-First Search

Breadth-First Search (BFS) is implemented to find the minimum number of SWAP operations.

Since every SWAP operation has unit cost, BFS guarantees an optimal solution for the modeled problem.

The implementation also reconstructs the sequence of operations and validates the resulting path.

## 5. Preliminary Results

The initial implementation has been tested on a four-qubit path topology.

| Initial Configuration | Target Configuration | Minimum SWAPs |
|---|---|---:|
| ABCD | DCBA | 6 |
| ABCD | BCDA | 3 |

An inversion-count analysis was also implemented.

For a path topology with adjacent swaps, the inversion count of a target permutation relative to the identity configuration equals the minimum number of adjacent swaps required to reach that permutation.

These experiments provide initial validation of the exact search implementation.

## 6. Repository Structure

```text
quantum-computer-architecture-research/
│
├── README.md
│
└── notebooks/
    ├── 01_permutations_and_symmetric_group.ipynb
    ├── 02_graph_theory.ipynb
    ├── 03_state_space_graph.ipynb
    └── 04_exact_bfs_solver.ipynb
```

## 7. Current Limitations

The current implementation is a simplified token-swapping model rather than a complete quantum circuit routing framework.

It does not yet incorporate:

- Quantum circuit gate dependencies.
- Parallel SWAP scheduling and circuit depth.
- Hardware noise and gate fidelity.
- Nonuniform SWAP operation costs.
- Hardware-specific error constraints.

The exact BFS solver is intended for small instances because the configuration state space grows factorially with the number of qubits.

## 8. Future Research Directions

The next stages of this project will investigate:

1. Graph-based lower bounds for minimum SWAP counts.
2. Comparison between exact solutions and heuristic algorithms.
3. Optimality gaps across different hardware topologies.
4. Mathematical properties of routing instances and their state spaces.
5. Experimental evaluation of lower-bound effectiveness.

## 9. Technologies

- Python
- Google Colab
- Jupyter Notebook
- Graph Theory
- Permutation Groups
- Breadth-First Search
- Combinatorial Optimization

## 10. Project Status

**Status: Research Prototype — Foundational Implementation Completed**

The mathematical foundations and initial exact solver have been implemented. Further experiments and theoretical analysis are required before drawing conclusions about lower-bound effectiveness or heuristic optimality.

---

*This repository documents an ongoing exploration of mathematical and algorithmic approaches to quantum computer architecture.*
