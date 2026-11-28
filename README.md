# Skin lesion classification

**ENGG 680 Course project: Developing a Machine Learning Approach for Benign and Malignant Skin Lesion Classification using Dermatoscopic Imaging**.

## Project Overview
Accurate classification of skin lesions as benign or malignant is critical for early cancer diagnosis and treatment. However, similarities between benign and malignant lesions can make clinical diagnosis challenging, motivating the development of automated diagnostic support tools. This study aimed to develop a convolutional neural network (CNN) using transfer learning to classify dermoscopic skin lesions and evaluate a confidence-based referral system. A pretrained ResNet-18 binary classifier was trained using the HAM10000 dermatoscopic image dataset, incorporating image augmentation, class weighting, and lesion-level data splitting to distinguish between benign and malignant lesions. Temperature scaling was implemented to calibrate predicted probabilities, and benign predictions were automatically accepted when their calibrated confidence reached or exceeded 0.80. All remaining images were referred for simulated expert review. 

On an independent, lesion-disjoint test set of 1,415 images, the model achieved a balanced accuracy of 80.83%, a malignant sensitivity of 91.10%, and a ROC-AUC of 0.8981. Temperature scaling reduced expected calibration error from 0.0793 to 0.0281. The calibrated referral system referred all 236 malignant images for simulated expert review, with an overall referral rate of 70.74%.  In comparison, the uncalibrated system referred 59.22% of images, including 235 of 236 malignant images, for simulated expert review. Calibration therefore increased the referral workload while producing a small improvement in observed malignant referral sensitivity. These findings highlight the trade-off between prioritizing malignant lesion detection and minimizing expert review workload. Although evaluation on a single dermatoscopic dataset does not establish clinical reliability or generalizability, the results support further investigation into machine-learning-based diagnostic support systems.  

## Objectives 
- Develop a CNN to distinguish between benign and malignant skin lesion images
- Investigate model optimization that prioritize malignant sensitivity
- Evaluate and improve reliability and trust in predicted confidence through calibration and temprature scaling.
- Develop a confidence-based referral strategy for simulated expert review
- Investigate the trade-off between malignant refferal sensitivity and clinician workload

## Dataset and approach

This project uses HAM10000 dataset, containing 10,015 dermatoscopic images across 7 diagnostic categories. 
- Dataset:[HAM 10000 Harvard Dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/DBW86T)
- Alternative Access: [HAM10000 / ISIC Archive](https://api.isic-archive.com/collections/212/)
- Task: Binary lesion classification. 
- Classification: Benign (0) and malignant (1), excluding the akiec diagnostic category. 
- Preprocessing: Image resizing (224 x 224), ImageNet normalization, training only augmentation. 
- Model: Pretrained ResNet-18 with fine tuning, weighted cross entropy loss.
- Optimization: Additional fine tuning, classification threshold optimization, class-weight adjustment.
- Calbration: Temprature scaing (T = 1.64)
- Referral: Benign predictions with calibrated confidence less than 0.80 were automatically accepted. All remaining predictions were refered for simulated expert review.
- Statistical evaluation: Lesion-level bootstrapping, Wilson confidence intervals. 
- Model Evaluation: lesion-grouped splits; malignant sensitivity, specificity, precision, F1, ROC-AUC, and confusion matrix.

## Packages and technologies used: 
- Enviornment: Python, Google Colab, Google drive
- Machine Learning: PyTorch, Torchvision, scikit-learn
- Preprocessing: pandas, NumPy, Pillow
- Visualization: Matplotlib

## Layout & Location of relevant info

| Path | Purpose |
| --- | --- |
| docs | Information on dataset, label policies and project summary | 
| `EGGG 680 Final Model.ipynb` | Notebook with final model development and evaluation|
| `ENGG 680 Model Optimization CLEAN.ipynb` | Notebook for model optimization experiments |
| `ENGG 680 Threshold Optimization CLEAN.ipynb` | Notebook for threshold optimization |
| `ENG 680 Original Data Processing CLEAN.ipynb` | Notebook for data processing |

