## Repository Structure & Reproducing Results

All code for this project was developed and executed in **Google Colab** with GPU runtime / acceleration, as the pipeline involves large-scale graph construction, GNN / HGT training, evidence extraction, and LLM-based explanation generation that depend on a continuous runtime with shared memory.

The primary runnable notebook is:

**`notebooks/full-pipeline/DS_5500_Full-Pipeline_Comprehensive_Codebook.ipynb`** — This is the single end-to-end notebook that contains the full pipeline from data loading through model training, evaluation, re-ranking, and RAG-based explanation generation. **To reproduce results, run this notebook on Google Colab with a GPU runtime.**

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
