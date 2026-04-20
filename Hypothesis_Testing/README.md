# Hypothesis Testing

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

## T Test

## What is a T-Test

The **T-Test** is a statistical hypothesis test used to determine whether
there is a **significant difference between the means** of one or two groups.

> It is used when:
> - The **sample size is small** (n < 30)
> - The **population standard deviation is unknown**
> - The data follows a **normal distribution**

The test compares the **sample mean** to a known value or another sample mean
and tells us whether any observed difference is **real** or just due to
**random chance**.

---

## When to Use T-Test

| Condition | Details |
|-----------|---------|
| **Sample size** | Small (n < 30) — use Z-test for n ≥ 30 |
| **Population σ** | Unknown |
| **Data type** | Continuous (interval or ratio) |
| **Distribution** | Approximately normal |
| **Parametric?** | ✅ Yes — assumes normality |

---

## Types of T-Test

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

---

## T-Test Formula

### One-Sample T-Test

```
      X̄  -  μ₀
t =  ──────────
      s / √n

Where:
  X̄   = sample mean
  μ₀  = known/hypothesized population mean
  s   = sample standard deviation
  n   = sample size
```

### Independent Two-Sample T-Test

```
        X̄₁  -  X̄₂
t =  ─────────────────────
      √( s₁²/n₁ + s₂²/n₂ )

Where:
  X̄₁, X̄₂  = means of group 1 and group 2
  s₁², s₂² = variances of group 1 and group 2
  n₁, n₂   = sample sizes
```

### Paired T-Test

```
       d̄
t =  ──────
      sd/√n

Where:
  d̄   = mean of the differences (after - before)
  sd  = standard deviation of the differences
  n   = number of pairs
```

### Degrees of Freedom

```
One-Sample / Paired :  df = n - 1
Two-Sample          :  df = n₁ + n₂ - 2
```

---

## Worked Example — One Sample T-Test

### Problem Statement

A school claims the **average exam score** of students is **75**.
A teacher randomly selects **10 students** and records their scores.
Test whether the claim is true at **α = 0.05**.

### Student Data

| Student | Score |
|---------|-------|
| A       | 70    |
| B       | 78    |
| C       | 65    |
| D       | 80    |
| E       | 72    |
| F       | 85    |
| G       | 68    |
| H       | 74    |
| I       | 79    |
| J       | 71    |

### Step 1 — State Hypotheses

```
H₀ (Null Hypothesis)        →  μ = 75  (mean is 75 as claimed)
H₁ (Alternative Hypothesis) →  μ ≠ 75  (mean is different from 75)

Two-tailed test, α = 0.05
```

### Step 2 — Calculate Sample Statistics

```
n  = 10
ΣX = 70+78+65+80+72+85+68+74+79+71 = 742

X̄  = 742 / 10 = 74.2

Variance:
  s² = Σ(Xᵢ - X̄)² / (n-1)

  Deviations from mean (74.2):
  (70-74.2)² = 17.64
  (78-74.2)² = 14.44
  (65-74.2)² = 84.64
  (80-74.2)² = 33.64
  (72-74.2)² =  4.84
  (85-74.2)² = 116.64
  (68-74.2)² = 38.44
  (74-74.2)² =  0.04
  (79-74.2)² = 23.04
  (71-74.2)² = 10.24
              ────────
  Σ = 343.60

  s² = 343.60 / 9 = 38.18
  s  = √38.18 ≈ 6.18
```

### Step 3 — Calculate T-Statistic

```
      X̄  -  μ₀         74.2 - 75         -0.8
t =  ──────────   =   ─────────────  =  ──────── = -0.409
      s / √n           6.18 / √10        1.954
```

### Step 4 — Find Critical Value

```
df = n - 1 = 10 - 1 = 9
α  = 0.05 (two-tailed)  →  α/2 = 0.025

From t-table:
  t_critical (df=9, α/2=0.025) = ±2.262
```

### Step 5 — Decision

```
|t calculated| = 0.409
 t critical   = 2.262

  0.409 < 2.262  →  FAIL to Reject H₀ ✅
```

### Step 6 — Conclusion

> The sample mean (74.2) is **not significantly different** from the
> claimed population mean (75). The school's claim holds true at 95%
> confidence level.

---

## Worked Example — Two Sample T-Test

### Problem Statement

Two groups of students are taught using **different teaching methods**.
Test if there is a **significant difference in their scores** at α = 0.05.

| Group A (Method 1) | Group B (Method 2) |
|--------------------|--------------------|
| 78                 | 85                 |
| 72                 | 90                 |
| 80                 | 88                 |
| 65                 | 76                 |
| 74                 | 82                 |

### Calculation

