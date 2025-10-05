# 🧩 Genetic Algorithm for the 8-Queens Problem

This project implements a genetic algorithm to solve the 8-queens problem, following the provided specifications.

## Implemented Specifications

* **Representation**: Permutation of a bit-string
* **Recombination**: *cut-and-crossfill* crossover
* **Crossover Probability**: 90%
* **Mutation**: Gene swap (swap mutation)
* **Mutation Probability**: 40%
* **Parent Selection**: Ranking — best of 2 from 5 randomly chosen (tournament-like selection)
* **Survivor Selection**: Replace the worst
* **Population Size**: 100
* **Number of Children per Mating**: 2
* **Initialization**: Random
* **Termination Condition**: Find a solution or 10,000 fitness evaluations

## Requirements

* Python 3.7+
* NumPy
* Matplotlib

## Installation

```bash
pip install -r requirements.txt
```

## Execution

To run the algorithm:

```bash
python eight_queens_ga.py
```

## Results Analysis

The program runs 30 experiments and provides the following analyses:

1. Number of runs that converged
2. Mean and standard deviation of iterations to convergence
3. Average population fitness for each run
4. Convergence plots showing the mean and the best individual per iteration
5. Average fitness achieved across the 30 runs (mean and standard deviation)
