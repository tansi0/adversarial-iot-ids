# Dataset

## Edge-IIoTset

**Source:** https://www.kaggle.com/datasets/mohamedamineferrag/edgeiiotset-cyber-security-dataset-of-iot-iiot

**Citation:**
Ferrag, M.A., Friha, O., Hamouda, D., Maglaras, L. and Janicke, H. (2022)
'Edge-IIoTset: A New Comprehensive Realistic Cyber Security Dataset of IoT and IIoT Applications for Centralized and Federated Learning',
*IEEE Access*, 10, pp. 40281–40306.
doi: 10.1109/ACCESS.2022.3165569

---

## What it contains

Generated from a physical IIoT testbed with 10+ heterogeneous device types; temperature sensors, heart rate monitors, soil moisture sensors, and Modbus-compatible industrial controllers. Traffic was captured under both normal operation and 14 attack scenarios.

**Attack categories:**
- DDoS: UDP flood, ICMP flood, TCP flood, HTTP flood
- Injection: SQL injection, XSS
- Reconnaissance: port scanning, OS fingerprinting, vulnerability scanning
- Man-in-the-middle: MITM
- Malware: backdoor, ransomware, file uploading, password attacks

Full dataset: 2,219,201 samples · 63 features · 15 classes

This study used a 15% stratified subsample — 286,450 samples, for compute feasibility on Kaggle GPU.

---

## Class imbalance

| Class | Count | % of dataset |
|---|---|---|
| Normal | ~1,615,643 | 73% |
| DDoS UDP | ~50,000 | ~2.3% |
| Fingerprinting | ~1,001 | 0.05% |
| MITM | ~1,214 | 0.05% |

This imbalance directly shaped the preprocessing approach. See below.

---

## Preprocessing

**Columns dropped (15 total):**
IP addresses, timestamps, port numbers, and raw payload bytes were removed before modelling. These fields identify which machines are talking, not how they are communicating. A model trained on them would memorise specific network topology rather than generalise to attack behaviour patterns.

After dropping columns: 309,530 duplicate rows removed. Clean dataset: 1,909,671 rows × 48 columns.

**Categorical encoding:** Seven categorical columns including `http.request.method` and `mqtt.protoname` encoded using LabelEncoder from scikit-learn.

---

## Split and scaling

Three-way stratified split:
- Training: 64% — 183,328 samples
- Validation: 16% — 45,832 samples
- Test: 20% — 57,290 samples

StandardScaler fitted on training data only, then applied to validation and test sets using training statistics. Fitting the scaler on all data before splitting would leak test distribution information into training, a form of data leakage that inflates reported metrics.

---

## Class imbalance treatment

Borderline-SMOTE applied to the training set only, after splitting. Training set expanded from 183,328 to approximately 1.96 million samples with each class balanced to ~130,943 samples.

Borderline-SMOTE was chosen over standard SMOTE because it generates synthetic samples near the decision boundary rather than randomly across the minority class. Validation and test sets were left untouched, all evaluation metrics reflect performance on real, unmodified data.
