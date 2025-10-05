# Complete Report: Comparison between Genetic Algorithm and Evolution Strategy

## 1. Introduction

### 1.1 Study Objective

This report presents a detailed comparative analysis between the Genetic Algorithm (GA) and the Evolution Strategy (ES) for optimizing complex benchmark functions. The main goal is to understand how different evolutionary approaches behave on high-dimensional continuous optimization problems (d = 30).

### 1.2 Benchmark Functions Used

Four classic benchmark functions were used, each with characteristics that challenge algorithms in different ways:

* **Ackley function**: Many local minima, global optimum at (0,0,...,0)
* **Rastrigin function**: Highly multimodal, many shallow local minima
* **Schwefel function**: Many local minima, global optimum far from the origin
* **Rosenbrock function**: Narrow, long valley, global optimum at (1,1,...,1)

### 1.3 Methodology Rationale

Choosing 30 independent runs per test was based on the need for statistically reliable results, given the stochastic nature of evolutionary algorithms. This approach allows identification of performance patterns and evaluation of method robustness.

---

## 2. Algorithm Implementations

### 2.1 Genetic Algorithm (GA)

#### 2.1.1 Structure and Representation

* **Representation**: Real-valued vectors of dimension 30
* **Population**: 100 individuals
* **Initialization**: Random values uniformly distributed within each function's bounds

#### 2.1.2 Genetic Operators

**Parent Selection (Binary Tournament)**

```python
# For each new parent, two individuals are randomly drawn
# The one with better fitness (lower value) is selected
```

**Rationale**: Binary tournament keeps adequate selective pressure without being overly elitist, allowing intermediate-fitness individuals a chance to reproduce.

**Recombination (Arithmetic Crossover)**

```python
# For each pair of parents, two children are generated as:
child1 = α * parent1 + (1-α) * parent2
child2 = α * parent2 + (1-α) * parent1
# where α is a random value between 0 and 1
```

**Rationale**: Arithmetic crossover suits continuous problems because it preserves search-space continuity and enables smooth combinations of parental solutions.

**Mutation (Gaussian)**

```python
# Each gene has probability 1/d to mutate
# Mutation = current_value + N(0, 0.1)
# Values are clipped to valid bounds
```

**Rationale**: Gaussian mutation introduces continuous variation, appropriate for continuous optimization. The 1/d probability ensures, on average, one gene per individual is mutated.

**Survivor Selection (Elitism)**

```python
# The best individual from the previous generation is always kept
# The remaining population slots are filled by the best offspring
```

**Rationale**: Elitism prevents loss of good solutions but can reduce diversity if overused.

### 2.2 Evolution Strategy (ES)

#### 2.2.1 Structure and Representation

* **Type**: (μ, λ)-ES
* **μ (parents)**: 30 individuals
* **λ (offspring)**: 200 individuals
* **Representation**: Real-valued vectors of dimension 30

#### 2.2.2 Evolutionary Operators

**Recombination (Intermediate)**

```python
# For each offspring, two parents are chosen at random
# The child is the average of the two parents
child = (parent1 + parent2) / 2
```

**Rationale**: Intermediate recombination is conservative and stable, suitable for continuous problems where gradual exploration is desired.

**Mutation (Gaussian)**

```python
# Every gene of each offspring receives Gaussian noise
# Mutation = current_value + N(0, 0.1)
# Values are clipped to valid bounds
```

**Rationale**: Similar to the GA, but applied to all offspring, ensuring broad exploration of the search space.

**Survivor Selection ((μ, λ)-ES)**

```python
# Only the μ best among the λ offspring form the new population
# There is no explicit elitism
```

**Rationale**: The strong selective pressure (λ ≫ μ) favors exploration and diversity but can hinder convergence on problems with narrow global optima.

---

## 3. Initial Experimental Results

### 3.1 Experimental Setup

* **Number of runs**: 30 independent runs per function/algorithm
* **Total runs**: 240 (4 functions × 2 algorithms × 30 runs)
* **Number of generations**: 1000
* **Dimension**: 30

### 3.2 Statistical Results

