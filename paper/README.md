# BioHackathon 2025 on2vec Paper

This directory contains the BioHackrXiv paper for the on2vec project from BioHackathon Japan 2025.

## Files

- `paper.md` - Main paper content in Markdown format
- `paper.bib` - Bibliography with all citations
- `biohackrxiv.png` - BioHackrXiv logo
- `figures/` - All figures used in the paper (7 PNG files, 5.3M total)

## Figures Included

All figures have been copied from the on2vec repository and are ready for building:

1. **Figure 1**: `heatmap_sorted.png` - Performance heatmap across all models and tasks
2. **Figure 2**: `task_performance.png` - Task-specific performance with error bars
3. **Figure 3**: `model_performance.png` - Top model rankings
4. **Figure 4**: `hyperparameter_analysis.png` - Hyperparameter importance from Optuna
5. **Figure 5**: `ontology_analysis.png` - Performance by source ontology

## Building the Paper

Follow BioHackrXiv submission guidelines at: https://github.com/biohackrxiv/bhxiv-gen-pdf

Typically:
```bash
docker run -it --rm -v $(pwd):/work biohackrxiv/gen-pdf:latest paper.md
```

## Status

- [x] Paper content written based on git logs and project analysis
- [x] Authors populated from git committers
- [x] Bibliography completed with key references
- [x] All 5 main figures copied and referenced
- [ ] Tables need to be added (see ../PAPER_TODOS.md)
- [ ] Statistical analysis to be expanded

## Key Results

- 187 models benchmarked across 3 MTEB biomedical clustering tasks
- 559 total benchmark results
- Top model: sentence-transformers/all-MiniLM-L6-v2 baseline (0.5277 ± 0.262)
- Top ontology-enhanced: chiro-all-MiniLM additive GCN (0.4975 ± 0.220)
- Early fusion architectures significantly outperformed others

## References

Source repository: https://github.com/david4096/on2vec
