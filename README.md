# CT-radiomics-and-laryngoscopic-deep-learning-model
# CT Radiomics and Laryngoscopic Deep Learning for Prediction of Thyroid Gland Invasion in LHSCC

## Overview

This repository contains the code associated with the study **"Multimodal CT Radiomics and Laryngoscopic Deep Learning for Prediction of Thyroid Gland Invasion in Laryngeal and Hypopharyngeal Squamous Cell Carcinoma."**

The study aimed to develop and externally validate a multimodal artificial intelligence framework integrating CT-based radiomics and laryngoscopic deep learning (DL) features for the preoperative prediction of thyroid gland invasion (TGI) in patients with laryngeal and hypopharyngeal squamous cell carcinoma (LHSCC).

The proposed framework combines complementary information from intratumoral and peritumoral CT radiomics features and multichannel laryngoscopic images, including white-light imaging (WLI) and narrow-band imaging (NBI).

## Study Design

This was a multicenter retrospective study involving three medical institutions:

- **Development cohort:** 185 patients
- **External validation cohort 1:** 55 patients
- **External validation cohort 2:** 135 patients
- **Total:** 375 patients

The primary outcome was histopathologically confirmed thyroid gland invasion.

## Methodology

The overall workflow consists of the following components:

### 1. CT Radiomics Analysis

- Manual segmentation of primary tumors on venous-phase contrast-enhanced CT images.
- Construction of three-dimensional intratumoral volumes of interest (VOIs).
- Generation of anatomically constrained peritumoral VOIs using 1-, 3-, and 5-mm expansions.
- Radiomic feature extraction using PyRadiomics.
- Feature selection using the Mann–Whitney U test, Spearman correlation analysis, minimum redundancy maximum relevance (mRMR), and least absolute shrinkage and selection operator (LASSO).
- Model development using logistic regression (LR), support vector machine (SVM), random forest (RF), and extra trees (ET).

### 2. Multichannel Laryngoscopic Deep Learning

- Two white-light imaging (WLI) images and one narrow-band imaging (NBI) image were used for each patient.
- Three images were incorporated as independent input channels.
- Five CNN architectures were evaluated:
  - ResNet101
  - ResNet152
  - DenseNet121
  - DenseNet201
  - MobileNetV3-Large
- ImageNet-pretrained weights were used for model initialization.
- Grad-CAM was employed for model interpretability.

### 3. Multimodal Feature Fusion

- Extraction of deep learning features from the optimal laryngoscopic model.
- Integration of CT radiomics and laryngoscopic deep learning features at the patient level.
- Development of multimodal prediction models.
- SHAP analysis to interpret feature contributions.

### 4. Model Evaluation

Model performance was evaluated in the development cohort and two independent external validation cohorts.

Evaluation metrics included:

- Area under the receiver operating characteristic curve (AUC)
- Accuracy, sensitivity, and specificity
- Positive and negative predictive values (PPV and NPV)
- F1 score
- Calibration analysis
- Decision curve analysis (DCA)

## Software and Computational Environment

| Component | Version / Configuration |
|---|---|
| Python | 3.8.10 |
| PyTorch | 2.0.1 |
| CUDA | 11.8 |
| PyRadiomics | 3.1.0 |
| GPU | NVIDIA GeForce RTX 4080 Ti |
| Random seed | 0 |

## Repository Structure

```text
CT-radiomics-and-laryngoscopic-deep-learning-model/
│
├── CT_Radiomics/
│   ├── preprocessing/
│   ├── segmentation/
│   ├── feature_extraction/
│   └── model_development/
│
├── Laryngoscopic_DL/
│   ├── preprocessing/
│   ├── model_training/
│   ├── feature_extraction/
│   └── Grad_CAM/
│
├── Multimodal_Fusion/
│   ├── feature_fusion/
│   ├── model_development/
│   └── SHAP_analysis/
│
├── Model_Evaluation/
│   ├── ROC_analysis/
│   ├── calibration/
│   └── DCA/
│
├── requirements.txt
├── README.md
└── LICENSE
```

*Note: The directory structure above provides an organizational framework and should be adjusted according to the actual files included in this repository.*

## Data Availability

The clinical data and medical images used in this study are not publicly available because of patient privacy and institutional ethical restrictions. The code provided in this repository is intended to facilitate methodological transparency and reproducibility.

Researchers interested in the study methodology or additional information may contact the corresponding author, subject to institutional policies and applicable data-sharing regulations.

## Reproducibility

The source code and computational settings are provided to support reproducibility of the proposed framework. Detailed implementation instructions and dependencies will be provided where applicable.

## Citation

If you use this code in your research, please cite the original publication:

**Multimodal CT Radiomics and Laryngoscopic Deep Learning for Prediction of Thyroid Gland Invasion in Laryngeal and Hypopharyngeal Squamous Cell Carcinoma.**

*Publication details will be added upon publication.*

## Ethics Statement

This study was conducted in accordance with the relevant institutional ethical requirements. Patient data were handled in accordance with applicable privacy and data protection regulations.

## Contact

For questions regarding the code or methodology, please contact the corresponding author of the study.
