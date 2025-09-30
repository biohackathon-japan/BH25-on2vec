# BioHackathon 2025 on2vec Paper - TODO Items

This document outlines the remaining tasks to complete the paper for publication.

## High Priority - Figures

### 1. MTEB Benchmark Performance Figures
**Location**: `paper/figures/` (copied from `../on2vec/mteb_visualizations/`)

- [x] **Figure 1: Model Performance Heatmap** (`heatmap_sorted.png`) ✅ ADDED TO PAPER
  - Shows comparative performance across all models and tasks
  - Included in Results section
  - Caption: "Performance heatmap of ontology-enhanced models across MTEB biomedical clustering tasks"

- [x] **Figure 2: Task Performance Analysis** (`task_performance.png`) ✅ ADDED TO PAPER
  - Average performance per task with error bars
  - Shows ClusTREC-Covid (0.7287), BiorxivClusteringS2S (0.2670), BiorxivClusteringP2P (0.2628)
  - Caption: "Average model performance across biomedical clustering tasks with standard deviation"

- [x] **Figure 3: Model Comparison Bar Chart** (`model_performance.png`) ✅ ADDED TO PAPER
  - Top models ranked by average score
  - Shows vanilla sentence-transformers baseline (0.5277) vs ontology-enhanced models
  - Caption: "Comparison of top model performance on biomedical clustering tasks"

### 2. Hyperparameter Optimization Results
**Location**: `paper/figures/` (copied from `../on2vec/mteb_visualizations/`)

- [x] **Figure 4: Hyperparameter Importance** (`hyperparameter_analysis.png`) ✅ ADDED TO PAPER
  - Shows relative importance of different hyperparameters
  - Discussion included: output dimension and learning rate as most important
  - Caption: "Hyperparameter importance from Optuna optimization"

### 3. Architecture Comparison
**Location**: `paper/figures/` (copied from `../on2vec/mteb_visualizations/`)

- [x] **Figure 5: Ontology Analysis** (`ontology_analysis.png`) ✅ ADDED TO PAPER
  - Performance breakdown by ontology type
  - Shows which ontologies benefit most from different architectures
  - Caption: "Performance breakdown by source ontology showing domain-specific patterns"

## Medium Priority - Tables

### 1. Main Results Table
- [ ] **Table 1: Top 10 Model Performance**
  - Extract from `../on2vec/mteb_visualizations/mteb_results.csv` or `summary_statistics.txt`
  - Columns: Rank, Model Name, Architecture, Avg Score, Std Dev, Best Task
  - Include the vanilla baseline and top ontology-enhanced models
  - Data available: 187 models total, top performer is sentence-transformers baseline (0.5277)

Example structure:
```
| Rank | Model | Architecture | Score | ±Std | Best Task |
|------|-------|--------------|-------|------|-----------|
| 1 | all-MiniLM-L6-v2 (vanilla) | - | 0.5277 | 0.262 | ClusTREC-Covid |
| 2 | chiro-all-MiniLM-additive-gcn-512-128 | Additive GCN | 0.4975 | 0.220 | ... |
| ... |
```

### 2. Ontology Coverage Table
- [ ] **Table 2: Ontologies Processed**
  - List all ontologies trained during the hackathon
  - Columns: Ontology, Abbreviation, Domain, # Classes, # Relations, Models Trained
  - Known ontologies from data:
    - EDAM (Bioinformatics operations)
    - Cell Ontology (CL)
    - Apollo Structured Vocabulary (APOLLO_SV)
    - Animal Gross Pathology Ontology (AGRO)
    - Adverse Drug Ontology (ADO)
    - Ascomycete Phenotype Ontology (APO)
    - AMPHX, AFPO, and many more (see model names in results)