```
Group A:  X̄₁ = 73.8,  s₁ = 5.89,  n₁ = 5
Group B:  X̄₂ = 84.2,  s₂ = 5.22,  n₂ = 5

H₀: μ₁ = μ₂   (no difference between methods)
H₁: μ₁ ≠ μ₂   (methods produce different results)

        X̄₁ - X̄₂           73.8 - 84.2          -10.4
t =  ─────────────────  =  ──────────────────  =  ──────  = -2.98
      √(s₁²/n₁+s₂²/n₂)    √(34.69/5+27.25/5)    3.488

df = n₁ + n₂ - 2 = 5 + 5 - 2 = 8
t_critical (df=8, α=0.05, two-tail) = ±2.306

|t| = 2.98  >  2.306  →  REJECT H₀ ✅
```

> **Conclusion:** There IS a significant difference between the two
> teaching methods. Method 2 produces significantly higher scores.

---

## Worked Example — Paired T-Test

### Problem Statement

The same 5 students are tested **before** and **after** a training program.
Check if the training made a significant improvement at α = 0.05.

| Student | Before | After | d = After-Before | d² |
|---------|--------|-------|------------------|----|
| A       | 60     | 70    | +10              | 100|
| B       | 55     | 65    | +10              | 100|
| C       | 70     | 75    | +5               | 25 |
| D       | 65     | 72    | +7               | 49 |
| E       | 58     | 68    | +10              | 100|

```
H₀: μd = 0   (no improvement)
H₁: μd > 0   (scores improved after training)

d̄  = (10+10+5+7+10) / 5 = 42/5 = 8.4

sd = √[ Σd² - n·d̄² ] / (n-1)
   = √[ 374 - 5×(8.4)² ] / 4
   = √[ 374 - 352.8 ] / 4
   = √[ 21.2/4 ]
   = √5.3 = 2.30

      d̄           8.4          8.4
t =  ──────  =  ────────  =  ──────  =  8.17
      sd/√n      2.30/√5      1.029

df = n - 1 = 4
t_critical (df=4, α=0.05, one-tail) = 2.132

t = 8.17  >  2.132  →  REJECT H₀ ✅
```

> **Conclusion:** The training program produced a **significant improvement**
> in student scores.

---

## Decision Boundary

```
          Two-Tailed Test (α = 0.05)

  Reject H₀       Accept H₀        Reject H₀
  ──────────┤──────────────────────┤──────────
           -t_c         0          +t_c
          -2.262                  +2.262
   (α/2=0.025)               (α/2=0.025)

          One-Tailed Test (α = 0.05)

       Accept H₀              Reject H₀
  ──────────────────────────┤──────────
                  0         +t_c
                           +2.132

Decision Rule:
  |t_calculated| > t_critical  →  REJECT H₀
  |t_calculated| ≤ t_critical  →  FAIL to Reject H₀

  p < α   →  REJECT H₀
  p ≥ α   →  FAIL to Reject H₀
```

---

## T-Table Reference

### Critical Values (Two-Tailed, α = 0.05)

| df | α = 0.10 | α = 0.05 | α = 0.02 | α = 0.01 |
|----|----------|----------|----------|----------|
| 1  | 6.314    | 12.706   | 31.821   | 63.657   |
| 2  | 2.920    | 4.303    | 6.965    | 9.925    |
| 3  | 2.353    | 3.182    | 4.541    | 5.841    |
| 4  | 2.132    | 2.776    | 3.747    | 4.604    |
| 5  | 2.015    | 2.571    | 3.365    | 4.032    |
| 8  | 1.860    | 2.306    | 2.896    | 3.355    |
| 9  | 1.833    | 2.262    | 2.821    | 3.250    |
| 10 | 1.812    | 2.228    | 2.764    | 3.169    |
| 20 | 1.725    | 2.086    | 2.528    | 2.845    |
| 30 | 1.697    | 2.042    | 2.457    | 2.750    |
| ∞  | 1.645    | 1.960    | 2.326    | 2.576    |

> As df → ∞, t-distribution → Normal distribution (Z-test)

---
## Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  T-TEST — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  ONE-SAMPLE        t = (X̄ - μ₀) / (s/√n)
  TWO-SAMPLE        t = (X̄₁-X̄₂) / √(s₁²/n₁ + s₂²/n₂)
  PAIRED            t = d̄ / (sd/√n)

  DEGREES OF FREEDOM
  One-Sample/Paired : df = n - 1
  Two-Sample        : df = n₁ + n₂ - 2

  DECISION RULE
  |t| > t_critical  →  Reject H₀
  |t| ≤ t_critical  →  Fail to Reject H₀

  p < α  (0.05)     →  Reject H₀  (significant)
  p ≥ α  (0.05)     →  Accept H₀  (not significant)

  ASSUMPTIONS
  1. Data is normally distributed
  2. Sample is random
  3. Observations are independent
  4. Population σ is unknown (use s instead)

  KEY CRITICAL VALUES (two-tail, α=0.05)
  df=4  →  2.776
  df=9  →  2.262
  df=29 →  2.045
  df=∞  →  1.960  (same as Z)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
