# Skin lesion classification

Course project: **Developing a Machine Learning Approach for Benign and Malignant Skin Lesion Classification using Dermatoscopic Imaging**.

This project investigates the use of deep learning for binary classification of dermatoscopic skin lesion images, with a focus on malignant lesion detection, probability calibration and confidence-based referral for expert review. 

An ImageNet-pretrained ResNet-18 CNN was fine tuned using the HAM 10000 dataset. Temperature scaling was applied to improve predicted probability reliability, followed by confidence based referral strategy to identify images requiring expert review. 

## Data and approach

- Dataset: [HAM10000 / ISIC Archive](https://api.isic-archive.com/collections/212/)
- Task: binary lesion classification. Define class mappings and exclusions in `docs/label-policy.md` before analysis.
- Preprocessing: pandas, NumPy, Pillow/OpenCV.
- Models: scikit-learn feature baseline and PyTorch transfer learning.
- Evaluation: lesion-grouped splits; malignant sensitivity, specificity, precision, F1, ROC-AUC, and confusion matrix.

## Layout

| Path | Purpose |
| --- | --- |
| `docs/` | Project summary, dataset use and label decisions |
| `data/raw/` | Downloaded source images and labels (ignored by Git) |
| `data/processed/` | Processed inputs (ignored by Git) |
| `notebooks/` | Exploratory work |
| `src/` | Reusable preprocessing, training, evaluation code |
| `models/` | Model weights (ignored by Git) |
| `results/` | Figures and metric tables |
| `tests/` | Checks for data integrity and splits |
