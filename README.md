# 🧮⚔️ SYMBOLIC REGRESSION — MAIN QUEST

> *“Find the hidden formula. Conquer the vineyard.”*

---

## 🗺️ Quest Overview

**Symbolic Regression** is a regression technique used to generate **interpretable mathematical expressions**.  

In this project, Genetic Programming (GP) is used to create a **regressor** to predict the number of **lugs** produced in 1991 using the vineyard dataset. The GP evolves candidate equations over generations to find the best fit.

---

## 📊 DATASET — VINEYARD QUEST MAP

The dataset is taken from *Smoothing Methods in Statistics* (pages 146–147). It contains harvest data from a vineyard on a small island in Lake Erie:

- **Rows:** 52 (northwest → southeast)
- **Observations per row:** Number of lugs harvested in 1989, 1990, and 1991
- **Lug weight:** ~13.6078 kg of grapes per lug
- **Train/Test Split:** 70% training, 30% testing
- **Duplicate Rows:** Dropped during preprocessing

### 🧩 Dataset Statistics

- **Title:** `192 vineyard`
- **Variables:** 3  
- **Observations:** 52  
- **Attribute Type:** Continuous  
- **Missing Values:** None  
- **Duplicate Rows:** 1 (dropped during preprocessing)

---

## 🌳 MODEL REPRESENTATION — SKILL TREE

The GP regressor is represented as an **Expression Tree**:

- **Internal Nodes:** Operators from the functional set  
- **Leaf Nodes:** Operands from the terminal set or functional set

Expression trees allow flexible node manipulation and easy evaluation of candidate equations.

### 🌱 Initial Population

- **Generation Method:** Growth Method  
- **Initial Tree Depth:** 0 → start with simple trees

---

## 📐 FITNESS FUNCTION — DAMAGE CALCULATION

**Mean Absolute Error (MAE)** is used to evaluate each individual.  

- Always **non-negative**  
- Robust to outliers  
- Lower MAE indicates a stronger regressor  

---

## 🎯 SELECTION METHOD — PARTY RECRUITMENT

**Tournament Selection** is used:

- Randomly pick `k` individuals from the population  
- Select the one with the **lowest fitness score**  
- Chosen parents reproduce for the next generation

---

## 🧬 GENETIC OPERATORS — EVOLUTION MECHANICS

### 🏆 Elitism

- Keeps top 10% of individuals for the next generation  
- Ensures strong candidates are preserved

---

### 🔀 Crossover Operator

- Swaps subtrees between parents at a random point  
- **Crossover Rate:** 80%  
- Stricter rule: if offspring fitness > parent, crossover retries  

---

### 🧫 Mutation Operator

- Replaces a node at a random point with a new subtree  
- **Mutation Rate:** 15%  
- Stricter rule: if mutated fitness > parent, mutation retries  

---

## ⏹️ TERMINATION CRITERIA

- Maximum **tree depth**  
- Maximum **number of generations**  
- **Population size**

---

## ⚙️ PARAMETERS — BUILD STATS

- **Population Size:** 500 → encourages diversity  
- **Crossover Rate:** 80%  
- **Mutation Rate:** 15%  
- **Elitism Rate:** 5%  
- **Maximum Tree Depth:** 3 → manageable tree growth  
- **Initial Population Method:** Growth Method  

---

### ➕ Functional & Terminal Sets

**Functional Set:**  
{ +, -, *, / }


**Terminal Set:**  


{ x1, x2, c }

- `x1` → lugs produced in 1989  
- `x2` → lugs produced in 1990  
- `c` → constant (value = 2, tuned for better regressors)

---

## 🏁 QUEST STATUS

🧩 **Main Quest:** Symbolic Regression with Genetic Programming  
🚀 **Objective:** Predict 1991 grape harvests with an interpretable formula  
🏆 **Reward:** A robust mathematical regressor for the vineyard dataset  

---

*Honours-level project — built for evolution, not brute force.*
