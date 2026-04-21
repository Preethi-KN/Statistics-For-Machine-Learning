# 📦 Outliers, IQR & Box Plot — Statistics Notes

> Notes based on handwritten class notes covering how to find outliers,
> calculate IQR, construct a box plot using the Five Number Summary.

---

## Table of Contents

1. [What are Outliers](#1-what-are-outliers)
2. [Five Number Summary](#2-five-number-summary)
3. [How to Find Outliers](#3-how-to-find-outliers)
4. [Worked Example — Step by Step](#4-worked-example--step-by-step)
5. [Box Plot](#5-box-plot)
6. [Cheat Sheet](#7-cheat-sheet)

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

## 2. Five Number Summary

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

## 3. How to Find Outliers

### Step 1 — Find Fences

```
Lower Fence (LF)  =  Q₁  -  1.5 × IQR
Higher Fence (HF) =  Q₃  +  1.5 × IQR
```

Any value **below the Lower Fence** or **above the Higher Fence**
is considered an **outlier**.

### Step 2 — Calculate Q₁ (1st Quartile)

```
Q₁  =  (25/100)  ×  (n + 1)

→  This gives the INDEX position of Q₁ in the sorted data
→  The value at that index is Q₁
```

### Step 3 — Calculate Q₃ (3rd Quartile)

```
Q₃  =  (75/100)  ×  (n + 1)

→  This gives the INDEX position of Q₃ in the sorted data
→  The value at that index is Q₃
```

### Step 4 — Calculate IQR

```
IQR  =  Q₃  -  Q₁
```

---

## 4. Worked Example — Step by Step

### Dataset (sorted)

```
Values = 1, 1, 2, 2, 2, 3, 3, 4, 5, 5, 5, 6, 6, 6, 6, 7 ...
          ↑ sorted  ↑ low
```

Full sorted dataset (n = 19):
```
Index:  1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19
Value:  1,  1,  2,  2,  2,  3,  3,  4,  5,  5,  5,  6,  6,  6,  6,  7, ...
```

### Step 1 — Find Q₁

```
Q₁  =  (25/100)  ×  (19 + 1)
     =  0.25  ×  20
     =  5   (index position)

→  Value at index 5  =  3  ← Q₁ = 3
```

### Step 2 — Find Q₃

```
Q₃  =  (75/100)  ×  (19 + 1)
     =  0.75  ×  20
     =  15  (index position)

→  Value at index 15  =  7  ← Q₃ = 7
```

### Step 3 — Calculate IQR

```
IQR  =  Q₃  -  Q₁  =  7  -  3  =  4
```

### Step 4 — Calculate Fences

```
Lower Fence  (LF)  =  Q₁  -  1.5 × IQR
                    =  3   -  1.5 × 4
                    =  3   -  6
                    =  -3

Higher Fence (HF)  =  Q₃  +  1.5 × IQR
                    =  7   +  1.5 × 4
                    =  7   +  6
                    =  13
```

### Step 5 — Identify Outliers

```
Lower Fence  =  -3
Higher Fence =  13

From the values:
  → There is NO negative value below -3  (no lower outlier)
  → Only one value 24 is higher than 13  (24 is an OUTLIER!)

✅ Outlier detected: 24
```

### Five Number Summary (for this example)

| # | Measure | Value |
|---|---------|-------|
| ① | Minimum | 1     |
| ② | Q₁      | 3     |
| ③ | Median  | 5 (middle value) |
| ④ | Q₃      | 7     |
| ⑤ | Maximum | 9 (excluding outlier) |

---

## 5. Box Plot

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


## 6. Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  OUTLIERS & IQR — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  FIVE NUMBER SUMMARY
  ① Minimum
  ② Q₁  =  (25/100) × (n+1)  → index → value
  ③ Median = middle value
  ④ Q₃  =  (75/100) × (n+1)  → index → value
  ⑤ Maximum

  IQR
  IQR  =  Q₃  -  Q₁

  FENCES (Outlier Boundaries)
  Lower  Fence  =  Q₁  -  1.5 × IQR
  Higher Fence  =  Q₃  +  1.5 × IQR

  OUTLIER RULE
  value < Lower Fence   →  Outlier ⚠️
  value > Higher Fence  →  Outlier ⚠️

  CLASS EXAMPLE
  Q₁ = 3,  Q₃ = 7,  IQR = 4
  LF = 3  - 1.5(4) = -3   (no values below)
  HF = 7  + 1.5(4) = +13  (value 24 is outlier!)

  BOX PLOT STRUCTURE
  Min──[Q₁═══Median═══Q₃]──Max   *Outlier

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Further Reading

- 🌐 [Outliers in Statistics — GeeksforGeeks](https://www.geeksforgeeks.org/machine-learning/detect-and-remove-the-outliers-using-python/)
- 🌐 [Box Plot — GeeksforGeeks](https://www.geeksforgeeks.org/box-plot/)
- 🌐 [IQR — GeeksforGeeks](https://www.geeksforgeeks.org/interquartile-range/)

---

*Class Notes — Outliers, IQR & Box Plot | April 2026*