### 3. Architecture Configuration Table
- [ ] **Table 3: Model Architecture Details**
  - Columns: Architecture Type, Hidden Dims, Output Dims, Loss Function, Fusion Method, # Parameters
  - Document the main configuration variants tested:
    - GCN with concat fusion (128/64)
    - GAT with attention fusion (1024/384)
    - Additive fusion variants (512/128, 512/256)
    - Cross-entropy vs cosine loss comparisons

## Low Priority - Additional Materials

### 1. Supplementary Figures
- [ ] **Supp Fig 1: Pairwise Model Comparison** (`pairwise_comparison.png`)
  - Detailed head-to-head comparisons
  - Could be supplementary material

- [ ] **Supp Fig 2: Task Difficulty Matrix** (`task_difficulty_matrix.png`)
  - Shows correlation between task difficulty and model performance
  - Could be supplementary material

### 2. Code Examples
- [ ] Add code snippet showing typical usage workflow in Results section
- [ ] Add example of model loading and inference

### 3. HuggingFace Model Cards
- [ ] List uploaded models with links to HuggingFace Hub
- [ ] Document model naming convention used
- [ ] Models available at: https://huggingface.co/david4096 and https://huggingface.co/ellisdoro

## Data Analysis Needed

### 1. Statistical Comparisons
- [ ] Calculate statistical significance between vanilla baseline and top ontology models
- [ ] Perform paired t-tests across tasks
- [ ] Report effect sizes

### 2. Architecture Analysis
- [ ] Summary: Early Fusion (164 models, avg 0.4344 ± 0.219) vs Other (23 models, avg 0.3077 ± 0.303)
- [ ] Analyze why vanilla baseline outperforms ontology models
- [ ] Investigate task-specific performance patterns

### 3. Hyperparameter Study Results
- [ ] Extract Optuna pareto front results (if available in `../on2vec/`)
- [ ] Document optimal hyperparameter ranges per ontology type
- [ ] Report convergence statistics

## Writing Enhancements

### 1. Methods Section Expansion
- [ ] Add detailed description of evaluation metrics
- [ ] Explain train/test split methodology
- [ ] Document computational resources used

### 2. Results Section
- [ ] Add quantitative comparison between fusion methods
- [ ] Report best configurations per ontology
- [ ] Discuss failure modes and limitations

### 3. Discussion
- [ ] Explain why vanilla baseline outperforms in some cases
- [ ] Discuss when ontology structure helps vs hurts
- [ ] Relate findings to Menad et al. 2024 work on BioSTransformers

## File Locations Reference

**Paper figures directory**: `paper/figures/`
All figures have been copied from `../on2vec/mteb_visualizations/` and are ready for paper build:
- ✅ `heatmap_sorted.png` (1.7M) - Figure 1
- ✅ `task_performance.png` (156K) - Figure 2
- ✅ `model_performance.png` (1.6M) - Figure 3
- ✅ `hyperparameter_analysis.png` (376K) - Figure 4
- ✅ `ontology_analysis.png` (857K) - Figure 5
- ✅ `model_comparison.png` (444K) - Available for supplementary
- ✅ `training_example.png` (123K) - Available if needed

**Source data locations**:
- `../on2vec/mteb_visualizations/mteb_results.csv` - raw data for tables
- `../on2vec/mteb_visualizations/summary_statistics.txt` - pre-computed statistics
- `../on2vec/evaluation_results/plots/` - training progress plots and loss curves

## Notes

- The paper currently has 187 models benchmarked across 3 tasks
- Total of 559 benchmark results collected
- Vanilla all-MiniLM-L6-v2 achieved best performance (0.5277 ± 0.262)
- Top ontology-enhanced model: chiro-all-MiniLM with additive GCN (0.4975 ± 0.220)
- Early fusion approaches significantly outperformed other architectures

## Timeline Suggestions

1. **Week 1**: Add main figures (Figures 1-3) and Table 1
2. **Week 2**: Add hyperparameter analysis (Figure 4-5) and architecture tables
3. **Week 3**: Statistical analysis and discussion expansion
4. **Week 4**: Supplementary materials and final polishing
