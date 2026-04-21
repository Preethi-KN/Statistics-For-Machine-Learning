# 📊 Hypothesis Testing — Complete Statistics Notes

> A comprehensive reference guide covering all major hypothesis tests:
> Z-Test, T-Test, Chi-Square Test, and ANOVA — with theory, worked examples,
> step-by-step solutions, and Python programs.

---

## 📌 Table of Contents

1. [Hypothesis Testing — Overview](#1-hypothesis-testing--overview)
2. [Z-Test](#2-z-test)
3. [T-Test](#3-t-test)
4. [Chi-Square Test](#4-chi-square-test)
5. [ANOVA Test](#5-anova-test)
6. [Comparison of All Tests](#6-comparison-of-all-tests)
7. [Master Cheat Sheet](#7-master-cheat-sheet)

---

## 1. Hypothesis Testing — Overview

A method to compare two opposite assumptions about a population using
sample data to determine which is more likely true.

### Key Concepts

| Concept | Description |
|---------|-------------|
| **Null Hypothesis (H₀)** | Assumes no effect or relationship exists |
| **Alternative Hypothesis (H₁)** | Suggests an effect or relationship does exist |
| **Type I Error (α)** | Rejecting a true null hypothesis (false positive) |
| **Type II Error (β)** | Failing to reject a false null hypothesis (false negative) |
| **p-Value** | Probability of obtaining observed results under H₀; small p → reject H₀ |

### Key Terms

| Term | Description |
|------|-------------|
| **Significance Level (α)** | How sure we want to be before saying the claim is false. Usually 0.05 (5%) |
| **p-value** | The chance of seeing the data if H₀ is true. If less than α → claim is probably false |
| **Test Statistic** | A number that helps decide if data supports or rejects the claim |
| **Critical Value** | The cutoff point to compare with the test statistic |
| **Degrees of Freedom** | A number that depends on data size and helps find the critical value |

### Common Tests at a Glance

| Test | Purpose |
|------|---------|
| **Z-Test** | Compare means when population std dev is known (large samples, n > 30) |
| **T-Test** | Compare means of one or two groups (small samples, n < 30) |
| **ANOVA** | Compare means across three or more groups |
| **Chi-Square Test** | Assess association between categorical variables |

### Steps of Hypothesis Testing

**Step 1 — Define Hypotheses**
- H₀ (Null): Assumes no effect or difference
- H₁ (Alternative): Assumes there is an effect or difference
- *Note: We assume data is normally distributed*

**Step 2 — Choose Significance Level**
Select α (usually 0.05) — the maximum chance we accept of wrongly rejecting H₀ (Type I error).

**Step 3 — Collect and Analyze Data**
Gather data from observations or experiments. Calculate appropriate statistics.

**Step 4 — Calculate Test Statistic**
- Z-test: Used when population variance is known and sample size is large
- T-test: Used when sample size is small or population variance is unknown
- Chi-square: Used for categorical data to compare observed vs expected counts

**Step 5 — Make a Decision**

Using Critical Value:
```
Test statistic > critical value  →  Reject H₀
Test statistic ≤ critical value  →  Fail to Reject H₀
```
Using p-value:
```
p-value ≤ α  →  Reject H₀
p-value > α  →  Fail to Reject H₀  (not proof that H₀ is true)

Example: p-value = 0.03, α = 0.05  →  0.03 < 0.05  →  Reject H₀
```

---

## 2. Z-Test

### What is Z-Test

The **Z-Test** is used in **inferential statistics** to **compare the mean
of a population and a sample**.

> It tells us whether the difference between the sample mean and the
> population mean is **statistically significant** or just due to **random chance**.

### When to Use Z-Test

| Condition | Details |
|-----------|---------|
| **Population σ known** | Standard deviation of population is known |
| **Sample size** | Large — more than 30 (n > 30) |
| **Data type** | Continuous (normally distributed) |
| **Purpose** | Compare sample mean to known population mean |

```
Use Z-Test when:
  ✅ We KNOW the std dev (σ) of the population
  ✅ Sample size is more than 30
```

### Z-Test Formula

```
         x̄  -  μ
Z  =  ────────────
         σ / √n

Where:
  x̄  =  sample mean
  μ   =  population mean (hypothesized)
  σ   =  population standard deviation
  n   =  sample size
```

### Worked Example — Height of Residents

**Problem:** The average height of all residents in a city is **168 cm**
with population std dev **σ = 3.9**. A doctor believes the mean is
different. He measured **36 individuals** and found average = **169.5 cm**.
Test at **α = 0.05**.

**Given Data:**
```
μ  =  168 cm     σ  =  3.9     n  =  36     x̄  =  169.5 cm     α  =  0.05
```

**Step 1 — State Hypotheses:**
```
H₀ : μ = 168 cm   (mean height has NOT changed)
H₁ : μ ≠ 168 cm   (mean height IS different)  → Two-tailed test
```

**Step 2 — Significance Level & CI:**
```
CI  = 0.95  →  95%
α   = 1 - CI = 0.05
α/2 = 0.025 per tail

  ┌──────────────────────────────────────────────┐
  │  2.5%   │        95%         │    2.5%       │
  │ Reject  │    Accept H₀       │    Reject     │
  └──────────────────────────────────────────────┘
  -1.96    168cm               +1.96
```

**Step 3 — Decision Boundary (Critical Z-value):**
```
Look up 0.9750 in Z-table:

  Z  │  ...  │  0.06
 ────┼───────┼────────
 1.9 │  ...  │ 0.9750   →  1.9 + 0.06 = 1.96

Critical Value = ±1.96

  If Z < -1.96            →  Reject H₀
  If Z > +1.96            →  Reject H₀
  If -1.96 ≤ Z ≤ +1.96   →  Fail to Reject H₀
```

**Step 4 — Calculate Z-statistic:**
```
       x̄  -  μ       169.5 - 168       1.5
Z  =  ──────────  =  ─────────────  =  ────  =  2.31
       σ / √n          3.9 / √36       0.65
```

**Conclusion:**
```
Z-calculated = 2.31
Z-critical   = ±1.96

|2.31| > 1.96  →  ✅ REJECT H₀
```
> **2.31 > 1.96** — we reject H₀. The sample mean (169.5 cm) is
> **significantly different** from the population mean (168 cm) at 95% CI.

### Z-Table Reading Reference

```
For 95% CI, two-tailed:
  Step 1: α/2 = 0.025  →  look up 1 - 0.025 = 0.9750
  Step 2: Find in table → row 1.9, column 0.06 → 0.9750
  Step 3: Critical Z = 1.9 + 0.06 = 1.96
```

### Z-Test Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Z-TEST — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  FORMULA        Z = (x̄ - μ) / (σ / √n)

  CRITICAL VALUES (Z-table)
  α = 0.05  two-tailed  →  ±1.96
  α = 0.05  one-tailed  →  ±1.645
  α = 0.01  two-tailed  →  ±2.576
  α = 0.01  one-tailed  →  ±2.326

  DECISION RULE
  |Z_calc| > Z_critical  →  Reject H₀
  |Z_calc| ≤ Z_critical  →  Fail to Reject H₀

  CLASS EXAMPLE:  Z = 2.31 > 1.96  →  ✅ Reject H₀
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 3. T-Test

### What is T-Test

The **T-Test** is a statistical hypothesis test used to determine whether
there is a **significant difference between the means** of one or two groups.

> Used when:
> - Sample size is **small** (n < 30)
> - Population standard deviation is **unknown**
> - Data follows a **normal distribution**

### When to Use T-Test

| Condition | Details |
|-----------|---------|
| **Sample size** | Small (n < 30) — use Z-test for n ≥ 30 |
| **Population σ** | Unknown |
| **Data type** | Continuous (interval or ratio) |
| **Distribution** | Approximately normal |
| **Parametric?** | ✅ Yes — assumes normality |

### Types of T-Test

```
T-Test
├── 1. One-Sample T-Test
│       Compare sample mean to a known population mean
│
├── 2. Independent Two-Sample T-Test
│       Compare means of two separate/unrelated groups
│
└── 3. Paired T-Test (Dependent)
        Compare means of the same group before & after
```

### T-Test Formulas

**One-Sample T-Test:**
```
      X̄  -  μ₀
t =  ──────────        df = n - 1
      s / √n
```

**Independent Two-Sample T-Test:**
```
        X̄₁  -  X̄₂
t =  ─────────────────────        df = n₁ + n₂ - 2
      √( s₁²/n₁ + s₂²/n₂ )
```

**Paired T-Test:**
```
       d̄
t =  ──────        df = n - 1
      sd/√n

Where d̄ = mean of differences (after - before)
```

### Worked Example 1 — One Sample T-Test

**Problem:** A school claims average exam score is **75**. A teacher picks
**10 students**. Test at **α = 0.05**.

| Student | A  | B  | C  | D  | E  | F  | G  | H  | I  | J  |
|---------|----|----|----|----|----|----|----|----|----|-----|
| Score   | 70 | 78 | 65 | 80 | 72 | 85 | 68 | 74 | 79 | 71 |

```
H₀ : μ = 75     H₁ : μ ≠ 75     (two-tailed, α = 0.05)

n = 10,  X̄ = 742/10 = 74.2,  s = √38.18 ≈ 6.18

      74.2 - 75       -0.8
t =  ───────────  =  ──────  =  -0.409
      6.18 / √10      1.954

df = 9  →  t_critical = ±2.262

|t| = 0.409 < 2.262  →  ❌ FAIL to Reject H₀
```
> Sample mean (74.2) is **not significantly different** from claimed mean (75).

### Worked Example 2 — Two Sample T-Test

**Problem:** Two groups taught with different methods. Test if scores differ at α = 0.05.

| Group A (Method 1) | 78 | 72 | 80 | 65 | 74 |
|--------------------|----|----|----|----|----|
| Group B (Method 2) | 85 | 90 | 88 | 76 | 82 |

```
H₀: μ₁ = μ₂     H₁: μ₁ ≠ μ₂

X̄₁ = 73.8,  X̄₂ = 84.2,  s₁ = 5.89,  s₂ = 5.22

        73.8 - 84.2
t =  ──────────────────────  =  -2.98
      √(34.69/5 + 27.25/5)

df = 8  →  t_critical = ±2.306

|t| = 2.98 > 2.306  →  ✅ REJECT H₀
```
> Method 2 produces **significantly higher** scores than Method 1.

### Worked Example 3 — Paired T-Test

**Problem:** Same 5 students tested before and after training. Check improvement at α = 0.05.

| Student | Before | After | d = After−Before | d²  |
|---------|--------|-------|------------------|-----|
| A       | 60     | 70    | +10              | 100 |
| B       | 55     | 65    | +10              | 100 |
| C       | 70     | 75    | +5               | 25  |
| D       | 65     | 72    | +7               | 49  |
| E       | 58     | 68    | +10              | 100 |

```
H₀: μd = 0     H₁: μd > 0     (one-tailed)

d̄  = 42/5 = 8.4
sd  = √5.3 = 2.30

     8.4
t = ──────  =  8.17
    2.30/√5

df = 4  →  t_critical = 2.132

t = 8.17 > 2.132  →  ✅ REJECT H₀
```
> Training program produced a **significant improvement** in scores.

### Decision Boundary

```
  Two-Tailed Test (α = 0.05)
  Reject H₀       Accept H₀        Reject H₀
  ──────────┤──────────────────────┤──────────
           -2.262        0        +2.262

  One-Tailed Test (α = 0.05)
       Accept H₀              Reject H₀
  ──────────────────────────┤──────────
                  0         +2.132
```

### T-Table Critical Values (Two-Tailed, α = 0.05)

| df | α=0.10 | α=0.05 | α=0.02 | α=0.01 |
|----|--------|--------|--------|--------|
| 1  | 6.314  | 12.706 | 31.821 | 63.657 |
| 4  | 2.132  | 2.776  | 3.747  | 4.604  |
| 5  | 2.015  | 2.571  | 3.365  | 4.032  |
| 8  | 1.860  | 2.306  | 2.896  | 3.355  |
| 9  | 1.833  | 2.262  | 2.821  | 3.250  |
| 20 | 1.725  | 2.086  | 2.528  | 2.845  |
| 30 | 1.697  | 2.042  | 2.457  | 2.750  |
| ∞  | 1.645  | 1.960  | 2.326  | 2.576  |

> As df → ∞, t-distribution → Normal distribution (same as Z-test)

### T-Test Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  T-TEST — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ONE-SAMPLE   t = (X̄ - μ₀) / (s/√n)           df = n-1
  TWO-SAMPLE   t = (X̄₁-X̄₂) / √(s₁²/n₁+s₂²/n₂)  df = n₁+n₂-2
  PAIRED       t = d̄ / (sd/√n)                 df = n-1

  DECISION RULE
  |t| > t_critical  →  Reject H₀
  p < α (0.05)      →  Reject H₀

  ASSUMPTIONS
  1. Normally distributed    2. Random sample
  3. Independent observations  4. σ unknown

  KEY VALUES (two-tail, α=0.05)
  df=4 → 2.776  |  df=9 → 2.262  |  df=∞ → 1.960
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 4. Chi-Square Test

### What is Chi-Square Test

The **Chi-Square Test (χ²)** is mainly used for **Inferential Statistics**.
Used for **categorical data**, checking how proportionally data is spread
in a population — both **ordinal** and **nominal** data.

> This is a **non-parametric test** (does not assume normal distribution).

### When to Use Chi-Square

| Condition | Details |
|-----------|---------|
| **Data type** | Categorical (nominal or ordinal) |
| **Purpose** | Check if observed data matches expected distribution |
| **Parametric?** | ❌ No — non-parametric test |
| **Hypotheses** | H₀ (null) vs H₁ (alternative) |

### Chi-Square Formula

```
         (O - E)²
χ² =  Σ  ────────
            E

Where:
  O = Observed frequency
  E = Expected frequency
  Σ = Sum across all categories
```

### Worked Example — Census Population

**Problem:** Census from **2010** shows population distribution. Check if
**2020** data (n = 500) follows the same distribution. **α = 0.05**.

**Expected (from 2010 census):**

| Age Group | % (2010) | Expected (E) = % × 500 |
|-----------|----------|------------------------|
| < 50      | 20%      | 0.2 × 500 = **100**    |
| 50 – 70   | 30%      | 0.3 × 500 = **150**    |
| > 70      | 50%      | 0.5 × 500 = **250**    |

**Observed (2020 data):**

| Age Group | Observed (O) | Expected (E) |
|-----------|-------------|--------------|
| < 50      | 120         | 100          |
| 50 – 70   | 160         | 150          |
| > 70      | 200         | 250          |

**Step 1 — Hypotheses:**
```
H₀ : Population has NOT changed  (same as 2010)
H₁ : Population HAS changed
```

**Step 2 — Significance & Degrees of Freedom:**
```
α  = 0.05
df = k - 1 = 3 - 1 = 2
CI = 95%
```

**Step 3 — Calculate χ²:**
```
       (140-100)²     (160-150)²     (200-250)²
χ² =  ──────────── + ──────────── + ────────────
           100             150            250

     1600     100     2500
   = ──── +  ──── +  ────
     100      150     250

   = 16  +  0.66  +  10

χ² = 26.66
```

**Step 4 — Critical Value (Chi-Square Table):**
```
  ┌────┬────────┐
  │ df │  0.05  │
  ├────┼────────┤
  │  2 │  5.99  │  ← Critical Value
  └────┴────────┘
```

**Step 5 — Decision:**
```
   Accept Region
────────────────────────*─────────►
0                     5.99       Rejection Area

χ² calculated = 26.66
χ² critical   = 5.99

26.66 > 5.99  →  ✅ REJECT H₀
```

**Conclusion:**
> The Chi-Square value **26.66 > 5.99** — we **reject H₀**.
> There IS a **population difference** — it has **increased** compared to 2010.

### Chi-Square Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  CHI-SQUARE TEST — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  FORMULA       χ² = Σ (O - E)² / E
  df            k - 1   (k = number of categories)

  COMMON CRITICAL VALUES
  df=1, α=0.05  →  3.84
  df=2, α=0.05  →  5.99  ← class example
  df=3, α=0.05  →  7.81
  df=4, α=0.05  →  9.49

  DECISION RULE
  χ² > critical value  →  Reject H₀
  p < 0.05             →  Reject H₀

  CLASS EXAMPLE:  26.66 > 5.99  →  ✅ Reject H₀
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 5. ANOVA Test

### What is ANOVA

**ANOVA (Analysis of Variance)** is a statistical test used to compare the
**mean (μ) of two or more groups** simultaneously using the **F-distribution**.

```
       Variance BETWEEN groups
F  =  ──────────────────────────
       Variance WITHIN groups

F large → groups differ significantly → Reject H₀
F small → groups are similar          → Fail to Reject H₀
```

### Key Terms

| Term | Definition |
|------|-----------|
| **Factor** | The variable being tested (e.g., Medication dosage) |
| **Level** | The different values/groups of the factor |
| **Between variance** | How much group means differ from the overall mean |
| **Within variance** | How much individual values vary within each group |

```
Factor  →  Medication
            ↓    ↓    ↓
Levels  →  10mg  20mg  50mg   (3 levels)
```

### Assumptions in ANOVA

| # | Assumption | Details |
|---|-----------|---------|
| 1 | **Normality** | Means (μ) of sample groups are normally distributed |
| 2 | **No Outliers** | No outliers — if they exist, remove them |
| 3 | **Homogeneity of Variance** | σ₁² = σ₂² = σ₃² (same variance across groups) |
| 4 | **Independence** | Samples are independent and random |

### Types of ANOVA

```
ANOVA
├── 1. One-Way ANOVA
│       One factor, minimum 2 levels, levels are INDEPENDENT
│       Ex: Medication → 10mg, 20mg, 50mg
│
├── 2. Repeated Measures ANOVA
│       One factor, at least 2 levels, levels are DEPENDENT
│       Ex: Running → Day1, Day2, Day3 (same subjects)
│
└── 3. Factorial ANOVA
        2 or more factors, multiple levels, can be dependent or independent
        Ex: Running (Day1/Day2/Day3) × Gender (Male/Female)
```

### Hypotheses in ANOVA

```
H₀ : μ₁ = μ₂ = μ₃ = ... = μₖ   (all group means are EQUAL)
H₁ : At least ONE mean is NOT equal to the others
```

### F-Distribution & Decision Rule

```
       MS_between      SS_between / df_between
F  =  ──────────── =  ─────────────────────────
       MS_within        SS_within  / df_within

      ╱─────────────╲
     ╱  95%  Accept  ╲
────╱──────────────────╲──────────────►
                        *  3.5546
                    Critical Value → Rejection Area

If F > Critical Value  →  REJECT H₀
If F ≤ Critical Value  →  FAIL to Reject H₀
```

### Worked Example — One Way ANOVA

**Problem:** A doctor tests a new headache medicine at **3 dosage levels:
10mg, 15mg, 25mg** on patients. **α = 0.05** — Is there a significant
difference between the 3 conditions?

**Dataset:**

| 10mg (x₁) | 15mg (x₂) | 25mg (x₃) |
|-----------|-----------|-----------|
| 9         | 7         | 4         |
| 8         | 6         | 3         |
| 7         | 6         | 2         |
| 8         | 7         | 3         |
| 8         | 8         | 4         |
| 9         | 7         | 3         |
| 8         | 6         | 2         |

```
Σx₁ = 57  →  x̄₁ ≈ 8.14
Σx₂ = 47  →  x̄₂ ≈ 6.71
Σx₃ = 21  →  x̄₃ = 3.00

N = 21  (total),  a = 3  (groups),  n = 7  (per group)
```

**Step 1 — Hypotheses:**
```
H₀ : μ₁₀ₘg = μ₁₅ₘg = μ₂₅ₘg
H₁ : At least one mean is not equal
```

**Step 2 — Significance:**
```
α = 0.05,   CI = 95%
```

**Step 3 — Degrees of Freedom:**
```
df (between) = a - 1 = 3 - 1 = 2
df (within)  = N - a = 21 - 3 = 18
df (total)   = N - 1 = 21 - 1 = 20
```

**Step 4 — F-Table Lookup:**
```
df(2, 18), α = 0.05:
┌─────┬─────┬──────────┐
│ df₁ │ df₂ │  α=0.05  │
├─────┼─────┼──────────┤
│  2  │ 18  │  3.5546  │  ← Critical Value
└─────┴─────┴──────────┘

If F > 3.5546  →  REJECT H₀
```

**Step 5 — Calculate F-Statistic:**

① SS_between:
```
              Σ(Σaₚ)²     T²
SS_between =  ──────── -  ──
                 n         N

T = 57 + 47 + 21 = 125

  57²   47²   21²    125²
= ─── + ─── + ─── -  ────
   7     7     7      21

= 464.14 + 315.57 + 63.00 - 744.05

SS_between ≈ 98.67
```

② SS_within:
```
Σy² = square EACH individual value across ALL groups, then sum:
    = (9²+8²+7²+8²+8²+9²+8²) + (7²+6²+6²+7²+8²+7²+6²) + (4²+3²+2²+3²+4²+3²+2²)
    = 417 + 319 + 57 = 793

SS_within = Σy² - Σ(Σaₚ)²/n
          = 793 - [464.14 + 315.57 + 63.00]
          = 793 - 842.71
          ≈ 10.29
```

③ F-Statistic:
```
MS_between = SS_between / df_between = 98.67 / 2  = 49.34
MS_within  = SS_within  / df_within  = 10.29 / 18 = 0.57

F = MS_between / MS_within = 49.34 / 0.57 ≈ 86.56
```

### ANOVA Summary Table

| Source   | SS      | df | MS (SS/df) | F     |
|----------|---------|----|------------|-------|
| Between  | 98.67   | 2  | 49.34      | 86.56 |
| Within   | 10.29   | 18 | 0.57       | —     |
| **Total**| **108.95** | **20** | —   | —     |

**Conclusion:**
```
F calculated = 86.56
F critical   =  3.5546

86.56 > 3.5546  →  ✅ REJECT H₀
```
> **F = 86.56 > 3.55** — we **reject H₀**. There IS a **significant
> difference** in headache relief between the 3 dosage levels.
> Medication dosage **does** significantly affect patient outcomes.

### ANOVA Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ANOVA — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  F FORMULA      F = MS_between / MS_within

  SS BETWEEN     Σ(Σaₚ)²/n  -  T²/N
  SS WITHIN      Σy²  -  Σ(Σaₚ)²/n
                 ← Σy² = ALL individual values squared

  DEGREES OF FREEDOM
  df_between = a - 1       (a = number of groups)
  df_within  = N - a       (N = total data points)
  df_total   = N - 1

  HYPOTHESES
  H₀ : μ₁ = μ₂ = ... = μₖ   (all means equal)
  H₁ : At least one μ is different

  DECISION RULE
  F > F_critical  →  Reject H₀
  p < α (0.05)    →  Reject H₀

  TYPES
  One-Way           →  1 factor, independent levels
  Repeated Measures →  1 factor, dependent levels
  Factorial         →  2+ factors, multiple levels

  ASSUMPTIONS
  1. Normality   2. No outliers
  3. Equal variance (σ₁²=σ₂²=σ₃²)   4. Independence

  CLASS EXAMPLE:  F = 86.56 > 3.5546  →  ✅ Reject H₀
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 6. Comparison of All Tests

| Feature | Z-Test | T-Test | Chi-Square | ANOVA |
|---------|--------|--------|------------|-------|
| **Data type** | Continuous | Continuous | Categorical | Continuous |
| **Sample size** | n > 30 | n < 30 | Any | Any |
| **Population σ** | ✅ Known | ❌ Unknown | N/A | N/A |
| **Groups compared** | 1 vs population | 1 or 2 | Frequencies | 3+ groups |
| **Distribution** | Normal (Z) | t-distribution | χ² | F-distribution |
| **Parametric** | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes |
| **Test statistic** | Z | t | χ² | F |
| **Critical value (α=0.05, two-tail)** | ±1.96 | Depends on df | Depends on df | Depends on df |

---

## 7. Master Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  HYPOTHESIS TESTING — MASTER QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  UNIVERSAL DECISION RULE
  Test Statistic > Critical Value  →  Reject H₀
  p-value < α                      →  Reject H₀

  ┌─────────────┬──────────────────────────────────────┐
  │   Z-TEST    │  Z = (x̄ - μ) / (σ/√n)               │
  │             │  Critical: ±1.96  (α=0.05, two-tail) │
  ├─────────────┼──────────────────────────────────────┤
  │  T-TEST     │  One:    t = (X̄-μ₀)/(s/√n)   df=n-1 │
  │             │  Two:    t = (X̄₁-X̄₂)/SE    df=n₁+n₂-2│
  │             │  Paired: t = d̄/(sd/√n)       df=n-1  │
  ├─────────────┼──────────────────────────────────────┤
  │ CHI-SQUARE  │  χ² = Σ(O-E)²/E              df=k-1  │
  ├─────────────┼──────────────────────────────────────┤
  │   ANOVA     │  F = MS_between / MS_within           │
  │             │  df_between=a-1, df_within=N-a        │
  └─────────────┴──────────────────────────────────────┘

  ERRORS
  Type I  (α) :  Reject H₀ when TRUE   → false positive
  Type II (β) :  Accept H₀ when FALSE  → false negative

  CONFIDENCE INTERVAL
  CI = 1 - α     →   95% CI means α = 0.05
  α/2 per tail for two-tailed tests

  CLASS EXAMPLES
  Z-Test      : Z=2.31 > 1.96        →  ✅ Reject H₀
  T-Test      : t=8.17 > 2.132       →  ✅ Reject H₀
  Chi-Square  : χ²=26.66 > 5.99      →  ✅ Reject H₀
  ANOVA       : F=86.56 > 3.5546     →  ✅ Reject H₀

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Further Reading

- 🌐 [Hypothesis Testing — GeeksforGeeks](https://www.geeksforgeeks.org/software-testing/understanding-hypothesis-testing/)
- 🌐 [Z-Test — GeeksforGeeks](https://www.geeksforgeeks.org/maths/z-test/)
- 🌐 [T-Test — GeeksforGeeks](https://www.geeksforgeeks.org/maths/t-test/)
- 🌐 [Chi-Square Test — GeeksforGeeks](https://www.geeksforgeeks.org/maths/chi-square-test/)
- 🌐 [ANOVA Test — GeeksforGeeks](https://www.geeksforgeeks.org/maths/anova-test/)

---

*Class Notes — Hypothesis Testing | April 2026*
