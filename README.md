# Efficiently Adapting SAM 2 for Hand-Drawn Circuit Diagram Segmentation

[![arXiv](https://img.shields.io/badge/arXiv-24XX.XXXXX-b31b1b.svg)](https://arxiv.org/abs/24XX.XXXXX) <!-- ### TODO: Replace with your arXiv ID and link -->
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/release/python-390/)
[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat&logo=PyTorch&logoColor=white)](https://pytorch.org/)

Official PyTorch implementation for the paper: **"Efficiently Adapting SAM 2 for Hand-Drawn Circuit Diagram Segmentation in a Low-Data Regime"**.

This repository contains the code for fine-tuning the Segment Anything Model 2 (SAM 2) with Low-Rank Adaptation (LoRa) and a custom Multi-Kernel Refinement (MKR) layer for high-fidelity segmentation of hand-drawn circuit diagrams, specifically designed for low-data scenarios.

![Qualitative Results from our model](assets/qualitative_results.png) <!-- ### TODO: Make sure this image exists in an 'assets' folder -->

---

## Repository Structure

```
sam2-circuit-segmentation/
│
├── assets/
│   └── qualitative_results.png      # Images for the README
│
├── notebooks/
│   ├── sam-2-circuits-training-peft.ipynb  # Main notebook for training the model using PEFT (LoRa).
│   ├── segmentation-model-inference.ipynb  # Notebook for running inference with a trained model.
│   └── segmentation-plots-zero-shot.ipynb  # Notebook to replicate the zero-shot SAM 2 results.
│
├── download_models.py             # Script to download the pre-trained SAM 2 model weights.
├── requirements.txt               # Required Python packages.
└── README.md                      # This file.
```

---

## Setup and Installation

Follow these steps to set up the environment and dependencies.

### 1. Clone the Repository
```bash
git clone https://github.com/mah-sam/sam2-circuit-segmentation.git
cd sam2-circuit-segmentation
```

### 2. Create a Virtual Environment (Recommended)
```bash
# For Linux/macOS
python3 -m venv venv
source venv/bin/activate

# For Windows
python -m venv venv
.\venv\Scripts\activate
```

### 3. Install Dependencies
Install the required Python packages using pip.
```bash
pip install -r requirements.txt
```

---

## Usage Instructions

### 1. Download Pre-trained Models
Run the provided script to download the official SAM 2 (Hiera-L) pre-trained model weights. The weights will be saved to a `models` directory.
```bash
python download_models.py
```

### 2. Prepare the Dataset
This work uses a subset of the **Circuit Graph Hand-Drawn dataset (CGHD-1152)**.
- Download the dataset from the [official source]([https://github.com/thoma/CGHD](https://www.kaggle.com/datasets/johannesbayer/cghd1152)).
- It's better to use Kaggle since it was trained on it, and the data is stored on Kaggle too

### 3. Run the Notebooks
The `notebooks/` directory contains Jupyter notebooks to replicate our findings.

- **`segmentation-plots-zero-shot.ipynb`**: Demonstrates the zero-shot performance of the base SAM 2 model on circuit diagrams.
- **`sam-2-circuits-training-peft.ipynb`**: This is the core notebook for fine-tuning the model with LoRa. You can configure hyperparameters, data paths, and run the training process here.
- **`segmentation-model-inference.ipynb`**: After training, use this notebook to load your fine-tuned model checkpoint and perform segmentation on new, unseen circuit diagrams.

---

## Citation

If you find this work useful for your research, please consider citing our paper:

```bibtex
@misc{sameh2025efficiently,
      title={Efficiently Adapting SAM 2 for Hand-Drawn Circuit Diagram Segmentation in a Low-Data Regime}, 
      author={Mahmoud Sameh and Adel Abdennour and Jawad K. Ali},
      year={2025},
      eprint={24XX.XXXXX},      -- ### TODO: Replace with your arXiv ID
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

---

## License

This project is licensed under the MIT License. See the [LICENSE](https://opensource.org/licenses/MIT) file for details.