| Function   | GA: Mean ± SD    | ES: Mean ± SD    | Best Algorithm    |
| ---------- | ---------------- | ---------------- | ----------------- |
| Ackley     | 8.69 ± 0.97      | 8.24 ± 1.03      | ES (5.2% better)  |
| Rastrigin  | 13.37 ± 4.02     | 51.79 ± 6.06     | GA (74.2% better) |
| Schwefel   | 9580.41 ± 379.71 | 9098.40 ± 657.43 | ES (5.0% better)  |
| Rosenbrock | 5.90 ± 17.42     | 64.90 ± 18.25    | GA (90.9% better) |

### 3.3 Results Analysis

**Ackley**: Both algorithms performed well, with a slight advantage for ES. The function has many local minima, but the global optimum is relatively easy to find.

**Rastrigin**: GA significantly outperformed ES. This function has many shallow local minima where GA's elitism helps retain good solutions.

**Schwefel**: ES achieved a better mean but with higher variability. The function is highly multimodal and benefits from ES’s stronger selective pressure.

**Rosenbrock**: GA showed a much better mean but high variability. The narrow valley of this function favors GA's arithmetic crossover.

---

## 4. Improvement Experiments

### 4.1 Motivation for Experiments

Based on initial results, we identified specific improvement opportunities for each algorithm:

1. **GA on Rosenbrock**: Excellent mean but high variability
2. **ES on Rastrigin**: Much worse performance than GA
3. **GA on other functions**: Potential for general improvements

### 4.2 Genetic Algorithm V2 (GA V2)

#### 4.2.1 Implemented Improvements

**Increased Population (100 → 200)**

* **Rationale**: Greater genetic diversity, important for narrow-valley problems like Rosenbrock

**Increased Mutation Rate (1/d → 2/d)**

* **Rationale**: Greater exploration of the search space

**Adaptive Mutation**

```python
# If little improvement in the last 10 generations:
mutation_rate = mutation_rate * 1.5
# If stagnation in the last 5 generations:
std_dev = 0.2  # Increase standard deviation
```

**Rationale**: Dynamically adjust mutation based on progress to avoid premature convergence

**Reduced Elitism (1 individual → 20% of population)**

* **Rationale**: Preserve good solutions while maintaining diversity

#### 4.2.2 GA V2 Results

| Function   | Original GA      | GA V2            | Improvement |
| ---------- | ---------------- | ---------------- | ----------- |
| Ackley     | 8.69 ± 0.97      | 5.37 ± 0.86      | 38.3%       |
| Rastrigin  | 13.37 ± 4.02     | 16.35 ± 8.43     | -22.3%      |
| Schwefel   | 9580.41 ± 379.71 | 7388.04 ± 478.98 | 22.9%       |
| Rosenbrock | 5.90 ± 17.42     | 2.12 ± 0.59      | 64.0%       |

**Analysis**: GA V2 was highly effective on Ackley, Schwefel, and Rosenbrock, but worsened on Rastrigin. This suggests the improvements are problem-specific.

### 4.3 Evolution Strategy V2 (ES V2)

#### 4.3.1 Implemented Improvements

**Reduced Selective Pressure (λ=200 → λ=150)**

* **Rationale**: Lower selective pressure to allow more exploration

**Increased Parent Population (μ=30 → μ=50)**

* **Rationale**: Greater parental diversity

**Uniform Recombination**

```python
# For each gene, randomly choose between the two parents
child[i] = parent1[i] if random() < 0.5 else parent2[i]
```

**Rationale**: Greater genetic diversity in recombination

**Added Elitism**

* **Rationale**: Preserve the best individual across generations

#### 4.3.2 ES V2 Results

**Rastrigin**: 72.54 ± 6.88 (worsened by 40.1% vs original)

**Analysis**: Aggressive changes worsened performance, indicating the original ES was better suited for Rastrigin.

### 4.4 Evolution Strategy V3 (ES V3)

#### 4.4.1 Conservative Adjustments

**Intermediate Parameters**

