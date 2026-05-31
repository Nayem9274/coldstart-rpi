# A Cold-Start Benchmark and Architectural Diagnosis for RNA-Protein Interaction Prediction

Code and reproduction artifacts for our ICDM 2026 submission. The full
pipeline lives in `pipeline.ipynb`; pre-computed result CSVs and figures
are in `results/`.

## Setup

```bash
git clone <this-repo>
cd coldstart-rpi
pip install -r requirements.txt
```

Then download embeddings into `data/` following `data/README.md`.

## Reproducing the paper

Open `pipeline.ipynb` and run the cells listed below. Cells 1–30
define data loaders, models, training, and metrics — run them first.

## Results already included

For convenience, the case-study aggregated CSVs and figures are committed
under `results/`. They can be inspected without rerunning training.

- `caseA_retrieval_summary.csv` — Case Study A means/std over seeds
- `caseB1_perprotein_summary.csv` — Per-protein AUROC by degree bucket
- `caseB2_orphan_summary.csv` — Pooled AUROC by RNA train-degree bucket
- `caseB_raw_alledges.csv`, `caseA_raw_perRNA.csv` — raw per-instance logs

## Compute

All experiments were run in a Kaggle GPU environment (NVIDIA Tesla T4).
A complete five-fold run for one model takes ~1–2 minutes; a full
three-seed two-dataset case study completes in ~20–24 minutes.

## Data

This project uses the same benchmark datasets and pre-computed RNA-FM /
ProtT5 embeddings as ZHMolGraph (Liu et al., Communications Biology 2025).

Download from Zenodo: https://zenodo.org/records/14747845

Expected layout after extracting into this directory:

    data/
      NPInter2/
        interactions.csv
        rna_embeddings.pkl
        prot_embeddings.pkl
      RPI7317/
        interactions.csv
        rna_embeddings.pkl
        prot_embeddings.pkl
      TheNovel/
        npinter5_pairs.csv
        rna_embeddings.pkl
        prot_embeddings.pkl

The notebook's `BASE` variable points to this folder.


