
# 📊 Statistics for Machine Learning

> **Source:** [GeeksforGeeks — Statistics for Machine Learning](https://www.geeksforgeeks.org/machine-learning/statistics-for-machine-learning/)

Statistics for Machine Learning is the study of collecting, analyzing, and interpreting data to build better ML models. It provides the mathematical foundation to understand data patterns, make predictions, and evaluate model performance.

---

## Table of Contents

1. [Why Learn Statistics for ML](#why-learn-statistics-for-ml)
2. [Applications of Statistics in ML](#applications-of-statistics-in-ml)
3. [Types of Statistics](#types-of-statistics)
4. [Descriptive Statistics](#descriptive-statistics)
5. [Inferential Statistics](#inferential-statistics)
6. [Probability Theory](#probability-theory)
7. [Bayesian Statistics](#bayesian-statistics)
8. [Quick Reference Cheat Sheet](#quick-reference-cheat-sheet)

---

## Why Learn Statistics for ML

- **Understand data** before training any model
- **Choose the right algorithm** for a specific problem
- **Evaluate model accuracy** and performance objectively
- **Handle uncertainty** and variability in real-world data

---

## Applications of Statistics in ML

| Area | How Statistics is Used |
|------|------------------------|
| **Feature Engineering** | Selecting and transforming useful variables |
| **Image Processing** | Analyzing patterns, shapes, and textures |
| **Anomaly Detection** | Spotting fraud or equipment failures |
| **Environmental Studies** | Modeling land cover, climate, and pollution |
| **Quality Control** | Identifying defects in manufacturing |

---

## Types of Statistics

```
Statistics
├── Descriptive Statistics  →  Summarize & organize existing data
└── Inferential Statistics  →  Draw conclusions about a larger population from a sample
```

- **Descriptive Statistics** — Simplifies and organizes large chunks of data to make them easier to understand.
- **Inferential Statistics** — Uses smaller sample data to draw conclusions and make predictions about an entire population.

---

## Descriptive Statistics

Descriptive statistics summarize and describe the features of a dataset, forming the foundation for further analysis.

### Measures of Central Tendency

| Measure | Definition | Formula |
|---------|-----------|---------|
| **Mean** | Sum of all values divided by total count | `μ = ΣX / n` |
| **Median** | Middle value of sorted data | `(n+1)/2`th value (odd n); average of `n/2`th and next (even n) |
| **Mode** | Most frequently occurring value | — |

### Measures of Dispersion

| Measure | Description |
|---------|-------------|
| **Range** | Difference between maximum and minimum values |
| **Variance** | Average squared deviation from the mean — measures overall spread |
| **Standard Deviation** | Square root of variance; spread relative to the mean |
| **Interquartile Range (IQR)** | Range between Q1 and Q3; measures spread around the median |

```
Range            = Max - Min
Variance (σ²)    = Σ(Xᵢ - μ)² / n
Std Deviation(σ) = √Variance
IQR              = Q3 - Q1
```

### Measures of Shape

- **Skewness** — Indicates asymmetry in data distribution.
  - Positive skew → tail on the right
  - Negative skew → tail on the left
  - Zero skew → symmetric (normal distribution)

- **Kurtosis** — Measures the "peakedness" of the distribution.
  - Leptokurtic → sharp peak, heavy tails (kurtosis > 3)
  - Platykurtic → flat peak, light tails (kurtosis < 3)
  - Mesokurtic → normal distribution baseline (kurtosis = 3)

---

## Inferential Statistics

Inferential statistics involve making predictions or inferences about a population based on a sample.

### Population vs Sample

| Term | Definition |
|------|-----------|
| **Population** | The entire group being studied |
| **Sample** | A subset of the population used for analysis |

### Estimation

- **Point Estimation** — Provides a single value estimate of a population parameter (e.g., sample mean as an estimate of population mean).
- **Interval Estimation** — Offers a range of values (confidence interval) within which the parameter likely lies.
- **Confidence Intervals** — Indicate the reliability of an estimate (e.g., 95% CI means we are 95% confident the true value lies within the range).

### Hypothesis Testing

A method to compare two opposite assumptions about a population using sample data to determine which is more likely true.

| Concept | Description |
|---------|-------------|
| **Null Hypothesis (H₀)** | Assumes no effect or relationship exists |
| **Alternative Hypothesis (H₁)** | Suggests an effect or relationship does exist |
| **Type I Error (α)** | Rejecting a true null hypothesis (false positive) |
| **Type II Error (β)** | Failing to reject a false null hypothesis (false negative) |
| **p-Value** | Probability of obtaining the observed results under H₀; small p → reject H₀ |

**Common Tests:**

| Test | Purpose |
|------|---------|
| **t-Test** | Compare means of one or two groups (small samples) |
| **z-Test** | Compare means when population std dev is known (large samples) |
| **ANOVA** | Compare means across three or more groups |
| **Chi-Square Test** | Assess association between categorical variables |

### Covariance and Correlation

| Measure | Description | Formula |
|---------|-------------|---------|
| **Covariance** | Degree to which two variables change together | `Cov(X,Y) = Σ(Xᵢ - X̄)(Yᵢ - Ȳ) / n` |
| **Correlation** | Strength and direction of relationship; ranges from -1 to +1 | `ρ = Cov(X,Y) / (σₓ · σᵧ)` |

- **Pearson Correlation** — Measures the linear relationship strength between two continuous variables.
- **Spearman Rank Correlation** — Assesses strength and direction of a monotonic (not necessarily linear) relationship.

```
Correlation values:
  +1.0  → Perfect positive relationship
   0.0  → No relationship
  -1.0  → Perfect negative relationship
```

### Visualization Techniques

| Chart | Purpose |
|-------|---------|
| **Histogram** | Shows the frequency distribution of a dataset |
| **Box Plot** | Highlights spread, median, and outliers (Q1, Q2, Q3, IQR) |
| **Scatter Plot** | Illustrates the relationship between two continuous variables |

### Regression Analysis

Understanding relationships between variables is central to ML model building.

| Type | Description |
|------|-------------|
| **Simple Linear Regression** | Models relationship between one predictor and one response variable |
| **Multiple Linear Regression** | Extends to two or more predictors |

**Key assumptions of linear regression:**
1. Linearity — relationship between X and Y is linear
2. Independence — observations are independent of each other
3. Homoscedasticity — constant variance of residuals
4. Normality — residuals are normally distributed

**Model Evaluation Metrics:**

| Metric | What it Measures |
|--------|-----------------|
| **R²** | Proportion of variance in Y explained by the model |
| **Adjusted R²** | R² adjusted for the number of predictors |
| **RMSE** | Root Mean Squared Error — average prediction error magnitude |

---

## Probability Theory

Probability theory forms the backbone of statistical inference, helping quantify uncertainty and make data-driven predictions.

### Basic Concepts

| Concept | Description |
|---------|-------------|
| **Random Variables** | Variables whose values are determined by random outcomes |
| **Probability Distributions** | Describe the likelihood of different outcomes |
| **Law of Large Numbers** | As sample size grows, sample mean converges to the population mean |
| **Central Limit Theorem** | Sample means follow a normal distribution as `n → ∞`, regardless of the original distribution |

### Common Probability Distributions

| Distribution | Type | Use Case |
|-------------|------|----------|
| **Binomial** | Discrete | Number of successes in a fixed number of trials |
| **Poisson** | Discrete | Number of events in a fixed time/space interval |
| **Normal (Gaussian)** | Continuous | Continuous data symmetrically distributed around the mean |

```
Normal Distribution:    X ~ N(μ, σ²)
Binomial Distribution:  X ~ B(n, p)
Poisson Distribution:   X ~ P(λ)
```

---

## Bayesian Statistics

Bayesian statistics combine **prior knowledge** (existing beliefs) with **new data** (observed evidence) to update understanding.

### Bayes' Theorem

```
P(A | B) = [ P(B | A) × P(A) ] / P(B)
```

| Term | Name | Meaning |
|------|------|---------|
| `P(A\|B)` | **Posterior** | Probability of A given B has occurred |
| `P(B\|A)` | **Likelihood** | Probability of B given A has occurred |
| `P(A)` | **Prior** | Initial probability of A before seeing data |
| `P(B)` | **Evidence** | Total probability of B |

**Key idea:** As new data arrives, the posterior becomes the new prior — beliefs update continuously.

---

## Quick Reference Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  STATISTICS FOR ML — FORMULA REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  DESCRIPTIVE
  Mean          μ = ΣX / n
  Variance      σ² = Σ(Xᵢ - μ)² / n
  Std Dev       σ = √σ²
  IQR           Q3 - Q1

  CORRELATION
  Covariance    Cov(X,Y) = Σ(Xᵢ-X̄)(Yᵢ-Ȳ) / n
  Pearson ρ     Cov(X,Y) / (σₓ · σᵧ)

  HYPOTHESIS TESTING
  p < 0.05      → Reject H₀ (statistically significant)
  p ≥ 0.05      → Fail to reject H₀

  NORMAL DISTRIBUTION
  68%  of data within ±1σ
  95%  of data within ±2σ
  99.7% of data within ±3σ

  BAYES' THEOREM
  P(A|B) = P(B|A) · P(A) / P(B)

  CENTRAL LIMIT THEOREM
  X̄ ~ N(μ, σ²/n)  for large n
$
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

*Notes compiled from GeeksforGeeks | Last updated: April 2026*

