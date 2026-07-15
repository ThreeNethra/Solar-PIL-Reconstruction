<div align="center">

# 🌞 Machine Learning for Reconstruction of Solar Polarity Inversion Lines from Solar Filaments

### M.Sc. Physics Thesis • Indian Institute of Technology (BHU), Varanasi

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-Deep_Learning-EE4C2C?logo=pytorch&logoColor=white)](https://pytorch.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-success)](LICENSE)

Reconstructing **solar magnetic polarity maps** from **historical solar filament observations** using deep learning.

</div>

---

## Overview

Understanding the evolution of the Sun's magnetic field is fundamental to solar physics and space weather prediction. Unfortunately, direct observations of the solar magnetic field are available only for the modern observational era.

Solar filaments, however, have been systematically recorded for over a century. Since these filaments form preferentially along **Polarity Inversion Lines (PILs)**, they provide valuable information about the underlying magnetic field.

This project investigates whether a neural network can reconstruct polarity maps from filament observations, enabling reconstruction of historical solar magnetic fields where magnetograms are unavailable.

The implementation reproduces the methodology presented in the paper:

> **Machine Learning for Reconstruction of Polarity Inversion Lines from Solar Filaments**

while extending it with additional datasets and exploratory experiments.

---

# Results

<div align="center">

<img src="results/Side-by-side comparison of McIntosh-input and Meudon-input reconstruction performance using IoU and Dice scores.jpeg" width="900">

**Comparison of reconstruction quality using McIntosh and Meudon filament datasets.**

</div>

---

# Project Highlights

- Reproduction of a published machine learning framework for solar polarity reconstruction
- Reconstruction from both **McIntosh** and **Meudon** filament archives
- Exploratory reconstruction using **Ca II K predicted magnetograms**
- Evaluation under multiple reference-point sampling strategies
- Quantitative comparison using **IoU** and **Dice Score**
- Fully reproducible Jupyter notebooks

---

# Scientific Motivation

Solar filaments are elongated plasma structures suspended above the solar surface by magnetic fields. Their locations closely trace polarity inversion lines separating regions of opposite magnetic polarity.

Recovering polarity maps from filament observations allows researchers to investigate historical solar magnetic evolution far beyond the era of direct magnetograph measurements.

Applications include

- Solar cycle studies
- Space weather research
- Active region evolution
- Coronal mass ejections
- Long-term solar magnetic field reconstruction

---

# Methodology

```text
Filament Observation
          │
          ▼
Image Processing
          │
          ▼
Reference Point Sampling
          │
          ▼
Neural Network
          │
          ▼
Predicted Polarity Map
          │
          ▼
Quantitative Evaluation
(IoU • Dice Score)
```

Reference-point sampling experiments were performed for

| Step Size |
|-----------|
| 1 |
| 8 |
| 32 |
| None (Original)|

---

# Datasets

## McIntosh Archive

- Solar filament synoptic maps
- Ground-truth polarity maps
- Time span: **1954–2024**

---

## Meudon Filament Archive

- Historical filament observations
- Time span: **1919–2003**

---

## Ca II K Predicted Magnetograms

Used for exploratory reconstruction experiments where polarity targets are derived from predicted magnetograms.

---

# Repository Structure

```text
Solar_PIL_reconstruction
│
├── data/
│   └── README.md
│
├── notebooks/
│   ├── Reconstruction_for_McIntosh_Filaments.ipynb
│   ├── Reconstruction_for_Meudon_Filaments.ipynb
│   └── Reconstruction_for_Meudon_CaK_Predicted_Magnetogram.ipynb
│
├── results/
│   ├── McIntosh/
│   ├── Meudon/
│   ├── CaK_based_magnetogram/
│   └── Comparison/
│
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```

---

# Installation

Clone the repository

```bash
git clone https://github.com/ThreeNethra/Solar-PIL-Reconstruction
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

# Usage

The project consists of three independent Jupyter notebooks.

| Notebook | Description |
|-----------|-------------|
| Reconstruction_for_McIntosh_Filaments.ipynb | Reconstruction using McIntosh filament observations |
| Reconstruction_for_Meudon_Filaments.ipynb | Reconstruction using Meudon filament observations |
| Reconstruction_for_Meudon_CaK_Predicted_Magnetogram.ipynb | Exploratory reconstruction using Ca II K derived magnetograms |

Run the notebook corresponding to the desired experiment.

---

# Experimental Outputs

The repository includes

- Reconstructed polarity maps
- Ground-truth comparisons
- Quantitative IoU evaluation
- Dice coefficient analysis
- Comparative performance across datasets
- Exploratory Ca II K reconstruction

---

# Technologies Used

| Category | Tools |
|-----------|------|
| Programming | Python |
| Deep Learning | PyTorch |
| Image Processing | scikit-image |
| Astronomy | Astropy |
| Scientific Computing | NumPy, SciPy |
| Visualization | Matplotlib |
| Development | Jupyter Notebook |

---

# Future Work

Possible future extensions include

- Physics-informed neural networks
- Vision Transformers
- Temporal polarity reconstruction
- Historical Carrington Rotation reconstruction
- Solar cycle forecasting
- Uncertainty-aware reconstruction

---

# Citation

If this repository contributes to your research, please cite:

```bibtex
@mastersthesis{Pranava2026,
  author       = {Pranava Prakash J},
  title        = {Machine Learning for Reconstruction of Solar Polarity Inversion Lines from Solar Filaments},
  school       = {Indian Institute of Technology (BHU), Varanasi},
  year         = {2026},
  type         = {M.Sc. Thesis}
}
```

---

# Acknowledgements

This work was completed as part of the **M.Sc. Physics programme** at **Indian Institute of Technology (BHU), Varanasi**.

The implementation reproduces and builds upon the methodology proposed in the paper:

> **Machine Learning for Reconstruction of Polarity Inversion Lines from Solar Filaments**

with additional experimental evaluation using multiple filament datasets.

---

# License

Distributed under the MIT License.

See the **LICENSE** file for details.
