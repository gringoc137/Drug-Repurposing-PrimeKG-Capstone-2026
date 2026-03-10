# Drug–Disease Link Prediction Using a Biomedical Knowledge Graph

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

### Dataset Link: https://github.com/mims-harvard/PrimeKG?tab=readme-ov-file 


<img width="350" height="550" alt="image" src="https://github.com/user-attachments/assets/f61e86b1-8773-4ce9-80cd-e353ff5fa622" />
