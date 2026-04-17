# 📈 Covariance and Correlation — Statistics Notes

> A comprehensive reference guide to understanding the relationship between variables using Covariance and Correlation.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Covariance](#covariance)
3. [Correlation](#correlation)
4. [Covariance vs Correlation](#covariance-vs-correlation)
5. [Types of Correlation](#types-of-correlation)
6. [Pearson Correlation](#pearson-correlation-coefficient)
7. [Spearman Rank Correlation](#spearman-rank-correlation)
8. [Common Mistakes](#common-mistakes)
9. [Applications in Machine Learning](#applications-in-machine-learning)
10. [Formulas Cheat Sheet](#formulas-cheat-sheet)

---

## Introduction

In statistics, we often want to understand **how two variables relate to each other**. Two key tools for this are:

- **Covariance** — tells us the *direction* of the relationship
- **Correlation** — tells us both the *direction* and *strength* of the relationship

```
Example Questions they answer:
  → Do student study hours and exam scores move together?
  → Does temperature increase when humidity increases?
  → Are house size and house price positively related?
```

---

## Covariance

### Definition

Covariance measures **how much two variables change together**. It tells us the direction of the linear relationship between two variables.

```
If X increases and Y also increases  →  Positive Covariance
If X increases and Y decreases       →  Negative Covariance
If X and Y change independently      →  Zero Covariance
```

### Formula

**Population Covariance:**
```
         Σ (Xᵢ - μₓ)(Yᵢ - μᵧ)
Cov(X,Y) = ─────────────────────
                    N
```

**Sample Covariance:**
```
         Σ (Xᵢ - X̄)(Yᵢ - Ȳ)
Cov(X,Y) = ──────────────────────
                  n - 1
```

Where:
- `Xᵢ, Yᵢ` = individual data points
- `μₓ, μᵧ` = population means of X and Y
- `X̄, Ȳ`  = sample means of X and Y
- `N`      = population size
- `n`      = sample size (`n-1` is Bessel's correction)

### Worked Example

| Student | Study Hours (X) | Exam Score (Y) |
|---------|----------------|----------------|
| A       | 2              | 50             |
| B       | 4              | 65             |
| C       | 6              | 75             |
| D       | 8              | 85             |
| E       | 10             | 95             |

```
X̄ = (2+4+6+8+10) / 5 = 6
Ȳ = (50+65+75+85+95) / 5 = 74

Σ(Xᵢ - X̄)(Yᵢ - Ȳ):
  (2-6)(50-74) = (-4)(-24) =  96
  (4-6)(65-74) = (-2)(-9)  =  18
  (6-6)(75-74) = ( 0)( 1)  =   0
  (8-6)(85-74) = ( 2)(11)  =  22
  (10-6)(95-74)= ( 4)(21)  =  84
                          ─────
  Sum = 220

Cov(X,Y) = 220 / (5-1) = 55  ← Positive! Hours & scores move together.
```

### Limitations of Covariance

- **Not standardized** — the value depends on the units of measurement
- Hard to interpret: `Cov = 55` vs `Cov = 55,000` — which is stronger?
- Cannot compare covariance across different datasets
- **This is why we use Correlation** — it fixes these problems

---

## Correlation

### Definition

Correlation is a **standardized version of covariance**. It measures both the **direction** and **strength** of the linear relationship between two variables, always producing a value between **−1 and +1**.

```
Correlation = Covariance / (Std Dev of X × Std Dev of Y)
```

### Correlation Scale

```
  −1.0          −0.5          0.0          +0.5          +1.0
   |─────────────|─────────────|─────────────|─────────────|
 Perfect      Moderate       None        Moderate      Perfect
 Negative     Negative                   Positive      Positive
```

| Value Range | Interpretation |
|-------------|----------------|
| `+0.9 to +1.0` | Very strong positive |
| `+0.7 to +0.9` | Strong positive |
| `+0.5 to +0.7` | Moderate positive |
| `+0.3 to +0.5` | Weak positive |
| `0.0 to +0.3`  | Negligible positive |
| `0.0`          | No relationship |
| `-0.3 to  0.0` | Negligible negative |
| `-0.5 to -0.3` | Weak negative |
| `-0.7 to -0.5` | Moderate negative |
| `-0.9 to -0.7` | Strong negative |
| `-1.0 to -0.9` | Very strong negative |

---

## Covariance vs Correlation

| Feature | Covariance | Correlation |
|---------|-----------|-------------|
| **Measures** | Direction only | Direction + Strength |
| **Range** | −∞ to +∞ | −1 to +1 |
| **Units** | Has units (e.g., kg·cm) | Unitless (dimensionless) |
| **Standardized** | ❌ No | ✅ Yes |
| **Comparability** | Hard to compare | Easy to compare |
| **Affected by scale** | ✅ Yes | ❌ No |
| **Formula** | `Σ(X-X̄)(Y-Ȳ) / (n-1)` | `Cov(X,Y) / (σₓ · σᵧ)` |

---

## Types of Correlation

### 1. Positive Correlation
Both variables move in the **same direction**.
```
  ↑ X  →  ↑ Y        Examples:
                       • Study hours & exam scores
     *   *             • Height & weight
   *   *               • Temperature & ice cream sales
  *  *
```

### 2. Negative Correlation
Variables move in **opposite directions**.
```
  ↑ X  →  ↓ Y        Examples:
                       • Price & demand
  *                    • Speed & travel time
    *  *               • Exercise & body fat
       *  *
          *  *
```

### 3. Zero Correlation
**No linear relationship** between variables.
```
  Random scatter      Examples:
                       • Shoe size & IQ
  * *  *  *            • Height & salary
   *  * *  *           • Hair color & exam score
  * *   * *
```

---

## Pearson Correlation Coefficient

The **most common** correlation measure for two continuous, normally distributed variables.

### Formula

```
          Cov(X, Y)        Σ(Xᵢ - X̄)(Yᵢ - Ȳ)
r = ─────────────────── = ─────────────────────────────
         σₓ · σᵧ          √Σ(Xᵢ-X̄)² · √Σ(Yᵢ-Ȳ)²
```

### Properties
- Measures **linear** relationships only
- Assumes both variables are **normally distributed**
- Sensitive to **outliers**
- Value ranges from **−1 to +1**

### Worked Example (continued from above)

```
σₓ = √[ ((2-6)²+(4-6)²+(6-6)²+(8-6)²+(10-6)²) / 4 ]
   = √[ (16+4+0+4+16) / 4 ]
   = √10 ≈ 3.162

σᵧ = √[ ((50-74)²+(65-74)²+(75-74)²+(85-74)²+(95-74)²) / 4 ]
   = √[ (576+81+1+121+441) / 4 ]
   = √305 ≈ 17.46

r = Cov(X,Y) / (σₓ · σᵧ)
  = 55 / (3.162 × 17.46)
  = 55 / 55.20
  ≈ 0.996  ← Very strong positive correlation ✓
```

---

## Spearman Rank Correlation

Used when data is **ordinal**, **non-normal**, or contains **outliers**. Works on the **ranks** of data rather than actual values.

### Formula

```
         6 · Σdᵢ²
rₛ = 1 - ────────────
          n(n² - 1)
```

Where:
- `dᵢ` = difference between the ranks of each pair
- `n`  = number of observations

### When to Use Spearman over Pearson

| Situation | Use |
|-----------|-----|
| Data is normally distributed, continuous | Pearson |
| Data is ordinal (rankings, ratings) | Spearman |
| Data has outliers | Spearman |
| Non-linear but monotonic relationship | Spearman |
| Small sample size with unknown distribution | Spearman |

### Worked Example

| Student | Hours (X) | Rank X | Score (Y) | Rank Y | d = Rₓ-Rᵧ | d² |
|---------|-----------|--------|-----------|--------|------------|-----|
| A       | 2         | 1      | 50        | 1      | 0          | 0   |
| B       | 4         | 2      | 65        | 2      | 0          | 0   |
| C       | 6         | 3      | 75        | 3      | 0          | 0   |
| D       | 8         | 4      | 85        | 4      | 0          | 0   |
| E       | 10        | 5      | 95        | 5      | 0          | 0   |

```
Σd² = 0

rₛ = 1 - (6 × 0) / (5 × (25 - 1))
   = 1 - 0 / 120
   = 1.0   ← Perfect monotonic relationship
```


### Comparison of Correlation Methods

| Method | Data Type | Handles Outliers | Relationship Type |
|--------|-----------|-----------------|-------------------|
| **Pearson** | Continuous, normal | ❌ Sensitive | Linear only |
| **Spearman** | Ordinal / any | ✅ Robust | Monotonic |

---

## Common Mistakes

| Mistake | Truth |
|---------|-------|
| **"Correlation implies causation"** | ❌ Correlation only shows association, not cause and effect |
| **"r = 0 means no relationship"** | ❌ It means no *linear* relationship — a curved relationship may still exist |
| **"Covariance shows strength"** | ❌ Covariance only shows direction; magnitude depends on units |
| **"Pearson works for all data"** | ❌ Only valid for linear relationships and normally distributed data |
| **"High correlation = important feature"** | ❌ A feature highly correlated with another may be redundant (multicollinearity) |

---

## Applications in Machine Learning

| ML Task | How Covariance/Correlation Helps |
|---------|----------------------------------|
| **Feature Selection** | Remove highly correlated features to reduce redundancy |
| **Multicollinearity Detection** | Identify predictors that are too closely related in regression |
| **PCA (Dimensionality Reduction)** | Uses the covariance matrix to find principal components |
| **Anomaly Detection** | Unusual correlation patterns can signal outliers |
| **Data Preprocessing** | Understand data structure before model training |
| **Recommendation Systems** | Find users/items with similar behavior patterns |

---


## Formulas Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  COVARIANCE & CORRELATION — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  COVARIANCE
  Population:   Cov(X,Y) = Σ(Xᵢ-μₓ)(Yᵢ-μᵧ) / N
  Sample:       Cov(X,Y) = Σ(Xᵢ-X̄)(Yᵢ-Ȳ)  / (n-1)
  Range:        -∞ to +∞

  PEARSON CORRELATION
  Formula:      r = Cov(X,Y) / (σₓ · σᵧ)
  Range:        -1 to +1
  Best for:     Continuous, normally distributed data

  SPEARMAN RANK CORRELATION
  Formula:      rₛ = 1 - (6·Σd²) / (n(n²-1))
  Range:        -1 to +1
  Best for:     Ordinal data, outliers, non-normal data

  KENDALL TAU
  Formula:      τ = (C - D) / (n(n-1)/2)
  Range:        -1 to +1
  Best for:     Small samples, robust to outliers

  INTERPRETATION
  |r| ≥ 0.9   →  Very Strong
  |r| ≥ 0.7   →  Strong
  |r| ≥ 0.5   →  Moderate
  |r| ≥ 0.3   →  Weak
  |r| <  0.3  →  Negligible

  KEY RULE
  Correlation ≠ Causation  ⚠️

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

*Statistics Reference Notes | Last updated: April 2026*
