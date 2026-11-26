
# 📊 Normalization and Standardization in Data Science

## 1. Normalization

**Normalization** is a data preprocessing technique used to scale numerical values into a specific range, usually between 0 and 1.

It ensures that features with larger numerical values do not dominate features with smaller numerical values.

Normalization is particularly useful for distance-based algorithms such as K-Nearest Neighbors (KNN), K-Means Clustering, and Neural Networks.

### Types of Normalization

### 1.1 Min-Max Normalization

Min-Max Normalization scales the values of a feature into a fixed range, usually [0, 1].

**Formula:**

```text
Normalized Value = (X - X_min) / (X_max - X_min)
```

**Where:**

- `X` = Original data value.
- `X_min` = Minimum value in the dataset.
- `X_max` = Maximum value in the dataset.
- `Normalized Value` = Scaled value.

**Example:**

Consider the dataset:

```text
X = [10, 20, 30, 40, 50]

X_min = 10
X_max = 50
```

For `X = 30`:

```text
Normalized Value = (30 - 10) / (50 - 10)
                 = 20 / 40
                 = 0.5
```

**Result:** The normalized value of 30 is **0.5**.

### 1.2 Decimal Scaling Normalization

Decimal Scaling Normalization scales data by moving the decimal point of the values. The number of decimal places moved depends on the maximum absolute value in the dataset.

**Formula:**

```text
Normalized Value = X / 10^j
```

**Where:**

- `X` = Original data value.
- `j` = Smallest integer such that the maximum absolute normalized value is less than 1.
- `Normalized Value` = Scaled value.

**Example:**

Consider the dataset:

```text
X = [25, 50, 75, 100]
```

The maximum absolute value is 100.

Therefore:

```text
j = 3
```

For `X = 50`:

```text
Normalized Value = 50 / 10^3
                 = 50 / 1000
                 = 0.05
```

The normalized dataset becomes:

```text
[0.025, 0.05, 0.075, 0.1]
```

**Result:** The normalized value of 50 is **0.05**.

### 1.3 Mean Normalization

Mean Normalization scales the values based on the mean and the range of the dataset. It generally transforms the values into a range around zero.

**Formula:**

```text
Normalized Value = (X - Mean) / (X_max - X_min)
```

**Where:**

- `X` = Original data value.
- `Mean` = Average of the dataset.
- `X_max` = Maximum value.
- `X_min` = Minimum value.
- `Normalized Value` = Scaled value.

**Example:**

Consider the dataset:

```text
X = [10, 20, 30, 40, 50]
```

**Step 1: Calculate the Mean**

```text
Mean = Sum of all values / Number of values

     = (10 + 20 + 30 + 40 + 50) / 5

     = 150 / 5

     = 30
```

**Step 2: Calculate the Normalized Value**

For `X = 40`:

```text
Normalized Value = (40 - 30) / (50 - 10)

                 = 10 / 40

                 = 0.25
```

**Result:** The mean-normalized value of 40 is **0.25**.

### 1.4 Vector Normalization (L2 Normalization)

Vector Normalization scales a vector so that its Euclidean (L2) norm becomes 1.

**Formula:**

```text
Normalized Vector = Original Vector / L2 Norm
```

The L2 norm is calculated using:

```text
L2 Norm = sqrt(x1^2 + x2^2 + ... + xn^2)
```

**Where:**

- `Original Vector` = Input feature vector.
- `xi` = Individual vector elements.
- `n` = Number of elements.
- `L2 Norm` = Euclidean norm of the vector.

**Example:**

Consider the vector:

```text
X = [3, 4]
```

**Step 1: Calculate the L2 Norm**

```text
L2 Norm = sqrt(3^2 + 4^2)

        = sqrt(9 + 16)

        = sqrt(25)

        = 5
```

**Step 2: Calculate the Normalized Vector**

```text
Normalized Vector = [3/5, 4/5]

                   = [0.6, 0.8]
```

**Result:** The normalized vector is **[0.6, 0.8]**, with an L2 norm of 1.

---

## 2. Standardization

**Standardization** is a data preprocessing technique that transforms numerical data so that it has a mean of 0 and a standard deviation of 1.

Unlike Min-Max Normalization, Standardization does not restrict values to a fixed range. The transformed values can be positive, negative, or zero.

It is commonly used in algorithms such as Logistic Regression, Support Vector Machines (SVM), and Principal Component Analysis (PCA).

### 2.1 Z-Score Standardization

Z-Score Standardization is the most commonly used standardization technique. It transforms data so that the mean becomes 0 and the standard deviation becomes 1.

**Formula:**

```text
Z = (X - Mean) / Standard Deviation
```

**Where:**

- `X` = Original data value.
- `Mean` = Average of the dataset.
- `Standard Deviation` = Measure of data dispersion.
- `Z` = Standardized value (Z-score).

**Example:**

Consider the dataset:

```text
X = [10, 20, 30, 40, 50]
```

**Step 1: Calculate the Mean**

```text
Mean = Sum of all values / Number of values

     = (10 + 20 + 30 + 40 + 50) / 5

     = 150 / 5

     = 30
```

**Step 2: Calculate the Standard Deviation**

Using the population standard deviation formula:

```text
Standard Deviation = sqrt(Sum of squared differences / N)
```

Substituting the values:

```text
                    sqrt((10-30)^2 + (20-30)^2 + (30-30)^2
Standard Deviation =  --------------------------------------
                       + (40-30)^2 + (50-30)^2) / 5

                    = sqrt((400 + 100 + 0 + 100 + 400) / 5)

                    = sqrt(1000 / 5)

                    = sqrt(200)

                    = 14.142
```

**Step 3: Calculate the Standardized Value**

For `X = 40`:

```text
Z = (X - Mean) / Standard Deviation

  = (40 - 30) / 14.142

  = 10 / 14.142

  = 0.707
```

**Result:** The standardized value of 40 is approximately **0.707**.

---

## 3. Difference Between Normalization and Standardization

| Basis | Normalization | Standardization |
|:---|:---|:---|
| **Meaning** | Scales data into a specific range. | Transforms data based on mean and standard deviation. |
| **Range** | Usually between 0 and 1. | No fixed range. |
| **Mean** | Not necessarily 0. | 0 (when calculated using the same dataset). |
| **Standard Deviation** | Not necessarily 1. | 1 (when using population standard deviation). |
| **Formula** | Min-Max or other scaling formulas. | Z-score formula. |
| **Outliers** | Sensitive to outliers, especially Min-Max. | Also influenced by outliers through mean and standard deviation. |
| **Common Use** | KNN, K-Means, and Neural Networks. | SVM, Logistic Regression, and PCA. |

---

## 4. Importance of Normalization and Standardization

Both techniques are important in data preprocessing because they:

1. Bring numerical features to comparable scales.
2. Prevent features with larger numerical values from dominating certain algorithms.
3. Improve the performance of distance-based machine learning algorithms.
4. Help improve model convergence during optimization.
5. Make numerical data easier to process and analyze.

---

## 5. Conclusion

Normalization and Standardization are important data preprocessing techniques used in Data Science and Machine Learning.

Normalization scales data into a specified range, whereas Standardization transforms data to have a mean of 0 and a standard deviation of 1.

The choice between these techniques depends on the dataset, the presence of outliers, and the machine learning algorithm being used.

**In simple terms: Normalization changes the range of data, whereas Standardization changes its scale based on the mean and standard deviation.**

---

<p align="center">
  <b>Data Science Assignment</b>
  <br>
  <i>Learn • Analyze • Implement</i>
</p>