* μ = 40 (between original 30 and V2's 50)
* λ = 180 (between original 200 and V2's 150)
* Recombination: return to intermediate recombination (original)
* Keep elitism

**Rationale**: Incremental adjustments based on V2 results

#### 4.4.2 ES V3 Results

**Rastrigin**: 30.66 ± 3.64 (improved 40.8% vs original)

**Analysis**: The conservative approach worked better, confirming that incremental adjustments are safer.

---

## 5. Detailed Statistical Analysis

### 5.1 Comparative Boxplots

The generated boxplots provide important visual insights:

**Result Distribution**

* Show variability between runs
* Identify outliers (exceptionally good or bad runs)
* Allow direct comparison between algorithms

**Boxplot Interpretation**

* **Median**: Central tendency of results
* **Quartiles**: Data dispersion
* **Outliers**: Atypical runs that may indicate convergence to different local optima

### 5.2 Robustness Analysis

**Original GA**

* More robust on Rastrigin and Rosenbrock
* Lower variability on functions with shallow local minima

**Original ES**

* More robust on Schwefel
* Higher variability, but better mean on highly multimodal functions

**GA V2**

* Significantly improved robustness on Rosenbrock
* Kept good performance on Ackley and Schwefel
* Worsened on Rastrigin (overfitting to other problem types)

**ES V3**

* Improved robustness on Rastrigin
* Showed that incremental adjustments are safer

---

## 6. Conclusions and Recommendations

### 6.1 Key Findings

1. **There is no universally superior algorithm**

   * Each function requires specific approaches
   * Problem characteristics determine the best method

2. **GA is more effective for problems with shallow local minima**

   * Excellent on Rastrigin and Rosenbrock
   * Benefits from elitism and arithmetic crossover

3. **ES is more effective for highly multimodal problems**

   * Better on Schwefel
   * Benefits from stronger selective pressure

4. **Problem-specific improvements outperform generic ones**

   * GA V2 worked well on 3 of 4 functions
   * ES V3 outperformed ES V2

### 6.2 Practical Recommendations

**For problems with shallow local minima (e.g., Rastrigin)**

* Use GA with elitism
* Consider larger populations and adaptive mutation

**For highly multimodal problems (e.g., Schwefel)**

* Use ES with appropriate selective pressure
* Avoid overly aggressive tuning

**For problems with narrow valleys (e.g., Rosenbrock)**

* Use GA with a larger population
* Implement adaptive mutation

**For practical applications**

* Always perform multiple runs
* Use robust statistical analysis
* Test different configurations
* Consider problem-specific characteristics

### 6.3 Limitations and Future Work

**Study Limitations**

* Tested only on benchmark functions
* Fixed parameters per algorithm
* Fixed dimension (d = 30)

**Suggested Future Work**

* Test on real-world optimization problems
* Implement adaptive parameters
* Explore varied dimensions
* Develop hybrid methods
* Implement formal statistical tests (t-test, ANOVA)

---

## 7. References and Generated Files

### 7.1 Result Files

* `resultados/ga_*_melhores_fitness.txt`: Best GA fitness values
* `resultados/es_*_melhores_fitness.txt`: Best ES fitness values
* `resultados/*_convergencia_media.txt`: Average convergence history
* `resultados/*_estatisticas.txt`: Detailed statistics

### 7.2 Generated Plots

* `resultados/boxplot_comparativo_*.png`: Comparative boxplots
* `resultados/*_convergencia_media.png`: Convergence plots
* `resultados/comparacao_*.png`: Visual comparisons

### 7.3 Source Code

* `algoritmos/genetic_algorithm.py`: Original GA
* `algoritmos/genetic_algorithm_v2.py`: Improved GA
* `algoritmos/evolution_strategy.py`: Original ES
* `algoritmos/evolution_strategy_v2.py`: Aggressive ES
* `algoritmos/evolution_strategy_v3.py`: Conservative ES

---

## 8. Appendix: Detailed Technical Analysis

### 8.1 Computational Complexity

* **GA**: O(n × g × p) where n = dimension, g = generations, p = population size
* **ES**: O(n × g × λ) where λ = number of offspring

### 8.2 Convergence Analysis

The convergence plots show:

* Initial convergence speed
* Stagnation in local optima
* Effectiveness of escape strategies

### 8.3 Impact of Parameters

* **Population**: Larger population = more diversity but higher computational cost
* **Mutation**: Higher mutation = more exploration but may harm convergence
* **Selective Pressure**: Higher pressure = faster convergence but higher risk of local optima
