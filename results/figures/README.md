# Figures

All charts exported from `notebook/ids_experiment.ipynb`.

| File | Description |
|---|---|
| `dataset_class_distribution.png` | Class imbalance in Edge-IIoTset — illustrates why Borderline-SMOTE was necessary |
| `training_history.png` | Loss and accuracy curves across training epochs for deep learning models |
| `model_comparison.png` | Accuracy, F1 macro, and MCC across all four models on clean test data |
| `confusion_matrix_hybrid.png` | Confusion matrix for the hybrid model — shows where misclassification concentrates |
| `confusion_matrix_random_forest.png` | Confusion matrix for the Random Forest baseline |
| `roc_curves.png` | ROC curves one-vs-rest for all 15 classes with per-class AUC values |
| `adversarial_comparison_all_models.png` | Accuracy degradation across all four models under FGSM attack |
| `adversarial_accuracy_hybrid.png` | Hybrid model accuracy at each epsilon perturbation level |
| `shap_feature_attribution.png` | SHAP feature attribution values — which features drive predictions |
| `shap_autoencoder_errors.png` | Autoencoder reconstruction error distribution for clean vs adversarial samples |
| `shap_fingerprint_detection.png` | SHAP fingerprinting detection rate across epsilon levels |
