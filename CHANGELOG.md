# Changelog

All significant changes to the Multimodal Deep Learning for Anaemia Classification project are documented here.

## [v0.6] - 2026-08-27

### Latest Release
**Current version in repository**

#### Added
- Extended model inventory with 11 total models across 3 categories
- 10-metric evaluation framework (accuracy, sensitivity, specificity, F1, MCC, ROC-AUC, PR-AUC, precision, recall, Brier score)
- McNemar statistical tests with Holm correction for pairwise model comparisons
- Calibration analysis with calibration curves and Brier scores
- Grad-CAM attention visualizations for model interpretability
- High-resolution figure exports (8.9 MB ZIP archive with 14 figures)

#### Models
- **Clinical models (5):** Logistic Regression, Random Forest, XGBoost, SVM (RBF), MLP
- **Image models (4):** EfficientNetB0, ResNet-50, DenseNet121, MobileNetV2
- **Fusion models (2):** Feature-level (concatenation), Late fusion (stacked)

#### Results
- Feature-level fusion: 89.0% accuracy, 0.957 ROC-AUC
- Image-based models: 79.0% - 85.5% accuracy
- Clinical-only models: 55.0% - 66.5% accuracy

#### Changed
- Methodological audit against dissertation completed
- Results validated against v04 outputs
- Patient-level data splitting refined

#### Technical
- TensorFlow 2.20.0
- Keras 3.0+
- GPU acceleration enabled
- Seed management (SEED=42) for reproducibility

---

## [v0.5.1] - 2026-08-16

### Corrected Release
Methodological audit completed against dissertation requirements.

#### Changes
- Corrected CBC variable extraction
- Validated patient-level splitting logic
- Confirmed 1,000 patients, 12 images each for AneRBC-II
- Rerun with updated configuration

#### Status
- All model architectures confirmed
- Hyperparameter tuning completed
- Ready for final evaluation

---

## [v0.5] - 2026-08-10

### Extended Experiments
Expanded model set and evaluation metrics.

#### Added
- Multiple image backbone architectures
- Fusion model implementations
- Extended evaluation metrics

#### Changes
- Increased model count from initial set
- Comprehensive metric suite added

---

## [v0.4] - 2026-07-30

### Initial Release
Core implementation with baseline models.

#### Features
- Data loading and preprocessing
- Train/validation/test splitting
- Baseline model implementations
- Initial results collection

---

## Version Numbering

Version format: `v[MAJOR].[MINOR]`

- **Major version**: Significant architectural changes or methodology updates
- **Minor version**: Bug fixes, hyperparameter tuning, added metrics
- **Development versions**: Intermediate iterations during experimentation

---

## Reproducibility

All experiments are reproducible with:
- SEED = 42 (fixed random states)
- AneRBC-II dataset (12,000 images, 1,000 patients)
- Patient-level train/val/test split (80/15/5)
- No data augmentation

---

## Known Limitations

1. **Balanced test set**: Performance metrics reflect balanced class distribution (500 anaemic, 500 healthy in test set). Real-world deployment may need recalibration.

2. **Low-level shortcuts**: Grad-CAM analysis suggests possible color-based shortcuts in image models. Further investigation needed.

3. **Clinical modality**: CBC variables alone achieve only 55-66% accuracy. More sophisticated feature engineering may improve performance.

4. **Calibration**: Models are well-calibrated but calibration is specific to this test cohort.

---

## Planned Future Work

- [ ] Investigate morphological feature extraction
- [ ] Explore attention mechanisms for fusion
- [ ] Test on external datasets
- [ ] Develop deployment-ready models with clinical validation
- [ ] Create API endpoint for predictions

---

## Citation

If referencing this project, cite the version number:

```
Shehnaz. Multimodal Deep Learning for Anaemia Classification (v0.6).
MSc Dissertation, CN7000, University of East London, 2026.
```

---

## Authors and Contributors

- **Shehnaz (3023411)** - Main implementation and analysis
- **Supervisors** - University of East London

---

## License

MIT License - See LICENSE file for details.
