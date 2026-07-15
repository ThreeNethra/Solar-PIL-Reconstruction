\# Machine Learning for Reconstruction of Solar Polarity Inversion Lines from Solar Filaments



!\[Python](https://img.shields.io/badge/Python-3.10+-blue.svg)

!\[PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-red.svg)

!\[License](https://img.shields.io/badge/License-MIT-green.svg)

!\[Status](https://img.shields.io/badge/Status-Completed-success.svg)



This repository contains the implementation, experiments, and results for my \*\*M.Sc. Physics Thesis\*\* at \*\*Indian Institute of Technology (BHU), Varanasi\*\*, focused on reconstructing \*\*solar polarity inversion lines (PILs)\*\* from solar filament observations using machine learning.



The work reproduces and extends the methodology proposed in the paper:



> \*\*Machine Learning for Reconstruction of Polarity Inversion Lines from Solar Filaments\*\*



using multiple solar filament datasets and evaluating reconstruction quality under different reference-point sampling strategies.



\---



\# Table of Contents



\- \[Project Overview](#project-overview)

\- \[Scientific Background](#scientific-background)

\- \[Objectives](#objectives)

\- \[Datasets](#datasets)

\- \[Methodology](#methodology)

\- \[Repository Structure](#repository-structure)

\- \[Experimental Results](#experimental-results)

\- \[Requirements](#requirements)

\- \[Installation](#installation)

\- \[Usage](#usage)

\- \[Results](#results)

\- \[Future Work](#future-work)

\- \[Citation](#citation)

\- \[License](#license)

\- \[Acknowledgements](#acknowledgements)



\---



\# Project Overview



Solar filaments are elongated structures suspended above the solar surface by magnetic fields. Since they are generally located along \*\*Polarity Inversion Lines (PILs)\*\*, filament observations can be used to reconstruct the underlying magnetic polarity distribution.



Direct magnetic field observations are unavailable for much of the historical solar record, whereas filament observations extend back more than a century.



This project investigates whether deep learning models can reconstruct solar polarity maps from filament observations, thereby enabling historical magnetic field reconstruction.



The project reproduces published work while also exploring additional datasets and reconstruction scenarios.



\---



\# Scientific Background



Polarity Inversion Lines represent the boundaries separating regions of opposite magnetic polarity on the Sun.



Understanding their evolution is essential for studying



\- Solar magnetic activity

\- Active regions

\- Solar cycles

\- Coronal mass ejections

\- Space weather forecasting



Since historical magnetograms are limited, reconstructing polarity maps from filament observations provides an alternative approach to studying long-term solar magnetic evolution.



\---



\# Objectives



The primary objectives of this work are:



\- Reproduce the published PIL reconstruction framework.

\- Train deep neural networks using historical filament observations.

\- Compare reconstruction quality across different reference-point step sizes.

\- Evaluate reconstruction performance using quantitative metrics.

\- Extend the original methodology using Meudon filament observations.

\- Explore reconstruction using Ca II K derived magnetograms.



\---



\# Datasets



The project utilizes three major datasets.



\## 1. McIntosh Synoptic Archive



Used for



\- Solar filament maps

\- Ground-truth polarity maps



Time span:



1954 – 2024



\---



\## 2. Meudon Filament Archive



Historical filament observations.



Time span:



1919 – 2003



\---



\## 3. Ca II K Predicted Magnetograms



Used for exploratory reconstruction experiments where polarity targets are derived from predicted magnetograms.



\---



\# Methodology



The reconstruction pipeline follows the methodology proposed in the reference paper.



The overall workflow is



```

Filament Map

&#x20;       │

&#x20;       ▼

Reference Point Sampling

&#x20;       │

&#x20;       ▼

Neural Network Training

&#x20;       │

&#x20;       ▼

Predicted Polarity Map

&#x20;       │

&#x20;       ▼

Evaluation (IoU \& Dice Score)

```



Experiments were conducted using multiple reference-point sampling strategies:



\- Step Size = 1

\- Step Size = 8

\- Step Size = 32

\- No Sampling (Original)



\---



\# Repository Structure



```

Solar\_PIL\_reconstruction/

│

├── data/

│   └── README.md

│

├── notebooks/

│   ├── Reconstruction\_for\_McIntosh\_Filaments.ipynb

│   ├── Reconstruction\_for\_Meudon\_Filaments.ipynb

│   └── Reconstruction\_for\_Meudon\_CaK\_Predicted\_Magnetogram.ipynb

│

├── results/

│   ├── McIntosh/

│   ├── Meudon/

│   ├── CaK\_based\_magnetogram/

│   └── Comparative Results/

│

├── requirements.txt

├── README.md

├── LICENSE

└── .gitignore

```



\---



\# Experimental Results



The repository contains



\- Reconstructed polarity maps

\- Ground truth comparisons

\- IoU analysis

\- Dice coefficient analysis

\- Comparative evaluation between McIntosh and Meudon datasets

\- Exploratory Ca II K reconstruction experiments



The experiments demonstrate successful reconstruction of polarity inversion structures from filament observations while highlighting the influence of reference-point sampling on reconstruction quality.



\---



\# Requirements



Python 3.10+



Major libraries include



```

numpy

matplotlib

torch

scikit-image

astropy

opencv-python

scipy

jupyter

```



Install dependencies using



```bash

pip install -r requirements.txt

```



\---



\# Installation



Clone the repository



```bash

git clone https://github.com/<username>/solar-pil-reconstruction.git

```



Move into the project



```bash

cd solar-pil-reconstruction

```



Install dependencies



```bash

pip install -r requirements.txt

```



\---



\# Usage



The experiments are provided as Jupyter notebooks.



Run any notebook in the `notebooks/` directory depending on the dataset of interest.



\- McIntosh reconstruction

\- Meudon reconstruction

\- Meudon → Ca II K reconstruction



Outputs and visualizations will be generated automatically.



\---



\# Results



The repository includes



✔ Reconstructed polarity maps



✔ Quantitative reconstruction metrics



✔ IoU comparisons



✔ Dice score comparisons



✔ Multiple reference-point sampling experiments



✔ Comparative evaluation across datasets



\---



\# Future Work



Potential extensions include



\- Transformer-based architectures

\- Physics-informed neural networks

\- Temporal reconstruction across multiple Carrington rotations

\- Uncertainty estimation

\- Solar cycle prediction using reconstructed magnetic maps

\- Full-disc historical magnetic field reconstruction



\---



\# Citation



If you use this repository in your research, please cite



```

Pranava Prakash J.



Machine Learning for Reconstruction of Solar Polarity Inversion Lines from Solar Filaments.



M.Sc. Thesis,

Department of Physics,

Indian Institute of Technology (BHU), Varanasi.

2026\.

```



\---



\# License



This project is released under the MIT License.



See the LICENSE file for details.



\---



\# Acknowledgements



This work was completed as part of the M.Sc. Physics programme at



\*\*Indian Institute of Technology (BHU), Varanasi\*\*



Special thanks to my thesis supervisor for continuous guidance and support throughout this research.



The implementation is based on the methodology presented in



\*\*Machine Learning for Reconstruction of Polarity Inversion Lines from Solar Filaments\*\*, with additional experiments and analyses performed as part of this thesis.

