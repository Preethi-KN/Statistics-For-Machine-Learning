# 📦 Outliers, IQR & Box Plot — Statistics Notes

> Notes based on handwritten class notes covering how to find outliers using
> two methods (IQR and Z-Score), calculate IQR, construct a box plot using
> the Five Number Summary, and compare both methods.

---

## Table of Contents

1. [What are Outliers](#1-what-are-outliers)
2. [Two Methods to Detect Outliers](#2-two-methods-to-detect-outliers)
3. [Method 1 — IQR Method](#3-method-1--iqr-method)
4. [Method 2 — Z-Score Method](#4-method-2--z-score-method)
5. [Worked Example — IQR Method](#5-worked-example--iqr-method)
6. [Worked Example — Z-Score Method](#6-worked-example--z-score-method)
7. [Z-Score vs IQR — Comparison](#7-z-score-vs-iqr--comparison)
8. [Five Number Summary](#8-five-number-summary)
9. [Box Plot](#9-box-plot)
10. [Cheat Sheet](#11-cheat-sheet)

---

## 1. What are Outliers

An **outlier** is a data point that lies **far away** from the rest of
the dataset — either unusually high or unusually low.

```
Normal data range:
  ──────────────────────────────────────
       ●   ●  ●●● ● ●●  ●  ●
  ──────────────────────────────────────
                                      ●  ← Outlier (too far right)

  ●                                      ← Outlier (too far left)
  ──────────────────────────────────────
```

**Why outliers matter:**
- They can **skew** the mean and mislead analysis
- They may indicate **data entry errors** or **genuine anomalies**
- Must be **detected and handled** before building ML models

---

## 2. Two Methods to Detect Outliers

There are **two main statistical methods** to detect outliers:

| Method | Based On | Best For |
|--------|----------|----------|
| **IQR Method** | Quartiles (Q₁, Q₃) | Skewed data, non-normal distributions |
| **Z-Score Method** | Mean & Std Deviation | Normally distributed data, large samples |

```
Which method to use?
  Data is normally distributed  →  Use Z-Score
  Data is skewed / has extremes →  Use IQR
  Small dataset (n < 30)        →  Use IQR
  Large dataset (n ≥ 30)        →  Either works
```

---

## 3. Method 1 — IQR Method

### Definition

The **IQR (Interquartile Range) Method** detects outliers by building
**fences** around the middle 50% of data using quartiles. Any value
outside these fences is flagged as an outlier.

```
IQR  =  Q₃  -  Q₁   (the spread of the middle 50% of data)

Lower  Fence  =  Q₁  -  1.5 × IQR   ← anything below is outlier
Higher Fence  =  Q₃  +  1.5 × IQR   ← anything above is outlier
```

### Steps

**Step 1 — Sort the data**

**Step 2 — Find Q₁ (1st Quartile / 25th percentile)**
```
Q₁  =  (25/100)  ×  (n + 1)
     → gives the INDEX position → look up value at that index
```

**Step 3 — Find Q₃ (3rd Quartile / 75th percentile)**
```
Q₃  =  (75/100)  ×  (n + 1)
     → gives the INDEX position → look up value at that index
```

**Step 4 — Calculate IQR**
```
IQR  =  Q₃  -  Q₁
```

**Step 5 — Calculate Fences**
```
Lower  Fence  =  Q₁  -  1.5 × IQR
Higher Fence  =  Q₃  +  1.5 × IQR
```

**Step 6 — Flag Outliers**
```
value < Lower  Fence  →  ⚠️ Outlier
value > Higher Fence  →  ⚠️ Outlier
```

---

## 4. Method 2 — Z-Score Method

### Definition

The **Z-Score** measures how many **standard deviations** a data point
is away from the **mean**. If a value is too far from the mean (beyond
a threshold), it is considered an **outlier**.

```
        X  -  μ
Z  =  ──────────
           σ

Where:
  X  =  individual data point
  μ  =  mean of the dataset
  σ  =  standard deviation of the dataset
```

### Outlier Rule for Z-Score

```
|Z|  >  3   →  ⚠️ Outlier   (most common threshold)
|Z|  >  2   →  ⚠️ Outlier   (stricter threshold, flags more values)

In other words:
  Z < -3  OR  Z > +3  →  Outlier
```

> **Why 3?** In a normal distribution, 99.73% of data falls within ±3σ.
> Any point beyond this is extremely unlikely and likely an outlier.

```
Normal distribution:

         99.73% of data
  ├─────────────────────────────────────────┤
     95.45% of data
  ├─────────────────────────────┤
     68.27% of data
  ├─────────────┤

────────────────────────────────────────────
-3σ  -2σ  -1σ   μ   +1σ  +2σ  +3σ
↑                                       ↑
Outlier region                  Outlier region
```

### Steps

**Step 1 — Calculate the Mean (μ)**
```
μ  =  ΣX / n
```

**Step 2 — Calculate Standard Deviation (σ)**
```
σ  =  √[ Σ(Xᵢ - μ)² / n ]
```

**Step 3 — Calculate Z-Score for each value**
```
Z  =  (X - μ) / σ
```

**Step 4 — Flag Outliers**
```
|Z|  >  3   →  ⚠️ Outlier
```

---

## 5. Worked Example — IQR Method

### Dataset (sorted, n = 19)

```
Index:  1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19
Value:  1,  1,  2,  2,  2,  3,  3,  4,  5,  5,  5,  6,  6,  6,  6,  7,  8,  9,  24
```

### Step 1 — Find Q₁

```
Q₁  =  (25/100)  ×  (19 + 1)  =  0.25 × 20  =  5  (index)

Value at index 5  =  3  ← Q₁ = 3
```

### Step 2 — Find Q₃

```
Q₃  =  (75/100)  ×  (19 + 1)  =  0.75 × 20  =  15  (index)

Value at index 15  =  7  ← Q₃ = 7
```

### Step 3 — Calculate IQR

```
IQR  =  Q₃  -  Q₁  =  7  -  3  =  4
```

### Step 4 — Calculate Fences

```
Lower Fence  (LF)  =  Q₁  -  1.5 × IQR  =  3  -  1.5(4)  =  3  -  6  =  -3
Higher Fence (HF)  =  Q₃  +  1.5 × IQR  =  7  +  1.5(4)  =  7  +  6  =  +13
```

### Step 5 — Identify Outliers

```
Lower Fence  = -3   →  No values below -3   ✅ No lower outlier
Higher Fence = 13   →  Value 24 > 13        ⚠️ 24 is an OUTLIER!
```

### Five Number Summary

| # | Measure | Value |
|---|---------|-------|
| ① | Minimum | 1 |
| ② | Q₁      | 3 |
| ③ | Median  | 5 |
| ④ | Q₃      | 7 |
| ⑤ | Maximum | 9 (excluding outlier 24) |

---

## 6. Worked Example — Z-Score Method

### Same Dataset

```
Data = [1, 1, 2, 2, 2, 3, 3, 4, 5, 5, 5, 6, 6, 6, 6, 7, 8, 9, 24]
n    = 19
```

### Step 1 — Calculate Mean

```
μ  =  ΣX / n
   =  (1+1+2+2+2+3+3+4+5+5+5+6+6+6+6+7+8+9+24) / 19
   =  105 / 19
   ≈  5.53
```

### Step 2 — Calculate Standard Deviation

```
σ  =  √[ Σ(Xᵢ - μ)² / n ]  ≈  4.87
```

### Step 3 — Calculate Z-Scores for Each Value

| Value (X) | Z = (X − 5.53) / 4.87 | \|Z\| > 3? | Outlier? |
|-----------|------------------------|------------|----------|
| 1         | (1 − 5.53) / 4.87  = **−0.93** | No  | ❌ No  |
| 2         | (2 − 5.53) / 4.87  = **−0.72** | No  | ❌ No  |
| 3         | (3 − 5.53) / 4.87  = **−0.52** | No  | ❌ No  |
| 4         | (4 − 5.53) / 4.87  = **−0.31** | No  | ❌ No  |
| 5         | (5 − 5.53) / 4.87  = **−0.11** | No  | ❌ No  |
| 6         | (6 − 5.53) / 4.87  = **+0.10** | No  | ❌ No  |
| 7         | (7 − 5.53) / 4.87  = **+0.30** | No  | ❌ No  |
| 8         | (8 − 5.53) / 4.87  = **+0.51** | No  | ❌ No  |
| 9         | (9 − 5.53) / 4.87  = **+0.71** | No  | ❌ No  |
| **24**    | (24 − 5.53) / 4.87 = **+3.79** | **Yes** | ⚠️ **OUTLIER!** |

### Step 4 — Conclusion

```
Threshold  =  |Z| > 3

Z-score of 24  =  +3.79

|3.79|  >  3   →  ⚠️ 24 IS an OUTLIER!

Both IQR and Z-Score methods agree: 24 is an outlier ✅
```

---

## 7. Z-Score vs IQR — Comparison

| Feature | Z-Score Method | IQR Method |
|---------|---------------|------------|
| **Based on** | Mean (μ) and Std Dev (σ) | Quartiles (Q₁, Q₃) |
| **Threshold** | \|Z\| > 3 (or 2) | Outside LF / HF fences |
| **Assumes normality** | ✅ Yes | ❌ No |
| **Sensitive to outliers** | ✅ Yes — mean & σ get pulled | ❌ No — quartiles are robust |
| **Best for** | Large samples, normal distribution | Skewed data, small samples |
| **Affected by extreme values** | ✅ Yes | ❌ No |
| **Gives distance info** | ✅ Yes — exact σ distance | ❌ No — only inside/outside fence |
| **Common use** | ML preprocessing, finance | EDA, box plots |

### When to Choose Which

```
Use Z-Score when:
  ✅ Data is approximately normally distributed
  ✅ Large dataset (n > 30)
  ✅ You need to know HOW FAR outlier is from mean
  ✅ ML model preprocessing

Use IQR when:
  ✅ Data is skewed or heavily tailed
  ✅ Small dataset (n < 30)
  ✅ Robust method not affected by extremes needed
  ✅ Box plot visualization required
  ✅ Quick EDA (Exploratory Data Analysis)
```

### Key Insight

```
⚠️ Important Limitation of Z-Score:

When an outlier is present in the data, it INFLATES both the
mean (μ) and standard deviation (σ), which makes the Z-Score
of that same outlier appear SMALLER than it really is.

Example:
  Data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 24]

  With 24 in data:
    μ = 6.9,  σ = 5.93
    Z(24) = (24 - 6.9) / 5.93 = +2.88  → NOT flagged at threshold 3!

  Without 24:
    μ = 5.0,  σ = 2.74
    Z(24) = (24 - 5.0) / 2.74 = +6.93  → Clearly an outlier!

→ IQR is IMMUNE to this — Q₁ and Q₃ are not affected by 24
→ IQR is the SAFER DEFAULT CHOICE for outlier detection
```

---

## 8. Five Number Summary

To construct a **Box Plot**, we need the **Five Number Summary**:

| # | Name | Description |
|---|------|-------------|
| ① | **Minimum** | Smallest value in the dataset |
| ② | **Q₁ (1st Quartile)** | 25th percentile — lower quartile |
| ③ | **Median** | 50th percentile — middle value |
| ④ | **Q₃ (3rd Quartile)** | 75th percentile — upper quartile |
| ⑤ | **Maximum** | Largest value in the dataset |

```
Five Number Summary forms the Box Plot:

  Min    Q₁    Median    Q₃    Max
   |──────[════════|════════]──────|
         ↑                 ↑
      25th %ile         75th %ile
```

---

## 9. Box Plot

A **Box Plot** (also called Box-and-Whisker plot) visually displays the
Five Number Summary and helps spot outliers easily.

### Structure of a Box Plot

```
        data to consider
        ╭───────╮
  ──────[════│════]──────    *
  ↑     ↑    ↑    ↑    ↑    ↑
 min   Q₁  Median Q₃  max  Outlier (*)

  -2   0  +2  +4  5+6  +8  +10  +12
             ↑        ↑
           Q₁(25%)  Q₃(75%)
```

### Reading a Box Plot

| Part | Description |
|------|-------------|
| **Left whisker** | Extends from Min to Q₁ |
| **Box (left half)** | Q₁ to Median (25% of data) |
| **Box (right half)** | Median to Q₃ (25% of data) |
| **Right whisker** | Extends from Q₃ to Max |
| **Dots / Stars (*)** | Outliers beyond the fences |
| **IQR** | Width of the box = Q₃ − Q₁ |

### Interpreting Box Plot Shape

```
Symmetric distribution:
  ──────[════│════]──────
        equal whiskers

Right-skewed (positive skew):
  ──[════│══════]────────────
        longer right whisker

Left-skewed (negative skew):
  ────────────[══════│════]──
        longer left whisker
```

---


## 10. Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  OUTLIERS — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  METHOD 1: IQR
  IQR          =  Q₃  -  Q₁
  Lower  Fence =  Q₁  -  1.5 × IQR
  Higher Fence =  Q₃  +  1.5 × IQR
  Outlier      →  value < LF  OR  value > HF

  Q₁ index  =  (25/100) × (n+1)
  Q₃ index  =  (75/100) × (n+1)

  METHOD 2: Z-SCORE
  Z        =  (X - μ) / σ
  Outlier  →  |Z| > 3   (common threshold)
  Outlier  →  |Z| > 2   (strict threshold)

  FIVE NUMBER SUMMARY (for Box Plot)
  ① Min  ② Q₁  ③ Median  ④ Q₃  ⑤ Max

  WHEN TO USE WHICH
  Normal data, large n    →  Z-Score
  Skewed data, small n    →  IQR  (safer default)

  CLASS EXAMPLE (n=19, dataset with 24 as outlier)
  Q₁=3, Q₃=7, IQR=4
  LF = 3-6 = -3     HF = 7+6 = +13
  IQR:     24 > 13   →  ⚠️ Outlier
  Z-Score: Z(24)=+3.79 > 3  →  ⚠️ Outlier

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Further Reading

- 🌐 [Outliers in Statistics — GeeksforGeeks](https://www.geeksforgeeks.org/machine-learning/detect-and-remove-the-outliers-using-python/)
- 🌐 [Box Plot — GeeksforGeeks](https://www.geeksforgeeks.org/box-plot/)
- 🌐 [IQR — GeeksforGeeks](https://www.geeksforgeeks.org/interquartile-range/)
- 🌐 [Z-Score for Outliers — GeeksforGeeks](https://www.geeksforgeeks.org/z-score-for-outlier-detection-python/)

---

*Class Notes — Outliers, IQR & Box Plot | April 2026*
