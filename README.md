# 📊 Predictive Analytics (UCS654) — Assignment 1

This repository contains my solution for **Assignment 1** of the **Predictive Analytics (UCS654)** course ✅

---

## 🎯 Objective

Estimate the parameters of the following probability density function (PDF):

\[
\hat{p}(z) = c \, e^{-\lambda (z-\mu)^2}
\]

using the **NO2** feature from the given Kaggle dataset after applying the required nonlinear transformation 🧠

---

## 🗂️ Dataset

- 📌 Source: Kaggle (as provided in the assignment)
- 📄 File used: `data.csv`
- 🔍 Feature used: **NO2**

---

## 🧪 Methodology

### 1️⃣ Load and preprocess data
- Load `data.csv`
- Clean column names ✨
- Extract **NO2** column
- Remove missing values (NaNs) 🚫
- Keep valid values only (`NO2 >= 0`) ✅

---

### 2️⃣ Compute roll-number dependent parameters

For roll number **r**, compute:

\[
a_r = 0.05(r \bmod 7)
\]
\[
b_r = 0.3(r \bmod 5 + 1)
\]

---

### 3️⃣ Apply nonlinear transformation

Transform NO2 values \(x\) into \(z\) using:

\[
z = x + a_r\arcsin(\text{clip}(b_r x))
\]

Clipping is applied to satisfy the valid domain of \(\arcsin(\cdot)\):

\[
-1 \le b_r x \le 1
\]

✅ This ensures there are no invalid values while retaining all data points.

---

### 4️⃣ Estimate PDF parameters

Given:

\[
\hat{p}(z) = c \, e^{-\lambda (z-\mu)^2}
\]

Estimate parameters using:

\[
\mu = \frac{1}{n}\sum_{i=1}^{n} z_i
\]

\[
\sigma^2 = \frac{1}{n}\sum_{i=1}^{n} (z_i-\mu)^2
\]

\[
\lambda = \frac{1}{2\sigma^2}
\]

\[
c = \sqrt{\frac{\lambda}{\pi}}
\]

---

## ✅ Final Outputs

The final submission consists of:

- 📍 \( \mu \) (mu)
- 📍 \( \lambda \) (lambda)
- 📍 \( c \)

📈 Additional plots generated:
- Histogram of \(z\) with PDF overlay
- CDF of the fitted distribution
- Empirical CDF vs theoretical CDF comparison

---

## 🏗️ Repository Structure

```text
.
├── data.csv
├── Assignment_01_L2.ipynb
└── README.md
