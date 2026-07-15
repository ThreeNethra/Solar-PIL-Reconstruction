# Bridging the Magnetogram Gap

Physics-informed neural reconstruction of solar Polarity Inversion Lines (PILs) from historical filament archives.

> MSc thesis project, Department of Physics, Indian Institute of Technology (BHU) Varanasi.
> Supervisor: Dr. Bidya Binay Karak.

## Overview

Direct magnetogram measurements of the Sun's magnetic polarity only go back a few decades, but filament observations extend much further into the past. Filaments form preferentially along polarity inversion lines (where the radial field changes sign), so filament geometry carries indirect information about historical polarity structure — but on its own it can't resolve *which side* of a filament is positive vs. negative.

This project implements and extends a physics-informed neural network (PINN) approach that reconstructs a continuous polarity field from filament locations, sparse polarity reference points, and physical constraints (boundary conditions, magnetic neutrality). The zero-level contour of the learned field is the reconstructed PIL.

It builds on and reproduces the method from:

> Kisielius, V. & Illarionov, E. (2024). *Machine Learning for Reconstruction of Polarity Inversion Lines from Solar Filaments.* Solar Physics, 299(5), 69. [DOI: 10.1007/s11207-024-02324-9](https://doi.org/10.1007/s11207-024-02324-9) · [arXiv:2405.06293](https://arxiv.org/abs/2405.06293)

Original reference implementation: *(link to Kisielius & Illarionov's repo here if public — check their license before reusing code directly)*.

## What's in this repo

Three experiments, each trained per-Carrington-Rotation with a 100-member network ensemble:

| Experiment | Filament input | Polarity target | Purpose |
|---|---|---|---|
| 1 | McIntosh | McIntosh | Reproduce the original paper |
| 2 | Meudon | McIntosh | Test an independent filament archive against the same target |
| 3 | Meudon | CaK-magnetogram-derived (CR 1957) | Exploratory: independent target source |

**Model:** fully connected MLP, `[3, 6, 12, 24, 12, 6, 3, 1]` (823 parameters). Inputs are spatial coordinates; output is a scalar polarity field. Ensembles of 100 independently initialized networks are trained per Carrington Rotation; the ensemble mean gives the polarity prediction and ensemble disagreement gives an uncertainty estimate.

**Evaluation:** IoU, Dice, Precision, Recall (macro-averaged over both polarity classes), averaged across 10 Carrington Rotations (1355, 1359, 1363, 1367, 1371, 1373, 1377, 1381, 1387, 1390) spanning solar minimum through decline, at four reference-point densities (step sizes 1, 8, 32, and none).

## Key results

| Reference step size | McIntosh→McIntosh IoU | Meudon→McIntosh IoU | Meudon→CaK IoU |
|---|---|---|---|
| 1 | 0.899 | 0.867 | 0.706 |
| 8 | 0.898 | 0.859 | 0.695 |
| 32 | 0.828 | 0.780 | 0.567 |
| None | 0.509 | 0.528 | 0.440 |

Headline finding: an independent filament archive (Meudon) can reconstruct McIntosh polarity maps at only a ~0.04 IoU penalty relative to using McIntosh's own filaments — suggesting the network is learning genuine physical structure rather than archive-specific quirks. Sparse reference points remain essential; without them, performance collapses close to random.

See `results/` for full figures and `docs/` (or the thesis, if shared separately) for detailed discussion.

## Repository structure

```
.
├── src/
│   ├── data/            # build_image_data() variants for each experiment
│   ├── model.py          # NeutralLiner architecture
│   ├── train.py          # ensemble training loop
│   └── evaluate.py       # IoU / Dice / Precision / Recall computation
├── notebooks/
│   └── demo.ipynb        # end-to-end demo on a single Carrington Rotation
├── results/               # generated figures (ensemble means, bar charts) — small files only
├── data/
│   └── README.md          # where to obtain McIntosh / Meudon / magnetogram data (not the data itself)
├── requirements.txt
├── LICENSE
└── README.md
```

## Getting the data

This repo does **not** redistribute the raw datasets. See `data/README.md` for:
- McIntosh Level-3 synoptic maps (NOAA/NGDC archive)
- Meudon filament maps (Observatoire de Paris / Meudon)
- CaK-magnetogram-derived polarity map (CR 1957)

Download these separately and point the scripts at your local copy — see `data/README.md` for expected folder layout.

## Setup

```bash
git clone https://github.com/<your-username>/pil-reconstruction.git
cd pil-reconstruction
pip install -r requirements.txt
```

## Usage

```bash
# Train an ensemble for one Carrington Rotation
python src/train.py --cr 1373 --experiment mcintosh --step-size 8

# Evaluate a trained ensemble
python src/evaluate.py --cr 1373 --experiment mcintosh --step-size 8
```

*(adjust to your actual CLI/argument names)*

## Citation

If you use this code, please cite the original method paper:

```bibtex
@article{kisielius2024pil,
  title={Machine Learning for Reconstruction of Polarity Inversion Lines from Solar Filaments},
  author={Kisielius, Vaclovas and Illarionov, Egor},
  journal={Solar Physics},
  volume={299},
  number={5},
  pages={69},
  year={2024},
  doi={10.1007/s11207-024-02324-9}
}
```

## License

Code in this repository is released under the MIT License (see `LICENSE`) unless otherwise noted. This does **not** cover:
- Third-party datasets (McIntosh, Meudon, magnetogram products) — subject to their originators' terms.
- The written thesis document, which is copyrighted by the Indian Institute of Technology (Banaras Hindu University), Varanasi.

## Acknowledgements

Thanks to Dr. Bidya Binay Karak (supervisor) and Mr. Rohan B. Mandrai for guidance during this project, and to Kisielius & Illarionov for the original reconstruction methodology.
