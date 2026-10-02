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
```

## 🛠️ Technical Approach and Model Architecture

To handle the multi-class classification task across **15 distinct classes**, the feature data was preprocessed using `StandardScaler` (centering features to mean ~0 and unit variance ~1). 

The deep learning architecture was updated with the following full configuration:

### Model Architecture & Hyperparameters

```python
import tensorflow as np
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.optimizers import Adam

# Sequential model build
model = Sequential([
    # Input layer and hidden layers
    Dense(64, activation='relu', input_shape=(78,)),
    Dense(32, activation='relu'),
    
    # Final output layer updated for 15 classes
    Dense(15, activation='softmax')
])

# Optimizer re-instantiated with learning rate 0.0001
opt = Adam(learning_rate=0.0001)

# Compilation
model.compile(
    optimizer=opt,
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)
