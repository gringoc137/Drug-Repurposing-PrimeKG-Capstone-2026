# Drug–Disease Repurposing Using Graph Neural Networks on a Biomedical Knowledge Graph (PrimeKG). 

#### Drug Repurposing & Disease Similarity on PrimeKG using GNNs and Explainable Graph-Based Evidence. 

## Project Description

This project focuses on predicting potential **drug–disease relationships** using a **biomedical knowledge graph** and **Graph Neural Networks (GNNs)**. The main idea is to represent biomedical entities such as drugs, diseases, proteins, phenotypes, and effects as nodes in a graph, and represent their known relationships as edges. Once the graph is built, machine learning models can learn patterns in the graph structure and predict missing or potential therapeutic links.

The project combines **data preprocessing**, **knowledge graph construction**, **graph-based modeling**, and **evaluation** to explore how graph learning can support biomedical discovery.

---

## Team Members

- Athul Dinesh
- Dilep Shetty Ittanguru Venkatesh
- Stuti Jandhyala

---

## Problem Statement

Drug discovery and treatment recommendation are complex problems because biomedical knowledge is spread across many connected entities such as diseases, proteins, phenotypes, and known drug actions. Traditional tabular methods may fail to fully capture these complex relationships.

This project addresses the problem of:

**Can we use a biomedical knowledge graph and graph neural networks to predict meaningful drug–disease links?**

In particular, we aim to model known relationships between biomedical entities and use those graph patterns to identify potential therapeutic associations.

---

## Project Objectives

The main objectives of this project are:

1. Build a clean and structured **biomedical knowledge graph** from relational data.
2. Preprocess and normalize entity and relationship information for graph construction.
3. Represent the data as a **heterogeneous graph** with multiple node and edge types.
4. Train graph-based machine learning models for **link prediction**.
5. Compare model behavior and evaluate how well the learned graph embeddings capture drug–disease relationships.
6. Interpret results and identify possible improvements for future work.

---

## Dataset Description

The project uses a biomedical relational dataset containing multiple entity types and relationship categories. These include drugs, diseases, proteins, phenotypes, and effects, connected through biologically meaningful edges.

### Entity Types
- Drug
- Disease
- Protein
- Phenotype
- Effect

### Positive Relationships
- `indication`: drug → indication → disease
- `disease_protein`: disease → associated with → protein
- `drug_protein`: drug → carrier/enzyme/target/transporter → protein
- `phenotype_protein`: phenotype → associated with → protein
- `disease_phenotype_positive`: disease → phenotype present → phenotype

### Similarity Relationships
- `disease_disease`: disease → parent-child → disease
- `phenotype_phenotype`: phenotype → parent-child → phenotype
- `protein_protein`: protein → ppi → protein

### Negative Relationships
- `contraindication`: drug → contraindication → disease
- `drug_effect`: drug → side effect → effect

### Dataset Role in the Project
The dataset is used to:
- construct the biomedical knowledge graph,
- define node and edge types,
- generate training, validation, and test edges,
- support link prediction experiments.

---

## Methods and Models

This project follows a graph-based machine learning workflow.

### 1. Data Preprocessing
The raw data is cleaned and standardized before graph construction. This includes:
- selecting relevant columns,
- normalizing entity and relation labels,
- creating canonical identifiers,
- removing duplicates,
- organizing relationships into consistent formats.

### 2. Knowledge Graph Construction
The cleaned relational data is converted into a **heterogeneous knowledge graph** where:
- nodes represent biomedical entities,
- edges represent typed relationships between those entities.

### 3. Graph Representation
The graph is transformed into a format compatible with **PyTorch Geometric**, specifically a `HeteroData` object that stores:
- node indices,
- node types,
- edge indices,
- edge types.

### 4. Models Used
The project currently explores:

- **Baseline Heterogeneous GNN**
- **Heterogeneous Graph Transformer (HGT)**

These models learn node embeddings and use them to predict whether a link between a drug and a disease is likely to exist.

### 5. Evaluation
The models are evaluated using link prediction performance on held-out edges. The evaluation process helps compare model effectiveness and understand whether the graph structure is informative for prediction.

---

## Repository Structure & Reproducing Results

All code for this project was developed and executed in **Google Colab** with GPU runtime / acceleration, as the pipeline involves large-scale graph construction, GNN / HGT training, evidence extraction, and LLM-based explanation generation that depend on a continuous runtime with shared memory.

The notebooks in **`notebooks/modules/`** are **modular excerpts** of the comprehensive notebook, separated by stage for easier reading and review:

```
notebooks/
├── full-pipeline/
│   └── DS_5500_Full-Pipeline_Comprehensive_Codebook.ipynb
├── modules/
│   ├── 1.Environment_setup.ipynb
│   ├── 2.Data_loader.ipynb
│   ├── 3.Preprocessing_pipeline+Hetro._graph_builder.ipynb
│   ├── 4.EDA_visualizations.ipynb
│   ├── 5.Train_Val_Test_split+PyG_HeteroData.ipynb
│   ├── 6.Model_Baseline_GNN+Model_HGT_train.ipynb
│   ├── 7.Model_evaluation_metrics.ipynb
│   ├── 8.Re-rank+evidence_safety+similarity_block.ipynb
│   ├── 9.run_demo()_pipeline.ipynb
│   └── A.Demo_Sample_output_blocks.ipynb
└── notebooks_README.md
```

The primary runnable notebook is:

**`notebooks/full-pipeline/DS_5500_Full-Pipeline_Comprehensive_Codebook.ipynb`** — This is the single end-to-end notebook that contains the full pipeline from data loading through model training, evaluation, re-ranking, and RAG-based explanation generation. **To reproduce results, run this notebook on Google Colab with a GPU runtime.**
- (built / dev. in **Google Colab A100/L4/T4**).

These modular notebooks are **not independently runnable** — they are provided for code review and documentation purposes only.

The notebooks in **`notebooks/modules/`** are **modular excerpts** of the comprehensive notebook, separated by stage for easier reading and review:

| Notebook | Stage |
|----------|-------|
| `1.Environment_setup` | Dependencies and environment configuration |
| `2.Data_loader` | Loading and inspecting the PrimeKG dataset |
| `3.Preprocessing_pipeline+Hetro._graph_builder` | Data cleaning, normalization, and heterogeneous graph construction |
| `4.EDA_visualizations` | Exploratory data analysis and graph statistics |
| `5.Train_Val_Test_split+PyG_HeteroData` | Train/validation/test edge splits and PyG HeteroData preparation |
| `6.Model_Baseline_GNN+Model_HGT_train` | Baseline heterogeneous GNN and HGT model training |
| `7.Model_evaluation_metrics` | Classification, ranking, and safety metric evaluation |
| `8.Re-rank+evidence_safety+similarity_block` | Evidence extraction, safety filtering, disease similarity, and re-ranking |
| `9.run_demo()_pipeline` | End-to-end demo pipeline for a given disease query |
| `A.Demo_Sample_output_blocks` | Sample output showing predicted drugs, evidence paths, and explanations |

. 

---

### Dataset Link: https://github.com/mims-harvard/PrimeKG?tab=readme-ov-file 
---
## System Design / Overview 


<img width="1637" height="1445" alt="Final - SD drawio" src="https://github.com/user-attachments/assets/7232720a-a901-400c-8472-d3f71e4fac05" /> 
