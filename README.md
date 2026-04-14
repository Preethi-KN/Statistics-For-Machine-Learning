# 📊 Normal Distribution — Statistics Notes

> A comprehensive reference guide for understanding the Normal (Gaussian) Distribution.

---

## Table of Contents

1. [Definition](#definition)
2. [Key Properties](#key-properties)
3. [Probability Density Function (PDF)](#probability-density-function-pdf)
4. [Cumulative Distribution Function (CDF)](#cumulative-distribution-function-cdf)
5. [Standard Normal Distribution](#standard-normal-distribution)
6. [Z-Score](#z-score)
7. [The Empirical Rule (68-95-99.7 Rule)](#the-empirical-rule-68-95-997-rule)
8. [Parameters](#parameters)
9. [Mean, Median, Mode](#mean-median-mode)
10. [Variance and Standard Deviation](#variance-and-standard-deviation)
11. [Skewness and Kurtosis](#skewness-and-kurtosis)
12. [Moment Generating Function](#moment-generating-function)
13. [Linear Combinations](#linear-combinations)
14. [Central Limit Theorem (CLT)](#central-limit-theorem-clt)
15. [Common Applications](#common-applications)
16. [Key Probability Values (Z-Table Reference)](#key-probability-values-z-table-reference)
17. [Formulas Cheat Sheet](#formulas-cheat-sheet)

---

## Definition

The **Normal Distribution** (also called the **Gaussian Distribution**) is a continuous probability distribution that is symmetric about its mean, showing that data near the mean are more frequent in occurrence than data far from the mean.

It is the most important distribution in statistics due to the **Central Limit Theorem**.

---

## Key Properties

- **Symmetric** about the mean `μ`
- **Bell-shaped** curve
- **Unimodal** — has exactly one peak
- The total area under the curve equals **1**
- The curve approaches but **never touches** the x-axis (asymptotic tails)
- Defined on the interval `(-∞, +∞)`
- Completely described by just **two parameters**: `μ` (mean) and `σ²` (variance)

---

## Probability Density Function (PDF)

The PDF of a normal distribution is:

```
         1                (x - μ)²
f(x) = ────── · exp( - ─────────── )
       σ√(2π)              2σ²
```

Where:
- `μ` = mean (location parameter)
- `σ` = standard deviation (scale parameter)
- `σ²` = variance
- `π ≈ 3.14159`
- `e ≈ 2.71828`

**Notation:** `X ~ N(μ, σ²)`

---

## Cumulative Distribution Function (CDF)

The CDF gives the probability that X takes a value ≤ x:

```
         x
         ⌠    1                (t - μ)²
F(x) =   │  ────── · exp( - ─────────── ) dt
         ⌡   σ√(2π)              2σ²
        -∞
```

The CDF has **no closed-form solution** and is typically evaluated using:
- **Z-tables** (standard normal table)
- **Statistical software** (Python, R, Excel)
- **Error function (erf)**:

```
F(x) = (1/2) · [1 + erf( (x - μ) / (σ√2) )]
```

---

## Standard Normal Distribution

When `μ = 0` and `σ = 1`, we get the **Standard Normal Distribution**:

```
         1           z²
φ(z) = ───── · exp(- ── )
       √(2π)          2
```

**Notation:** `Z ~ N(0, 1)`

The CDF of the standard normal is denoted `Φ(z)`.

**Key standard normal values:**

| z     | Φ(z)   |
|-------|--------|
| -3.00 | 0.0013 |
| -2.00 | 0.0228 |
| -1.00 | 0.1587 |
|  0.00 | 0.5000 |
| +1.00 | 0.8413 |
| +2.00 | 0.9772 |
| +3.00 | 0.9987 |

---

## Z-Score

The **Z-score** standardizes any normal variable X into a standard normal variable Z:

```
    X - μ
Z = ─────
      σ
```

**Interpretation:**
- Z = 0 → value equals the mean
- Z = +1 → value is 1 standard deviation **above** the mean
- Z = −1 → value is 1 standard deviation **below** the mean

**Use Case:** To find `P(a ≤ X ≤ b)`:

```
P(a ≤ X ≤ b) = Φ( (b - μ)/σ ) - Φ( (a - μ)/σ )
```

---

## The Empirical Rule (68-95-99.7 Rule)

For a normal distribution `N(μ, σ²)`:

```
 ┌─────────────────────────────────────────────────────┐
 │  P(μ - σ  < X < μ + σ)  ≈ 68.27%  (within 1σ)     │
 │  P(μ - 2σ < X < μ + 2σ) ≈ 95.45%  (within 2σ)     │
 │  P(μ - 3σ < X < μ + 3σ) ≈ 99.73%  (within 3σ)     │
 └─────────────────────────────────────────────────────┘
```

Visual representation:

```
          68.27%
       ┌──────────┐
          95.45%
       ┌──────────────────┐
              99.73%
       ┌──────────────────────────┐

  ─────|────|────|────|────|────|─────
     -3σ  -2σ  -1σ   μ  +1σ  +2σ  +3σ
```

---

## Parameters

| Parameter | Symbol | Role | Effect on curve |
|-----------|--------|------|-----------------|
| Mean | `μ` | Location | Shifts curve left/right |
| Variance | `σ²` | Spread | Wider (`σ²↑`) or narrower (`σ²↓`) |
| Std Dev | `σ` | Spread | Same as variance but in original units |

---

## Mean, Median, Mode

For a normal distribution, all three measures of central tendency are **equal**:

```
Mean = Median = Mode = μ
```

This is a direct consequence of the distribution's perfect symmetry.

---

## Variance and Standard Deviation

| Measure | Formula | Notes |
|---------|---------|-------|
| Variance | `Var(X) = σ²` | Second central moment |
| Std Deviation | `SD(X) = σ` | Square root of variance |
| Mean Absolute Deviation | `MAD = σ√(2/π) ≈ 0.798σ` | Average absolute deviation from mean |

---

## Skewness and Kurtosis

| Measure | Value | Meaning |
|---------|-------|---------|
| **Skewness** | `0` | Perfectly symmetric |
| **Excess Kurtosis** | `0` | Mesokurtic (baseline reference) |
| **Kurtosis** | `3` | Raw kurtosis value |

> The normal distribution is the **reference distribution** for kurtosis. Distributions with kurtosis > 3 are **leptokurtic** (heavier tails); < 3 are **platykurtic** (lighter tails).

---

## Moment Generating Function

The MGF of `X ~ N(μ, σ²)` is:

```
M_X(t) = E[e^(tX)] = exp( μt + σ²t²/2 )
```

**Moments derived from the MGF:**
- `E[X] = μ`
- `E[X²] = μ² + σ²`
- `Var(X) = σ²`

---

## Linear Combinations

If `X ~ N(μ_X, σ²_X)` and `Y ~ N(μ_Y, σ²_Y)` are **independent**, then:

```
aX + bY ~ N( aμ_X + bμ_Y,  a²σ²_X + b²σ²_Y )
```

**Special cases:**

| Combination | Result |
|-------------|--------|
| `aX + b` | `N(aμ + b, a²σ²)` |
| `X + Y` | `N(μ_X + μ_Y, σ²_X + σ²_Y)` |
| `X - Y` | `N(μ_X - μ_Y, σ²_X + σ²_Y)` |
| `X̄` (sample mean, n obs.) | `N(μ, σ²/n)` |

> **Note:** The normal distribution is **closed under linear transformations**.

---

## Central Limit Theorem (CLT)

> **Theorem:** Let `X₁, X₂, ..., Xₙ` be i.i.d. random variables with mean `μ` and finite variance `σ²`. As `n → ∞`:

```
     X̄ - μ
Z = ──────── → N(0, 1)   (in distribution)
     σ/√n
```

**Implications:**
- The sample mean `X̄` is approximately normal for large `n`, **regardless** of the original distribution
- Rule of thumb: `n ≥ 30` is usually sufficient
- This is why the normal distribution appears so widely in nature and statistics

---

## Common Applications

| Field | Application |
|-------|-------------|
| 📐 Engineering | Measurement errors, tolerances |
| 🧬 Biology | Heights, weights, blood pressure |
| 💰 Finance | Asset returns (approximately), risk models |
| 🧪 Quality Control | Process variation (Six Sigma) |
| 📡 Signal Processing | Gaussian noise |
| 📊 Hypothesis Testing | Z-tests, t-tests (via CLT) |
| 🎓 Education | Standardized test scores (SAT, IQ) |
| 🏭 Manufacturing | Dimensional tolerances |

---

## Key Probability Values (Z-Table Reference)

### One-Tailed Probabilities `P(Z ≤ z)`

| z    | 0.00   | 0.01   | 0.02   | 0.03   |
|------|--------|--------|--------|--------|
| 0.0  | 0.5000 | 0.5040 | 0.5080 | 0.5120 |
| 0.5  | 0.6915 | 0.6950 | 0.6985 | 0.7019 |
| 1.0  | 0.8413 | 0.8438 | 0.8461 | 0.8485 |
| 1.5  | 0.9332 | 0.9345 | 0.9357 | 0.9370 |
| 2.0  | 0.9772 | 0.9778 | 0.9783 | 0.9788 |
| 2.5  | 0.9938 | 0.9940 | 0.9941 | 0.9943 |
| 3.0  | 0.9987 | 0.9987 | 0.9987 | 0.9988 |

### Critical Z-Values for Confidence Intervals

| Confidence Level | α     | α/2   | z_{α/2} |
|-----------------|-------|-------|---------|
| 90%             | 0.10  | 0.05  | 1.645   |
| 95%             | 0.05  | 0.025 | 1.960   |
| 99%             | 0.01  | 0.005 | 2.576   |
| 99.9%           | 0.001 | 0.0005| 3.291   |

---

## Formulas Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  NORMAL DISTRIBUTION — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  Notation:       X ~ N(μ, σ²)

  PDF:            f(x) = (1/σ√2π) · e^[-(x-μ)²/2σ²]

  Z-score:        Z = (X - μ) / σ

  Mean:           E[X] = μ

  Variance:       Var(X) = σ²

  Skewness:       0

  Kurtosis:       3  (excess kurtosis = 0)

  MGF:            M(t) = exp(μt + σ²t²/2)

  Empirical Rule: ±1σ → 68.27%
                  ±2σ → 95.45%
                  ±3σ → 99.73%

  CLT:            X̄ ~ N(μ, σ²/n)  for large n

  Symmetry:       P(X > μ + k) = P(X < μ - k)

  Complement:     P(Z > z) = 1 - Φ(z)

  Two-tail:       P(|Z| > z) = 2(1 - Φ(z))

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Further Reading

- 📖 *Introduction to Probability and Statistics* — Mendenhall, Beaver & Beaver
- 📖 *Probability and Statistics for Engineers and Scientists* — Walpole et al.
- 📖 *The Elements of Statistical Learning* — Hastie, Tibshirani & Friedman
- 🌐 [NIST/SEMATECH e-Handbook of Statistical Methods](https://www.itl.nist.gov/div898/handbook/)
- 🌐 [Khan Academy — Normal Distribution](https://www.khanacademy.org/math/statistics-probability)

---

*Last updated: April 2026 | Statistics Reference Notes*