---
## Chi-Square Test


## What is Chi-Square Test

The **Chi-Square Test (χ²)** is mainly used for **Inferential Statistics**.
It is used for **categorical data**, where we are checking how proportionally
(properly) spread data is in the population — both **ordinal** and **nominal** data.

> This is a **non-parametric test** (like median, mode — does not assume
> normal distribution).

---

## When to Use

| Condition | Details |
|-----------|---------|
| **Data type** | Categorical (nominal or ordinal) |
| **Purpose** | Check if observed data matches expected distribution |
| **Parametric?** | ❌ No — non-parametric test |
| **Hypotheses** | H₀ (null) vs H₁ (alternative) |

---

## Worked Example — Census Population

### Problem Statement

There is a census data from **2010** of a population distributed across
3 age groups:

| Age Group | Percentage |
|-----------|-----------|
| < 50      | 20%       |
| 50 – 70   | 30%       |
| > 70      | 50%       |

Now we are checking whether the **data from 2020** follows the same
distribution.

**Sample size: n = 500**

### Observed Data (2020)

| Age Group | Observed Count |
|-----------|---------------|
| < 50      | 120           |
| 50 – 70   | 160           |
| > 70      | 200           |
| **Total** | **500**       |

---

## Step-by-Step Solution

### Step 1 — State the Hypotheses

```
H₀ (Null Hypothesis)        → Population has NOT changed
                               (same distribution as 2010)

H₁ (Alternative Hypothesis) → Population HAS changed
                               (different from 2010 distribution)
```

### Step 2 — Set Significance Level & Degrees of Freedom

```
α (significance level) = 0.05  (5%)

Degrees of Freedom (df) = k - 1 = 3 - 1 = 2

Confidence Interval = 95%
```

### Step 3 — Calculate Expected Frequencies

Using the **2010 percentages** applied to **n = 500**:

| Age Group | Calculation        | Expected (E) |
|-----------|--------------------|--------------|
| < 50      | 20% × 500 = 0.2 × 500 | **100**  |
| 50 – 70   | 30% × 500 = 0.3 × 500 | **150**  |
| > 70      | 50% × 500 = 0.5 × 500 | **250**  |

### Step 4 — Chi-Square Formula

```
     (Observed - Expected)²
χ² = Σ ─────────────────────
            Expected
```

### Step 5 — Calculate χ² Value

```
       (140 - 100)²     (160 - 150)²     (200 - 250)²
χ² =  ─────────────  +  ─────────────  +  ─────────────
           100                150               250

       (40)²     (10)²     (-50)²
    =  ──────  + ──────  + ───────
        100       150        250

       1600      100       2500
    =  ────── + ────── + ──────
        100      150       250

    =  16  +  0.66  +  10

χ² = 26.66
```

### Step 6 — Check Critical Value (Chi-Square Table)

```
  df = 2,  α = 0.05

  ┌────┬────────┐
  │ df │  0.05  │
  ├────┼────────┤
  │  2 │  5.99  │  ← Critical Value
  └────┴────────┘

  χ² calculated = 26.66
  χ² critical   =  5.99

  Since 26.66 > 5.99  →  REJECT H₀
```

---

## Chi-Square Formula

```
         (O - E)²
χ² =  Σ  ────────
            E

Where:
  O  =  Observed frequency
  E  =  Expected frequency
  Σ  =  Sum across all categories
```

---

## Decision Boundary

```
                    Accept Region
          ┌──────────────────────────┐
          │                          │
   ───────┤──────────────────────────┼──────────────►
          0                        5.99    χ²
                                      ↑
                              α = 0.05 (2)
                                   Rejection Area →
```

**Rule:**
```
If χ² calculated  >  χ² critical  →  REJECT H₀
If χ² calculated  ≤  χ² critical  →  ACCEPT H₀
```

In our example:
```
26.66  >  5.99   →  ✅ REJECT H₀
```

---

## Conclusion

> ⑦ The Chi-Square test value **26.66 > 5.99**, so we are **rejecting
> the null hypothesis**.
>
> **There is a population difference** — and it has **increased** when
> compared to the census in 2010.

---
## Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  CHI-SQUARE TEST — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  Formula:     χ² = Σ (O - E)² / E

  df:          k - 1  (k = number of categories)

  α:           0.05  (most common significance level)

  H₀:          No difference / No change
  H₁:          Significant difference / Change exists

  Decision:
    χ² > critical value  →  Reject H₀
    χ² ≤ critical value  →  Accept H₀

    p < 0.05   →  Reject H₀  (significant)
    p ≥ 0.05   →  Accept H₀  (not significant)

  Common Critical Values:
    df=1, α=0.05  →  3.84
    df=2, α=0.05  →  5.99  ← used in class example
    df=3, α=0.05  →  7.81
    df=4, α=0.05  →  9.49

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

*Chi-Square Test | April 2026*