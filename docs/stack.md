# Technology Stack

All experiments were run on Kaggle GPU (NVIDIA Tesla P100).

---

## Core

| Library | Purpose |
|---|---|
| Python 3.10 | Language |
| TensorFlow / Keras | Building and training CNN, BiLSTM, and Transformer models |
| scikit-learn | Random Forest, StandardScaler, LabelEncoder, train/test split, classification metrics |
| imbalanced-learn | Borderline-SMOTE for class imbalance treatment |

---

## Adversarial testing

| Library | Purpose |
|---|---|
| IBM Adversarial Robustness Toolbox (ART) | FGSM adversarial attack generation |

ART was used to generate adversarial examples at four epsilon levels (0.01, 0.05, 0.10, 0.20) using the Fast Gradient Sign Method. The attack was applied as a white-box attack against the hybrid model, then transferred to all other models to measure cross-model adversarial transferability.

---

## Explainability and defence

| Library | Purpose |
|---|---|
| SHAP | KernelExplainer for generating Shapley attribution values |
| scikit-learn MinMaxScaler | Normalising SHAP vectors before autoencoder training |

The SHAP autoencoder defence layer was built using Keras. Architecture: 47→64→16→64→47 (input dimension matches the 47 feature columns after preprocessing). Detection threshold was set at the 95th percentile of reconstruction errors on clean samples, targeting a 5% false positive rate.

---

## Data and visualisation

| Library | Purpose |
|---|---|
| pandas | Data loading, cleaning, subsample, preprocessing |
| NumPy | Numerical operations |
| Matplotlib | All charts and plots |
| Seaborn | Confusion matrix heatmaps |

---

## Environment

Experiments run on Kaggle Notebooks with GPU accelerator enabled.
Dataset accessed directly via Kaggle dataset import (no local download required).
