# Data sources

Raw data is **not** included in this repository. Obtain it from the original archives and place it in the folders below (which are git-ignored).

## McIntosh Level-3 synoptic maps
- Source: NOAA/NGDC solar imagery archive
- Format: FITS (`.fits.gz`), one file per Carrington Rotation
- Naming: `ptmc_compo_sm_YYYYMMDD_HHMMSS_crNNNNk_l3.fits.gz`
- Expected local path: `LEVEL3FITS/`

## Meudon filament maps
- Source: Observatoire de Paris — Meudon spectroheliograph archive
- Format: PNG, one file per Carrington Rotation (e.g. `1373.png`)
- Expected local path: `meudon_filaments/`
- Contact the Meudon Observatory / BASS2000 database for access terms before redistributing any of this data yourself.

## CaK-magnetogram-derived polarity map (CR 1957)
- Source: a separate machine-learning magnetogram-prediction project (exploratory validation target for Experiment 3)
- Not redistributed here — check licensing terms with the originating project if you need access.

## Carrington Rotation matching
Both McIntosh and Meudon files are indexed by Carrington Rotation number, which is used as the join key between archives during preprocessing.
