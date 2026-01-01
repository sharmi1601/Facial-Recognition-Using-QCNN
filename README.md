# Facial Recognition Using Quantum Convolutional Neural Networks (QCNN)

This repository contains the code, experiments, and analysis accompanying the paper:

**“Facial Recognition by Using Ensemble and Network of Quantum Convolutional Neural Networks”**  
Accepted at **ASCE CSCI 2025** (Springer proceedings, publication expected Jan 2026)


## Motivation

Quantum Convolutional Neural Networks (QCNNs) are often evaluated primarily on benchmark accuracy.
This work instead investigates **when and why QCNN-based representations are effective**, and where
they collapse due to noise, limited qubit capacity, or encoding constraints.

The central question explored in this project:

> *Do QCNNs provide meaningful inductive bias for facial representations, or are gains largely driven by classical post-processing?*


## Key Contributions

- Designed a **QCNN + SVM ensemble architecture** for face recognition using amplitude encoding.
- Systematically studied the effect of:
  - number of qubits
  - circuit depth
  - measurement strategy
  - ensemble aggregation
- Identified regimes where QCNN representations generalize vs overfit.
- Benchmarked simulation results against **IBM Quantum hardware**, documenting noise-induced degradation.
- Reported **failure cases**, not only best-case accuracy.

---

## Experimental Setup

- **Dataset**: Yale Face Dataset (selected subjects, controlled lighting variations)
- **Encoding**: Amplitude encoding into multi-qubit quantum states
- **Models**:
  - QCNN (custom circuit design)
  - Classical SVM on quantum feature measurements
  - Ensemble voting across QCNN variants
- **Evaluation**:
  - Accuracy
  - Stability across runs
  - Sensitivity to shot count and noise


## Results Summary

- Achieved **95.27% accuracy** under ideal simulation conditions.
- Observed performance degradation on real quantum hardware due to:
  - gate noise
  - measurement variance
  - limited shot budget
- Found diminishing returns beyond certain circuit depths.

Detailed results, ablations, and plots are included in the paper.


## Limitations & Open Questions

This work does claim quantum advantage.

Key limitations identified:
- Amplitude encoding scalability
- Noise sensitivity on current NISQ hardware
- Dependence on classical classifiers for final decision boundaries

Open research directions:
- Alternative encodings with lower normalization constraints
- Noise-aware training objectives
- End-to-end quantum classifiers without classical SVM
