# cs131-letter-recognition

This repo is from CS-131: Processing Big Data - Tools and Techniques (SJSU, Spring 2025),
a course that combined Unix/bash tooling with machine learning. Assignment notebooks live
in `notebooks/`, their datasets in `data/`, and bash preprocessing scripts in `preprocessing/`.

---

# Final Project — Bridging the Gap Between Visual Input and Textual Output

A machine learning project revisiting a classic optical character recognition (OCR) problem:
given pixel measurements of a capital letter, can we correctly identify it? We used the same
dataset from Frey and Slate's 1991 paper as a benchmark, then evaluated three modern models
against it to see how far the field has come.

*Partner project with Huu Tinh Nguyen. Full methodology and results in `CS131 Final Report.pdf`.*

Primary contributions: dataset selection, problem framing, preprocessing pipeline, Random
Forest and MLP implementation, experimental design, and report writing.

## The Question

Frey and Slate achieved roughly 80% accuracy on this task in 1991 with the tools available
to them. With modern libraries, better cross-validation practices, and tuned hyperparameters,
how much better can we do?

Answer: a lot. Our best model hit 98%.

## What We Built

A full ML pipeline from raw data to evaluated models, including:

- **Preprocessing in bash** — relabeling, deduplication, class distribution checks, and
missing value verification, all done in the command line before touching Python
- **Three models** — Random Forest, Multinomial Logistic Regression, and a Multilayer
Perceptron (TensorFlow)
- **Systematic experimentation** — each model evaluated across four conditions: original
vs. deduplicated data, with and without 5-fold cross-validation, to isolate what actually
improved performance
- **Hyperparameter tuning via GridSearchCV** on all models

## Results

| Model | Best Accuracy |
|---|---|
| Random Forest | 97.9% |
| Multilayer Perceptron | 96.1% |
| Multinomial Logistic Regression | 76.7% |

The best overall model was a Random Forest trained on deduplicated data with GridSearchCV
(750 estimators, max depth 15). It outperformed the MLP while training significantly faster —
an important consideration for real-world OCR deployment.

A key finding: deduplication + cross-validation consistently improved performance across all
model types, reinforcing how much data preparation and evaluation methodology matter
relative to model choice alone.

## Stack

Python, Scikit-Learn, TensorFlow, bash
