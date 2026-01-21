# 📊 Predictive Analytics (UCS654) — Assignment 1

This repository contains my solution for **Assignment 1** of the **Predictive Analytics (UCS654)** course ✅

---

## 🎯 Objective

Estimate the parameters of the following PDF:

**p̂(z) = c · exp( −λ (z − μ)² )**

using the **NO2** feature from the given Kaggle dataset after applying the nonlinear transformation specified in the assignment.

---

## 🗂️ Dataset

- 📌 Source: Kaggle  
- 🔗 Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data  
- 📄 File used: `data.csv` (downloaded from Kaggle)
- 🔍 Feature used: **NO2**

⚠️ Note: The dataset file is large, so it is **not uploaded** in this repository.

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

- **aᵣ = 0.05 · (r mod 7)**
- **bᵣ = 0.3 · ((r mod 5) + 1)**

---

### 3️⃣ Apply nonlinear transformation

Transform NO2 values **x** into **z** using:

**z = x + aᵣ · arcsin( clip(bᵣ · x, −1, 1) )**

✅ Clipping is applied to satisfy the valid domain of arcsin (input must be between −1 and 1).

---

### 4️⃣ Estimate PDF parameters

Given:

**p̂(z) = c · exp( −λ (z − μ)² )**

Estimate parameters:

- **μ = mean(z)**
- **σ² = mean( (z − μ)² )**
- **λ = 1 / (2σ²)**
- **c = sqrt( λ / π )**

---

## ✅ Final Outputs

The final submission consists of:

- 📍 μ (mu)
- 📍 λ (lambda)
- 📍 c


---

## 🏗️ Repository Structure

```text
.
├── Assignment_01_L2.ipynb
└── README.md
