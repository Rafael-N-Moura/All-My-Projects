# Pit-Stop Strategy Optimizer - Formula 1

## 📋 Project Description

This project implements an advanced pit-stop strategy optimization system for Formula 1 races using bio-inspired algorithms. The system compares two main algorithms with robust statistical analysis:

1. **Genetic Algorithm (GA)** – Based on natural evolution
2. **Ant Colony Optimization (ACO)** – Based on ant behavior

The goal is to find the pit-stop strategy that minimizes total race time, taking into account factors such as tyre degradation, fuel effect, pit stop time and **official F1 rules**.

## 🏗️ System Architecture

### Directory Structure

```
f1_optimizer/
├── main.py                 # Main script for basic execution
├── optimize_and_analyze.py # Optimization and robust statistical analysis script
├── test_multiple_drivers.py # Script to test multiple drivers
├── visualize_results.py    # Basic visualization script
├── visualize_statistics.py # Advanced statistical visualization script
├── requirements.txt        # Project dependencies
├── README.md               # Documentation
├── RELATORIO_FINAL_PROJETO.md # Complete project report
├── RESUMO_EXECUTIVO.md     # Executive summary
├── data/
│   └── cache/              # FastF1 data cache
├── results/                # Results and visualizations
└── src/
    ├── __init__.py
    ├── data_handler.py     # Data loading and processing module
    ├── race_simulator.py   # Race simulator with F1 validation
    ├── genetic_algorithm.py# GA implementation with F1 rules
    ├── ant_colony.py       # ACO implementation with decision graph
    ├── parameter_optimizer.py # Systematic parameter optimizer
    └── statistical_analyzer.py # Robust statistical analyzer
```

## 🚀 Installation and Setup

### Prerequisites

* Python 3.8 or higher
* Internet connection (to download data via FastF1)
* 4GB+ RAM (for robust statistical analysis)

### Installation

1. **Clone the repository:**

```bash
git clone <repository-url>
cd f1_optimizer
```

2. **Create a virtual environment:**

```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
# or
venv\Scripts\activate     # Windows
```

3. **Install dependencies:**

```bash
pip install -r requirements.txt
```

## 📊 How to Use

### Basic Execution

1. **Run the basic optimizer:**

```bash
python main.py
```

2. **View basic results:**

```bash
python visualize_results.py
```

### Parameter Optimization and Robust Statistical Analysis

1. **Run full optimization and statistical analysis:**

```bash
python optimize_and_analyze.py
```

*Estimated time: 5-8 hours for a complete analysis*

2. **For a quick test (fewer runs):**

```bash
python optimize_and_analyze.py --quick
```

3. **View advanced statistical results:**

```bash
python visualize_statistics.py
```

### Test Multiple Drivers

```bash
python test_multiple_drivers.py
```

### Scenario Configuration

To test different scenarios, edit the variables in the scripts:

```python
# Default test scenario configuration
year = 2024
race_name = "Spain Grand Prix"
driver_code = "HAM"  # Lewis Hamilton
```

## 🔧 System Modules

### 1. DataHandler (`src/data_handler.py`)

Responsible for loading and processing F1 race data via the FastF1 API.

**Features:**

* Loading data via FastF1 with local cache
* Advanced preprocessing (filtering accurate laps)
* Correction for fuel effect
* Time conversion to seconds
* Data integrity validation

**Data Collected from the API:**

* **LapTime**: Lap time
* **LapNumber**: Lap number
* **Compound**: Tyre compound (SOFT, MEDIUM, HARD, INTERMEDIATE)
* **TyreLife**: Tyre age in laps
* **IsAccurate**: Flag indicating whether the lap is accurate
* **DriverCode**: Driver code

**Main Methods:**

* `get_race_data(year, race_name, driver_code)`: Loads data for a specific race
* `get_available_compounds(race_data)`: Gets available compounds
* `get_race_info(race_data)`: Returns basic race information

### 2. RaceSimulator (`src/race_simulator.py`)

Race simulator with automatic calibration and F1 rules validation.

**Features:**

* Automatic parameter calibration via linear regression
* Lap-by-lap simulation with a mathematical model
* F1 rules validation (use of at least 2 compounds)
* Automatic correction of unrealistic parameters
* Penalization of invalid strategies

