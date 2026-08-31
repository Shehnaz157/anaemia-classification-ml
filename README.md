# Multimodal Deep Learning for Anaemia Classification

MSc Dissertation project (CN7000) at University of East London

## Overview

Classifies anaemia using combined clinical (CBC) and blood cell image data 
through multimodal deep learning fusion. Compares feature-level and late fusion 
architectures against single-modality baselines.

## Dataset

Download the AneRBC dataset from Mendeley Data:
https://data.mendeley.com/datasets/hms3sjzt7f/1

Place the files in `data/raw/` before running the notebook.

## Models

- Image models: EfficientNetB0, ResNet-50, DenseNet121, MobileNetV2
- Clinical models: Logistic Regression, Random Forest, XGBoost, SVM, MLP
- Fusion: Feature-level concatenation, Late stacking

## Results

Best model: Feature-level fusion (89.0% accuracy, 95.7% ROC-AUC)

## Usage

1. Download data from the link above
2. Run the notebook: `notebooks/mdlforanaemiaclassificationv06.ipynb`

## Citation

If you use this work, please cite:
[Your name]. Multimodal Deep Learning for Anaemia Classification. 
MSc Dissertation, University of East London, 2026.

## License

This code is licensed under the MIT License.
Dataset: See Mendeley Data page for terms.
