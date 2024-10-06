# Steiner Tree Problem Solver

This project aims to solve the Steiner Tree Problem, a well-known combinatorial optimization problem. The Steiner problem involves finding a minimum-cost tree that spans a set of terminal nodes in a graph, with possible inclusion of additional non-terminal nodes. This problem has a variety of real-world applications, such as network design, circuit layouts, and transportation systems.

## Introduction

The Steiner Tree Problem is named after the Swiss mathematician Jakob Steiner and belongs to the field of combinatorial optimization. It is a graph-based problem where the goal is to find the least-cost tree that spans a set of terminal vertices. The problem is NP-hard, meaning finding an exact solution in reasonable time becomes impractical for large input sizes. Hence, approximation and heuristic methods are commonly used.

## Problem Description

Given:

  - A graph G(V, E) where V is a set of vertices and E is a set of edges.
  - A set of terminal vertices T.
  - Non-negative costs assigned to edges.

The objective is to find a tree that spans all terminals with the minimum cost. Non-terminal vertices may be included in the tree if they reduce the overall cost.

**Example**

Consider a graph with vertices A, B, C, and D, where A and D are terminal nodes. The goal is to connect these terminals with the least-cost path, possibly adding intermediate nodes (non-terminals) to minimize cost.

## Algorithms Implemented

This project implements two key approaches to solve the Steiner Tree Problem:

### 1. Branch-and-Bound Algorithm

This exact algorithm explores all possible solutions, recursively dividing the problem into sub-problems. It systematically evaluates potential solutions while pruning sub-optimal branches. Although it guarantees an optimal solution, the algorithm is computationally expensive with exponential time complexity in the worst case.

**Pseudo Code:**

```
BranchAndBound(Graph G, Set T):
    Initialize least_cost = INFINITY
    Initialize optimal_tree = NULL
    Call SubProblemSolver(G, T, {}, 0, least_cost, optimal_tree)
    Return optimal_tree
```

### 2. Vazirani and Yannakakis Approximation Algorithm

This approximation algorithm provides near-optimal solutions within a constant factor of the best possible result. It builds clusters of terminal nodes and connects them using minimum spanning trees, yielding efficient results with much faster runtimes.

**Pseudo Code:**

```
VAY(Graph G, Set T):
    MST = MinimumSpanningTree(G)
    Return MST
```

## Mathematical Formulation

Given:

- **G(V, E)**: A graph with a set of vertices V and edges E.
- **T(V)**: A set of terminal vertices.
- **Cost(E)**: The cost of traveling between vertices using edge E.

The goal is to minimize the total cost of edges in the Steiner Tree ST:


$min(\sum Cost(E)) for E \in ST $


## Applications

The Steiner Tree Problem has numerous real-world applications, including:

1. VLSI Design: Optimizing circuit layouts to minimize wiring costs.
2. Telecommunications: Reducing the amount of cable or fiber optic lines required.
3. Molecular Biology: Constructing phylogenetic trees that represent evolutionary relationships.
4. Robotics: Planning optimal paths for robots to navigate through various nodes.
5. Transportation Networks: Selecting optimal routes for vehicles, pipelines, and powerlines.

## Results

### Example Outputs

- Branch-and-Bound: Provides the optimal tree but can be computationally expensive for large graphs.
- Approximation (Vazirani and Yannakakis): Offers faster results with an approximation error bound of 2, ensuring the solution is within twice the optimal cost.

### Performance Comparison

- Branch-and-Bound: Time complexity: O(2^n), Space complexity: O(n)
- Vazirani and Yannakakis: Time complexity: O(|E| log(|V|)), Space complexity: O(n)

In the project, we test both algorithms on various graphs, demonstrating the trade-offs between speed and accuracy.