**Mathematical Model:**

```
Lap_Time = T_base + α_compound + (δ_degradation × tyre_age) - (δ_fuel × current_lap)
```

**Implemented F1 Validations:**

* Mandatory use of at least 2 different compounds
* Realistic limit of 3 pit stops
* Severe penalty for invalid strategies

**Main Methods:**

* `evaluate_strategy(strategy)`: Evaluates a complete strategy
* `_calculate_model_parameters()`: Calibrates parameters via ML
* `_validate_and_correct_parameters()`: Corrects unrealistic parameters
* `get_model_parameters()`: Returns parameters for analysis

### 3. GeneticAlgorithm (`src/genetic_algorithm.py`)

GA implementation with F1 rules validation.

**Characteristics:**

* Representation: List of tuples `(pit_lap, new_compound)`
* Selection: Tournament
* Crossover: One-point
* Mutation: Change pit lap, compound, add/remove pit stop
* Elitism: Preserves best individuals
* **F1 Validation**: Severe penalty for violating the 2-compound rule

**Main Methods:**

* `run()`: Runs the algorithm
* `calculate_fitness(individual)`: Computes fitness with F1 validation
* `tournament_selection()`: Tournament selection
* `crossover()`: One-point crossover
* `mutate()`: Applies mutations

### 4. AntColonyOptimizer (`src/ant_colony.py`)

ACO implementation modeled as a decision graph.

**Characteristics:**

* **Decision graph modeling**: Each lap is a node with possible decisions
* **Pheromone matrix**: For each lap/decision
* **Probabilistic transition rule**: Normalized to ensure valid probabilities
* **Heuristic information**: Based on the race simulator
* **F1 Validation**: Enforces use of at least 2 compounds
* **Realistic limit**: Maximum 3 pit stops

**Problem Representation:**

```
Decision Graph:
Lap 1: [CONTINUE, SOFT, MEDIUM, HARD] → Probabilities based on pheromone + heuristic
Lap 2: [CONTINUE, SOFT, MEDIUM, HARD] → Updated probabilities
...
Lap N: [CONTINUE, SOFT, MEDIUM, HARD] → Final probabilities
```

**Main Methods:**

* `run()`: Executes the algorithm
* `build_solution()`: Builds a solution by a single ant
* `_calculate_transition_probabilities()`: Computes normalized transition probabilities
* `update_pheromones()`: Updates the pheromone matrix
* `_calculate_heuristic()`: Computes heuristic information

### 5. ParameterOptimizer (`src/parameter_optimizer.py`)

Systematic hyperparameter optimization for the algorithms.

**Features:**

* **Grid Search**: Systematic grid search over parameters
* **Random Search**: Random search for quick exploration
* **Robust evaluation**: Multiple runs per configuration
* **Auto-save**: Saves optimized parameters in JSON

**Optimized Parameters:**

**GA:**

* `population_size`: [30, 50, 70, 100]
* `generations`: [50, 100, 150, 200]
* `mutation_rate`: [0.05, 0.1, 0.15, 0.2]
* `crossover_rate`: [0.6, 0.8, 0.9, 1.0]
* `elitism_size`: [2, 5, 10]

**ACO:**

* `num_ants`: [20, 30, 50, 70]
* `iterations`: [30, 50, 70, 100]
* `evaporation_rate`: [0.05, 0.1, 0.15, 0.2]
* `alpha`: [0.5, 1.0, 1.5, 2.0]
* `beta`: [1.0, 2.0, 3.0, 4.0]

### 6. StatisticalAnalyzer (`src/statistical_analyzer.py`)

Robust statistical analysis system for scientific comparison of algorithms.

**Features:**

* **Multiple runs**: 30 runs per algorithm (configurable)
* **Complete statistical tests**:

  * **Shapiro-Wilk**: Normality test
  * **t-Student**: Parametric test for mean comparison
  * **Wilcoxon**: Non-parametric paired test
  * **Mann-Whitney U**: Non-parametric test for independent samples
* **Effect size analysis**: Cohen's d
* **Advanced metrics**: CV, quartiles, descriptive statistics

**Collected Metrics:**

* Total race time
* Algorithm runtime
* Number of pit stops
* Strategy variability
* Convergence rate
* Result consistency

