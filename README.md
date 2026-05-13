**General Overview**
This is the repo I made for CS-131: Processing Big Data - Tools and Techniques, a class I took at SJSU in Spring 2025. 
Assignment notebooks can be found in `notebooks`, their csv's live in `data`, and the Bash preprocessing scripts are in `preprocessing`.

# OCR Machine Learning Project Overview
A machine learning project revisiting a classic optical character recognition (OCR) problem: given pixel measurements of a capital letter, can we correctly identify it? We used the same dataset from Frey and Slate's 1991 paper as a benchmark, then evaluated three modern models against it to see how far the field has come.

*Partner project with Huu Tinh Nguyen. Full methodology and results in `CS131_Final_Report.pdf`.*

Primary contributions: dataset selection, problem framing, preprocessing pipeline, Random Forest and MLP implementation, experimental design, and report writing.

**The Question**

Frey and Slate achieved roughly 80% accuracy on this task in 1991 with the tools available to them. With modern libraries, better cross-validation practices, and tuned hyperparameters, how much better can we do?

Answer: a lot. Our best model hit 98%.

**What we built**

A full ML pipeline from raw data to evaluated models, including:

_Preprocessing in Linux command-line_ — relabeling, deduplication, class distribution checks, and missing value verification, all done in bash before touching Python
**Three models:** Random Forest, Multinomial Logistic Regression, and a Multilayer Perceptron (TensorFlow)
_Systematic experimentation_ — each model was evaluated across four conditions: original vs. deduplicated data, with and without 5-fold cross-validation, to isolate what actually improved performance
_Hyperparameter tuning via GridSearchCV_ on all models

**Results**

| Model | Best Accuracy |
|---|---|
| Random Forest | 97.9% |
| Multilayer Perceptron | 96.1% |
| Multinomial Logistic Regression | 76.7% |

The best overall model was a Random Forest trained on deduplicated data with GridSearchCV (750 estimators, max depth 15). Notably, it outperformed the MLP while training significantly faster, which is an important consideration for real-world OCR deployment.

A key finding: deduplication + cross-validation consistently improved performance across all model types, reinforcing how much data preparation and evaluation methodology matter relative to model choice alone.

**Stack**

Python, Scikit-Learn, TensorFlow, bash
