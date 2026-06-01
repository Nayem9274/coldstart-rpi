# A Cold-Start Benchmark and Architectural Diagnosis for RNA-Protein Interaction Prediction

This repository contains the code and experimental pipeline for our study on cold-start RNA–protein interaction prediction.

## Notebook Preview

GitHub may occasionally fail to render the main Jupyter notebook and show an error such as:

> An error occurred  
> Using nbformat v5.10.4 and nbconvert v7.17.1

If this happens, please use:

- **nbviewer:** https://nbviewer.org/github/Nayem9274/coldstart-rpi/blob/main/pipeline.ipynb
- **Google Colab:** https://colab.research.google.com/github/Nayem9274/coldstart-rpi/blob/main/pipeline.ipynb


## Reproducing the paper

Open `pipeline.ipynb` and run the cells listed below. Cells 1–30 define data loaders, models, training, and metrics — run them first.

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

### Trainable parameter counts

| Model             | Parameters |
|-------------------|------------|
| PairMLP           | 1,082,881  |
| PairMLP-Wide      | 3,312,129  |
| PairMLP-Deep      | 2,099,841  |
| PairMLP-Cross     | 1,610,241  |
| DegGate           | 2,267,334  |
| WeightedBipartite | 2,265,603  |
| CoNeighbor        | 2,004,483  |
| ProtoContrast     | 2,531,012  |
| GraphSAGE-2L      | 2,198,530  |

## Data

This project uses the same benchmark datasets and pre-computed RNA-FM /
ProtT5 embeddings as **ZHMolGraph** (RNA–protein interaction prediction
using network-guided deep learning — Liu et al., *Communications Biology*, 2025,  
DOI: [10.1038/s42003-025-07694-9](https://doi.org/10.1038/s42003-025-07694-9)).


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


