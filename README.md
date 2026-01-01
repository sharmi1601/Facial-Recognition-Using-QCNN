# Facial Recognition Using Ensemble and Network of Quantum Convolutional Neural Networks (N-QCNN)

This repository contains the code, experimental pipeline, and supporting material for the paper:
Accepted at **ASCE CSCI 2025** (Springer proceedings; publication expected Jan 2026)


## Overview

This work presents a **hybrid quantum–classical ensemble model** for multiclass facial recognition based on the *Network of Quantum Convolutional Neural Networks (N-QCNN)* framework.

Instead of relying on a single QCNN architecture, the proposed approach integrates **three structurally distinct QCNNs**, each paired with a classical Support Vector Machine (SVM). Final predictions are produced using **majority voting with a confidence-based tie-breaking rule**.

The primary motivation is to achieve **robust feature extraction on small datasets**, where classical deep learning models often struggle due to limited training samples.


## Key Idea

> Can an ensemble of diverse QCNN architectures extract complementary quantum features that improve robustness and generalization on limited facial image data?

To explore this question, the model:
- treats entire quantum circuits as **modular subnetworks**
- emphasizes **architectural diversity** rather than deeper circuits
- combines quantum feature extraction with classical SVM decision boundaries


## Contributions

- Practical implementation of the **N-QCNN ensemble framework**
- Design of **three distinct 4-qubit QCNN architectures** with different entanglement and pooling strategies
- Integration of QCNN outputs with **three independent classical SVMs**
- Majority voting with **confidence-based tie breaking** for final classification
- Evaluation on:
  - a **7-class subset** of the Yale Face Dataset (95.27% accuracy)
  - the **full 15-class dataset** (80.00% accuracy)
- Demonstration of strong performance under **extremely limited training data**


## Dataset & Preprocessing

- **Dataset**: Yale Face Dataset
- Images converted to grayscale and resized to **48×48**
- Each image divided into **non-overlapping 2×2 patches**
- Pixel values normalized to the range **[0, 2π]**
- Each patch encoded using **angle encoding (RY gates)** into a 4-qubit quantum state


## Model Architecture

### Quantum Feature Extraction

- Ensemble of **three independent QCNN circuits**
- Each QCNN:
  - uses a unique circuit design
  - extracts complementary quantum features
  - mitigates overfitting and barren plateau risks through diversity

QCNN variants include:
- rotationally entangled architectures
- superposition-enhanced designs using Hadamard gates
- parameter-efficient layered circuits with controlled entanglement

### Classical Classification

- Each QCNN feeds into a dedicated **RBF-kernel SVM**
- Final prediction determined by:
  1. majority voting across SVM outputs
  2. confidence-based tie breaking in case of ties


## Experimental Setup

- Implemented using **Python + Qiskit**
- Quantum execution via **Qiskit Aer Simulator**
- Optimizer: **COBYLA**
- Shots per circuit: **1024**
- Training/testing split:
  - 8 images per subject for training
  - 3 images per subject for testing


## Results

| Experiment | Classes | Accuracy |
|----------|--------|---------|
| Partial Yale Dataset | 7 | **95.27%** |
| Full Yale Dataset | 15 | **80.00%** |

Observations:
- Near-perfect classification for several subjects
- Increased performance variance for visually similar subjects
- Ensemble architecture remains robust as classification complexity increases
