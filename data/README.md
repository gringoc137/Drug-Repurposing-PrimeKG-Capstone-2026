# Data Directory

This folder contains data files used in the project. Due to file size constraints, the full PrimeKG dataset is **not included** in this repository and must be downloaded separately.

## Included Files

| File | Description |
|------|-------------|
| `sampleprimekg.xlsx` | A small sample of the PrimeKG dataset for quick inspection and reference. |

## Downloading the Full PrimeKG Dataset

The full Precision Medicine Knowledge Graph (PrimeKG) dataset is required to run the comprehensive pipeline notebook.

**Source:** [Harvard MIMS Lab – PrimeKG Repository](https://github.com/mims-harvard/PrimeKG)

### Option A: Direct download

1. Visit the [PrimeKG GitHub releases page](https://github.com/mims-harvard/PrimeKG).
2. Download `kg.csv` (the main knowledge graph file).
3. Place `kg.csv` in this `data/` directory.

### Option B: Download via Python (used in the Colab notebook)

The first cells of the comprehensive pipeline notebook handle the download automatically when running on Google Colab. No manual download is needed if you run the full notebook end-to-end.

## Dataset Overview

PrimeKG integrates 20 high-quality biomedical resources and contains:

- **~129,375 nodes** (drugs, diseases, genes/proteins, pathways, phenotypes, effects)
- **~4,000,000+ edges** across 10 biological scales
- **Relationship types:** indication, contraindication, drug–protein (target/enzyme/carrier/transporter), disease–protein, disease–phenotype, protein–protein interactions, and more

For full documentation, see: [Chandak, P., Huang, K. & Zitnik, M. (2023). *Building a knowledge graph to enable precision medicine.* Scientific Data, 10, 67.](https://doi.org/10.1038/s41597-023-01960-3)

## Important Notes

- Do **not** commit large data files (`.csv`, `.tsv`, `.parquet`) to Git. They are excluded by the `.gitignore` in the repo root.
- If using Google Colab, mount your Google Drive or use the notebook's built-in download cells to access the data at runtime.
