# Setup Instructions

Follow these steps to get the project running on your machine.

## Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Git
- At least 8GB RAM (16GB recommended for GPU)
- GPU optional but recommended for faster training

## Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/anaemia-classification.git
cd anaemia-classification
```

## Step 2: Create a Virtual Environment

```bash
# On macOS/Linux
python3 -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate
```

## Step 3: Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

If you have a GPU and want to use it:

```bash
# For NVIDIA GPUs (CUDA)
pip install tensorflow-gpu==2.20.0
```

## Step 4: Download the Dataset

1. Go to https://data.mendeley.com/datasets/hms3sjzt7f/1
2. Download the AneRBC dataset files
3. Extract them to the `data/raw/` folder in your project

Your folder structure should look like:
```
data/raw/
├── anerbc-ii/
│   ├── anaemic/
│   │   └── original_images/
│   └── healthy/
│       └── original_images/
└── cbc_reports/
```

## Step 5: Verify Installation

Run Python and check if imports work:

```bash
python -c "import tensorflow; import pandas; import sklearn; print('All imports successful!')"
```

## Step 6: Run the Notebook

Start Jupyter:

```bash
jupyter notebook
```

Navigate to `notebooks/mdlforanaemiaclassificationv06.ipynb` and run the cells.

## Troubleshooting

### Issue: GPU not detected
**Solution:** Ensure CUDA and cuDNN are installed. Check with:
```bash
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

### Issue: Out of memory errors
**Solution:** Reduce batch size in the notebook from 32 to 16 or 8.

### Issue: Dataset not found
**Solution:** Double-check the path matches `CFG['data_dir']` in the notebook. Update if needed.

### Issue: Permission denied on macOS/Linux
**Solution:** Run:
```bash
chmod +x data/raw/
```

## Using the Models

The notebook trains and evaluates all models. Key sections:

1. **Data Preparation** (Section 2): Loads and splits the dataset
2. **Clinical Models** (Section 3): Trains CBC-based classifiers
3. **Image Models** (Section 4): Trains deep learning image classifiers
4. **Fusion Models** (Section 5): Combines clinical and image features
5. **Evaluation** (Section 6): Compares all models across metrics

Results are saved in `results/` and `output/` folders.

## Hardware Requirements

| Task | Minimum | Recommended |
|------|---------|------------|
| Running full notebook | 8GB RAM, CPU | 16GB RAM, GPU |
| Training image models | GPU preferred | NVIDIA RTX 2070+ |
| Inference only | 4GB RAM, CPU | 8GB RAM, any GPU |

## Computational Time

On NVIDIA RTX 3060:
- Full experiment: ~2-3 hours
- Individual model: 10-30 minutes
- Inference on 200 patients: ~2 minutes

On CPU:
- Full experiment: ~8-12 hours
- Inference slower by 10-20x

## Next Steps

1. Read the README.md for project overview
2. Check the notebook comments for detailed explanations
3. Review dissertation for methodology and results interpretation
4. Modify hyperparameters in the `CFG` dictionary to experiment

## Questions

If you encounter issues:
1. Check this file first
2. Verify dataset download
3. Ensure all dependencies are installed
4. Check TensorFlow/GPU setup

For technical questions about the model, refer to the dissertation document.