## 📈 Results Analysis

### Compared Metrics

1. **Quality of Final Solution**

   * Total race time
   * Found strategy (pit laps and compounds)
   * F1 rules validation

2. **Statistical Performance**

   * Mean, standard deviation, coefficient of variation
   * Quartiles and extremes
   * Significance tests
   * Effect size (Cohen's d)

3. **Convergence Speed**

   * Fitness curves per generation/iteration
   * Convergence rate
   * Stability of results

4. **Consistency and Robustness**

   * Variability across runs
   * Reliability of results
   * Outlier analysis

### Generated Visualizations

**Basic:**

* Convergence: Comparison of fitness curves
* Strategies: Comparison of found strategies
* Performance: Total time and runtime metrics

**Advanced Statistics:**

* Boxplots of time distributions
* Frequency histograms
* Comparative convergence plots
* Analysis of found strategies
* Visualization of statistical tests
* Effect size plots

## 🔬 Advanced Features Implemented

### 1. Advanced Data Collection and Processing

**FastF1 API Data:**

* Automatic collection of real race data
* Processing with fuel-effect correction
* Filtering of imprecise laps (Safety Car, pit entry/exit)
* Automatic calibration of parameters via linear regression

**Calibrated Mathematical Model:**

```python
# Linear regression per compound
X = compound_data['TyreLife'].values  # Tyre age
y = compound_data['CorrectedTime'].values  # Corrected time
model = LinearRegression()
model.fit(X, y)
degradation_coeff = model.coef_[0]  # δ_degradation
```

### 2. F1 Rules Validation

**Implemented Rules:**

* **Mandatory use of at least 2 compounds**: Severe penalty (50000s)
* **Realistic pit stop limit**: Maximum 3 stops
* **Validation of empty strategies**: Returns infinity for strategies with no stops

**Implementation:**

```python
# Check unique compounds
total_compounds = len(set(strategy_compounds) | {initial_compound})
if total_compounds < 2:
    penalty += 50000.0  # Severe penalty
```

### 3. Systematic Parameter Optimization

**Full Grid Search:**

* 3125 parameter combinations per algorithm
* Evaluation with multiple runs per configuration
* Automatic saving of best parameters

**Example Optimized Parameters (HAM, Spain 2024):**

```python
# Optimized GA
{
    "population_size": 70,
    "generations": 150,
    "mutation_rate": 0.15,
    "crossover_rate": 0.9,
    "elitism_size": 5
}

# Optimized ACO
{
    "num_ants": 50,
    "iterations": 70,
    "evaporation_rate": 0.1,
    "alpha": 1.5,
    "beta": 2.0
}
```

### 4. Robust Statistical Analysis

**Implemented Tests:**

* **Shapiro-Wilk**: Tests data normality
* **t-Student**: Compares means (when data is normal)
* **Wilcoxon**: Robust non-parametric test
* **Mann-Whitney U**: Independent sample comparison
* **Cohen's d**: Measures effect size

**Typical Results (HAM, Spain 2024):**

```python
# ACO vs GA
ACO_mean = 4858.76s, CV = 0.001%
GA_mean = 4859.44s, CV = 0.034%
Cohen's_d = 0.582 (medium effect)
p_value = 0.023 (significant)
```

### 5. Advanced ACO Representation

**Decision Graph:**

* Each lap is a node with possible decisions
* Pheromones guide exploration
* Heuristic considers pit stop cost
* Normalization ensures valid probabilities

**Transition Rule:**

```python
P(decision) = (τ^α × η^β) / Σ(τ^α × η^β)
# Normalization ensures ΣP = 1
```

### 6. Scientific Visualizations

**Generated Plots:**

* Comparative performance boxplots
* Time distribution histograms
* Convergence curves
* Analysis of found strategies
* Visualization of statistical tests
* Effect size charts

## 📊 Example Full Output

```
============================================================
PIT-STOP STRATEGY OPTIMIZER - FORMULA 1
============================================================

Test scenario:
Year: 2024
Race: Spain Grand Prix
Driver: HAM (Lewis Hamilton)
Initial compound: MEDIUM
----------------------------------------

1. Loading race data...
Data loaded successfully!
Total laps: 66
Compounds used: ['SOFT', 'MEDIUM', 'HARD']
Average lap time: 85.23s

2. Initializing race simulator...
Model parameters (calibrated via ML):
  Base time (T_base): 82.45s
  Fuel effect: 0.035s/lap
  Degradation coefficients: {'SOFT': 0.12, 'MEDIUM': 0.08, 'HARD': 0.05}
  Performance deltas: {'SOFT': -2.1, 'MEDIUM': 0.0, 'HARD': 1.5}

3. Running Genetic Algorithm (optimized parameters)...
----------------------------------------
Generation 0: Best fitness = 0.011234
Generation 10: Best fitness = 0.011456
...
Generation 150: Best fitness = 0.011789

Genetic Algorithm Results:
  Best strategy: [(25, 'MEDIUM'), (52, 'HARD')]
  Total time: 4859.44s
  Execution time: 12.45s
  F1 validation: ✅ 2 compounds used

4. Running Ant Colony Optimization (optimized parameters)...
----------------------------------------
Iteration 0: Best time = 4865.45s
Iteration 10: Best time = 4862.23s
...
Iteration 70: Best time = 4858.76s

ACO Results:
  Best strategy: [(23, 'MEDIUM'), (50, 'HARD')]
  Total time: 4858.76s
  Execution time: 8.92s
  F1 validation: ✅ 2 compounds used

5. Robust Statistical Analysis
========================================
Runs: 30 per algorithm
Tests performed: Shapiro-Wilk, t-Student, Wilcoxon, Mann-Whitney U

Statistical Results:
  ACO - Mean: 4858.76s, CV: 0.001%, Std: 0.05s
  GA  - Mean: 4859.44s, CV: 0.034%, Std: 1.65s
  
Significance Tests:
  t-Student: p = 0.023 (significant)
  Wilcoxon: p = 0.018 (significant)
  Mann-Whitney U: p = 0.021 (significant)
  
Effect Size:
  Cohen's d = 0.582 (medium effect)

🏆 FINAL RECOMMENDATION:
  Algorithm: ACO (Ant Colony Optimization)
  Rationale: Statistically significant superiority, greater consistency (lower CV)
  Optimized parameters: num_ants=50, iterations=70, alpha=1.5, beta=2.0

✅ Analysis complete! Results saved in 'results/'
============================================================
```

## 🛠️ Troubleshooting

### Common Issues

1. **Error loading data:**

   * Check your internet connection
   * Confirm the year, race and driver are correct
   * Ensure FastF1 is up to date
   * Clear cache: `rm -rf data/cache/*`

2. **Insufficient data:**

   * The system uses defaults when data is insufficient
   * Check if the driver finished the race
   * Try another driver or race

3. **Long execution time:**

   * Use `--quick` for a fast analysis
   * Reduce the number of runs in `statistical_analyzer.py`
   * Lower optimization parameters

4. **Memory error:**

   * Reduce the number of concurrent runs
   * Use quick analysis with `--quick`
   * Close other programs while running

5. **Inconsistent results:**

   * Run multiple times to verify consistency
   * Check if the race data is adequate
   * Use robust statistical analysis

## 📚 References and Documentation

### Project Documentation

* **RELATORIO_FINAL_PROJETO.md**: Full report with methodology and results
* **RESUMO_EXECUTIVO.md**: Executive summary
* **PLANEJAMENTO_OTIMIZACAO_ESTATISTICA.md**: Optimization planning

### Libraries Used

* **FastF1**: Official F1 data collection
* **Pandas**: Data manipulation and analysis
* **NumPy**: Numerical computing
* **Matplotlib/Seaborn**: Visualizations
* **Scikit-learn**: Machine Learning (linear regression)
* **SciPy**: Statistical tests

### Scientific References

* **Genetic Algorithms**: Goldberg, D. E. (1989). *Genetic algorithms in search, optimization, and machine learning.*
* **Ant Colony Optimization**: Dorigo, M., & Stützle, T. (2004). *Ant colony optimization.*
* **Statistical Analysis**: Cohen, J. (1988). *Statistical power analysis for the behavioral sciences.*

## 🤝 Contributions

To contribute to the project:

1. Fork the repository
2. Create a feature branch
3. Implement your changes
4. Add tests if needed
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---
