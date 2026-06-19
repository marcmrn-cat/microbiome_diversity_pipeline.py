# microbiome_diversity_pipeline.py
**Overview**
This repository contains a robust, end-to-end Python pipeline for analyzing 16S rRNA amplicon and metagenomic sequencing data. It bridges the gap between raw taxonomic abundance tables (OTUs/ASVs) and clinical/behavioral metadata.
Designed for observational cohort studies, the script automatically computes core ecological metrics (Alpha and Beta diversity), performs non-parametric statistical testing, and generates publication-ready ordinations.
**Key Features**
- Alpha Diversity (Within-Sample): Calculates the Shannon Entropy Index to assess community richness and evenness. Automatically computes Kruskal-Wallis H-tests to determine statistical significance between host phenotypes.
- Beta Diversity (Between-Sample): Computes ecological distances using the Bray-Curtis dissimilarity metric, adjusting for relative abundances to prevent sequencing depth bias.
- Principal Coordinates Analysis (PCoA): Utilizes Metric Multidimensional Scaling (MDS) to project complex multi-dimensional microbial communities into readable 2D visualizations, highlighting clustering driven by host species or behavioral scores.
- Metadata Integration: Seamlessly aligns taxonomic count matrices with clinical metadata matrices, ensuring robust mapping of multi-variable traits (e.g., physiological vs. behavioral variables).
- Synthetic Cohort Generator: If no input files are detected, the pipeline will auto-generate a statistically sound mock dataset simulating an observational study comparing different Host Species and their Behavior Phenotypes.
**Dependencies**
- pandas & numpy (Matrix manipulation)
- scipy (Ecological distance metrics & non-parametric statistics)
- scikit-learn (Dimensionality reduction / MDS-PCoA)
- matplotlib & seaborn (Data visualization)
**Usage**
- Modify the CONFIG block inside the script to point to your specific OTU/ASV table and metadata CSV. Specify the target analytical variables, and run: python microbiome_diversity_pipeline.py --otu "your_asv_table.csv" --meta "your_metadata.csv"

the script outputs a comprehensive .csv integrating the metadata with Shannon indices and PCoA coordinates, alongside high-resolution .png scatter and box plots.
