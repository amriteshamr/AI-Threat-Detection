# AI-Threat-Detection

An end-to-end Machine Learning pipeline for automated Network Intrusion Detection (NIDS). This project analyzes network traffic flow features to classify traffic as **benign** or **malicious** with high precision and recall.

---

## Overview & Objectives

Traditional threat detection systems often struggle with evolving traffic patterns and high volumes of data. This project leverages supervised machine learning to deliver fast, highly accurate, and automated threat detection across network traffic logs.

### Key Highlights
- **High Performance:** Achieved balanced Precision, Recall, and F1-scores of `1.00` on test evaluation.
- **Robust Validation:** 5-fold cross-validation demonstrated consistent reliability with a mean score of `~0.99978`.
- **Feature Optimization:** Identified critical network metrics driving malicious traffic classification.

---

## Key Features & Model Insights

Feature importance analysis revealed that forward packet behavior and initial window bytes are the strongest predictors of malicious activity:

1. `Init_Win_bytes_forward` — Initial window size in bytes for forward flow.
2. `Forward Packet Length Max` — Maximum length of forward packets.
3. `Average Forward Segment Size` — Mean size of forward segments.
4. `Forward Packet Length Mean` — Average length of forward packets.

---

## Performance & Evaluation

### 5-Fold Cross-Validation Scores
- **Fold Scores:** `[0.999354, 0.999354, 0.999845, 0.999354, 0.999912]`
- **Mean CV Score:** `0.999783`

### Model Metrics Summary
| Metric | Score |
| :--- | :--- |
| **Precision** | `1.00` |
| **Recall** | `1.00` |
| **F1-Score** | `1.00` |
| **Accuracy** | `99.98%` |

---

## Reproduction & Environment Setup

This project was developed and tested in **Google Colab** and can also be executed locally.

### Prerequisites & Dependencies
Ensure you have **Python 3.8+** installed along with the following packages:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter
