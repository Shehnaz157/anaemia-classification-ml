# Multimodal Deep Learning for Anaemia Classification

MSc Dissertation project (CN7000) at University of East London

## Overview

This project classifies anaemia using combined clinical and blood cell image data through multimodal deep learning. It compares feature-level and late fusion architectures against single-modality baselines across three model families: clinical (CBC), image, and fusion models.

**Best model:** Feature-level fusion achieved 89.0% accuracy, 94.8% sensitivity, and 0.957 ROC-AUC on the held-out test set (200 patients).

## Dataset

Download the AneRBC dataset from Mendeley Data:
https://data.mendeley.com/datasets/hms3sjzt7f/1

The dataset contains:
- 12,000 blood cell images (6,000 anaemic, 6,000 healthy)
- 1,000 patients (12 tiles per patient from AneRBC-II)
- Complete blood count (CBC) values paired with each patient
- Patient-level train/validation/test split (80/15/5)

### Setup

1. Download the dataset from the link above
2. Extract the files
3. Place the dataset folder in `data/raw/` before running the notebook

## Models and Results

### Model Inventory

| Category | Models |
|----------|--------|
| **Clinical** | Logistic Regression, Random Forest, XGBoost, SVM, MLP |
| **Image** | EfficientNetB0, ResNet-50, DenseNet121, MobileNetV2 |
| **Fusion** | Feature-level (concatenation), Late fusion (stacked) |

### Test Set Performance (200 held-out patients)

| Model | Accuracy | Sensitivity | Specificity | ROC-AUC |
|-------|----------|-------------|-------------|---------|
| **Fusion: feature-level** | 0.890 | 0.948 | 0.835 | 0.957 |
| Image: EfficientNetB0 | 0.835 | 0.784 | 0.883 | 0.938 |
| Fusion: late (stacked) | 0.830 | 0.804 | 0.854 | 0.935 |
| Image: MobileNetV2 | 0.855 | 0.784 | 0.922 | 0.935 |
| Image: DenseNet121 | 0.825 | 0.918 | 0.738 | 0.932 |
| Image: ResNet50 | 0.790 | 0.856 | 0.728 | 0.927 |
| Clinical: Logistic Regression | 0.665 | 0.660 | 0.670 | 0.715 |
| Clinical: SVM | 0.640 | 0.701 | 0.583 | 0.706 |

Full results across 10 metrics available in the notebook and results CSV.

## Project Structure

```
anaemia-classification/
├── README.md                                  # This file
├── .gitignore                                 # Git ignore rules
├── LICENSE                                    # MIT License
├── notebooks/
│   └── mdlforanaemiaclassificationv06.ipynb  # Main analysis notebook
├── data/
│   ├── raw/                                   # Downloaded dataset (not in repo)
│   └── processed/                             # Any processed datasets
└── results/
    └── figures/                               # Generated visualizations
```

## Usage

1. Install dependencies:
   ```bash
   pip install tensorflow keras pandas numpy scikit-learn matplotlib pillow
   ```

2. Download the dataset and place in `data/raw/`

3. Run the notebook:
   ```bash
   jupyter notebook notebooks/mdlforanaemiaclassificationv06.ipynb
   ```

## Key Features

- **Data preparation**: Patient-level splitting to avoid data leakage
- **Multimodal fusion**: Compares concatenation vs late fusion architectures
- **Extended evaluation**: 10 metrics per model (accuracy, sensitivity, specificity, F1, MCC, ROC-AUC, PR-AUC, precision, recall, Brier score)
- **Calibration analysis**: Calibration curves and Brier scores assess reliability
- **Interpretability**: Grad-CAM visualizations show where models focus
- **Statistical testing**: McNemar tests with Holm correction for pairwise comparisons

## Dependencies

- TensorFlow 2.20.0
- Keras
- pandas
- numpy
- scikit-learn
- Pillow
- matplotlib

## Metrics Explained

- **Accuracy**: Proportion of correct predictions
- **Sensitivity**: True positive rate (correctly identified anaemic cases)
- **Specificity**: True negative rate (correctly identified healthy cases)
- **F1**: Harmonic mean of precision and recall
- **ROC-AUC**: Area under receiver operating characteristic curve
- **PR-AUC**: Area under precision-recall curve
- **MCC**: Matthews correlation coefficient (balanced metric for imbalanced data)

## Author

Shehnaz (3023411)  
MSc Dissertation, University of East London, 2026

## Citation

If you use this project or dataset in your work, please cite:

```
Shehnaz. Multimodal Deep Learning for Anaemia Classification. 
MSc Dissertation, CN7000, University of East London, 2026.

Dataset: https://data.mendeley.com/datasets/hms3sjzt7f/1
```

## License

This code is licensed under the MIT License. See LICENSE file for details.

The AneRBC dataset is available under its own license on Mendeley Data. Please check the dataset page for appropriate citation and usage terms.

## Notes for Dissertation Review

- The main notebook implements the complete experimental pipeline from v06
- Results are derived from AneRBC-II only (12,000 images, 1,000 patients)
- AneRBC-I slides are excluded from modelling
- All splits are patient-based to prevent specimen leakage
- Clinical and image modalities are preprocessed separately before fusion
- No data augmentation applied during training
- Early stopping (patience=5) prevents overfitting

## Questions or Issues

For questions about the project, please refer to the dissertation document or contact the author.
