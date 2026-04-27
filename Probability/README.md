# 🎲 Probability — Statistics Notes

> Notes based on handwritten class notes covering Probability fundamentals,
> Types of Data, Fundamental Rules, Conditional Probability, and Bayes' Theorem
> with worked examples.

---

## Table of Contents

1. [What is Probability](#1-what-is-probability)
2. [Types of Data](#2-types-of-data)
3. [Key Terms](#3-key-terms)
4. [Fundamental Rules of Probability](#4-fundamental-rules-of-probability)
5. [Conditional Probability](#5-conditional-probability)
6. [Bayes Theorem](#6-bayes-theorem)
7. [Cheat Sheet](#8-cheat-sheet)

---

## 1. What is Probability

**ML** involves building mathematical functions (models) to **predict**
the result based on data. Two core tools used are:

- → **Conditional Probability**
- → **Bayes' Theorem**

So they use **Statistics & Probability** together.

| Tool | Purpose |
|------|---------|
| **Probability** | Deals with uncertain data |
| **Statistics** | Helps to summarize and analyse data |

**Real-world Examples:**
- Finding dates of spam emails
- Weather prediction

### Definition

> **Probability** = Measure of how likely an event occurs

```
                  No. of event outcomes
P(Event)  =  ──────────────────────────────
               Total number of outcomes
```

### Basic Example — Dice Rolling

```
Favourable outcomes for "even" number → {2, 4, 6}
Total outcomes → {1, 2, 3, 4, 5, 6}

P(even) = 3/6 = 1/2
```

---

## 2. Types of Data

```
Data
├── Categorical Data  →  Data divided into categories or groups
│                        Ex: Gender, Color, Grade
│
└── Numerical Data    →  Data in the form of numbers
    ├── Discrete      →  Whole number data
    │                    Ex: Total number of students
    │
    └── Continuous    →  Floating number data
                         Ex: Height of a student (5.7 ft)
```

---

## 3. Key Terms

| Term | Definition | Example |
|------|-----------|---------|
| **Sample Space (S)** | All possible outcomes | S = {1, 2, 3, 4, 5, 6} for a die |
| **Event Space** | Subset of the sample space | {2, 4, 6} for even numbers |
| **Event A** | A specific outcome we are interested in | Rolling an even number |
| **P(A)** | Probability of event A occurring | P(even) = 3/6 = 1/2 |

```
Sample Space (S) = All possible outcomes = {1, 2, 3, 4, 5, 6}

Event Space     = Subset of sample space = {2, 4, 6}
```

---

## 4. Fundamental Rules of Probability

### ① Addition Rule

Used when we want the probability of **either event A or event B** occurring.

```
P(A ∪ B)  =  P(A) + P(B) − P(A ∩ B)
```

```
Venn Diagram:

    ╭───────╮ ╭───────╮
    │  P(A) │▓│ P(B)  │
    │       │▓│       │
    ╰───────╯ ╰───────╯
             ↑
           P(A∩B)
           (subtract to avoid double counting)
```

**Example — Dice rolled, what is P(even number OR number greater than 4)?**

```
① Even numbers     → {2, 4, 6}    P(E₁) = 3/6 = 1/2
② Numbers > 4      → {5, 6}       P(E₂) = 2/6 = 1/3
③ Both (even AND >4) → {6}        P(A∩B) = 1/6   ← because 6 is in both

P(A∪B) = 1/2 + 1/3 − 1/6
        = 3/6 + 2/6 − 1/6
        = 4/6
        = 2/3
```

---

### ② Multiplication Rule

Used when we want the probability of **both event A AND event B** occurring.

```
P(A ∩ B)  =  P(A)  ×  P(B|A)
                          ↑
               Probability of B happening
               when A has already happened
```

**Example — A deck of cards. What is the probability of drawing 2 Aces consecutively WITHOUT replacement?**

```
Event A → P(Ace) = 4/52   (no. of Aces in a full deck)

Event B|A → Second card is an Ace given first was Ace
          P(B|A) = 3/51   (only 3 Aces left, only 51 cards left)

P(A ∩ B) = 4/52 × 3/51
          = 12/2652
```

---

### ③ Complement Rule

Used when it is easier to calculate what does **NOT** happen.

```
P(A')  =  1  −  P(A)

Where A' = complement of A (event A does NOT occur)
```

**Example — A coin is flipped twice. What is the probability of getting at least one head?**

```
Event A  → No heads → {Tail, Tail}
P(Event A) = 1/2 × 1/2 = 1/4   (probability of NO head)

Event A' → At least 1 head → could be HT, TH, or HH
P(Event A') = 1 − P(Event A)
            = 1 − 1/4
            = 3/4
```

---

## 5. Conditional Probability

### What is Conditional Probability

**Conditional Probability** = Probability of event A occurring
**given** that event B has already occurred.

```
P(A|B)  =  P(A ∩ B)        where P(B) > 0
           ───────────
              P(B)
```

```
Venn Diagram:

  Event A ←──●────────→ Event B
              ↑
            A ∩ B
          (already happened)
```

> **Conditional probability allows us to redefine probability
> based on new information.**

### Why Use Conditional Probability

When there are **few conditions** we are applying, we use more different
results from prior probability:

1. We have some **initial probability** which we are using to get new result
2. → **Naive Bayes** classifier → uses conditional base probability

### Worked Example — Red Balls

**Problem:** A bag has **3 red balls** and **some blue balls**. One ball is
drawn and **not replaced**, another is drawn. What is the probability the
second ball is red **given** the first ball is also red?

```
Event A    → First ball is red:   P(A)   = 3/5
Event B|A  → Second ball is red given first was red:
             P(B|A) = 2/4         (only 2 red left, 4 balls total)

Event A∩B  → "First ball red AND second ball also red"
P(A ∩ B)  = 3/5 × 2/4 = 6/20

P(B|A) = P(A∩B) / P(A)
       = (6/20) / (3/5)
       = (6/20) × (5/3)
       = 30/60
       = 1/2
```

---

## 6. Bayes' Theorem

### What is Bayes' Theorem

**Bayes' Theorem** is a formula to find the probability of event A
given event B — using **prior knowledge** and **new evidence**.

```
              P(A) × P(B|A)
P(A|B)  =  ─────────────────
                 P(B)

Where:
  P(A|B)  =  Posterior  — probability of A given B
  P(B|A)  =  Likelihood — probability of B given A
  P(A)    =  Prior      — initial probability of A
  P(B)    =  Evidence   — total probability of B
```

### Example — Spam Email Filter

**Problem Setup:**
```
Event A → Email is Spam
Event B → Email contains the word "cash price"

Given an email containing the word "cash price",
calculate the probability that the email is actually spam.
```

**Data (tree diagram):**
```
                    10k emails
                   /          \
              100 spam       9900 not spam
              /    \           /         \
            90      10        50         9850
         "cash    don't    have         don't have
          price"  have    "cash          "cash
                "cash     price"         price"
                 price"
```

**Contingency Table:**

|                     | Spam     | Non-Spam   |
|---------------------|----------|------------|
| **Has "cash price"**| 90/100   | 50/9900    |
| **No "cash price"** | 10/100   | 9850/9900  |

**Applying Bayes' Theorem — P(Spam | "cash price"):**

```
Step 1: P(spam)         = 100/10k
Step 2: P(B|A)          = 90/100      (P("cash price" | spam))
Step 3: P(B)            = P(word in ANY email)
                        = (90/10k) + (50/10k)
                        = 90/10k + 50/10k
                        = 140/10k

Step 4:
              (100/10k) × (90/100)
P(A|B)   =  ─────────────────────
                    140/10k

              90/10k
           = ──────────
              140/10k

           = 90/140

           ≈ 0.64  =  64%
```

**Conclusion:**
> Given an email contains the word "cash price", there is a
> **64% probability** that the email is spam.

---

## 7. Cheat Sheet

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  PROBABILITY — QUICK REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  BASIC
  P(A) = No. of favourable outcomes / Total outcomes
  0 ≤ P(A) ≤ 1

  FUNDAMENTAL RULES
  ① Addition    P(A∪B) = P(A) + P(B) − P(A∩B)
  ② Multiplication P(A∩B) = P(A) × P(B|A)
  ③ Complement  P(A') = 1 − P(A)

  CONDITIONAL PROBABILITY
  P(A|B) = P(A∩B) / P(B)       where P(B) > 0

  BAYES' THEOREM
  P(A|B) = P(A) × P(B|A) / P(B)

  Terms:
    P(A|B) → Posterior  (updated belief)
    P(B|A) → Likelihood (evidence strength)
    P(A)   → Prior      (initial belief)
    P(B)   → Evidence   (total probability)

  KEY EXAMPLES FROM CLASS
  Dice  P(even)           = 3/6 = 1/2
  Dice  P(even OR >4)     = 2/3
  Cards P(2 Aces, no rep) = 12/2652
  Coin  P(≥1 head, 2flip) = 3/4
  Balls P(2nd red|1st red)= 1/2
  Spam  P(spam|"cashprice")= 64%

  TYPES OF DATA
  Categorical → groups/categories
  Numerical   → Discrete (whole) / Continuous (float)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Further Reading

- 🌐 [Probability in ML — GeeksforGeeks](https://www.geeksforgeeks.org/maths/probability-in-machine-learning/)
- 🌐 [Bayes Theorem — GeeksforGeeks](https://www.geeksforgeeks.org/maths/bayes-theorem/)
- 🌐 [Conditional Probability — GeeksforGeeks](https://www.geeksforgeeks.org/maths/conditional-probability/)
- 🌐 [Naive Bayes Classifier](https://www.geeksforgeeks.org/naive-bayes-classifiers/)

---

*Class Notes — Probability | April 2026*
