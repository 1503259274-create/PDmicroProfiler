# PDmicroProfiler

<p align="center">
  <img src="PDmicroProfiler_README_workflow.png" width="1200">
</p>

<p align="center">
An R package for profiling gut bacterial and viral signatures in Parkinson's disease
</p>

---

## Overview

PDmicroProfiler is an R package designed for integrated exploration of Parkinson's disease-associated gut bacteriome and virome.

The package supports:

- Bacterial abundance profiling
- Viral (vOTU) abundance profiling
- Functional annotation analysis
- Phage-host interaction exploration
- Bacteria–phage network visualization

---

## Installation

```r
# install.packages("devtools")
devtools::install_github("1503259274-create/PDmicroProfiler")
```

---

## Workflow

The workflow of PDmicroProfiler is shown below.

<p align="center">
  <img src="PDmicroProfiler_README_workflow.png" width="1200">
</p>

---

## Main Functionalities

### Abundance Profiling

```r
get_microbe_abundance()
plot_microbe_abundance()
```

### Phage Family Dashboard

```r
phage_family_dashboard()
plot_phage_summary()
```

### Functional Annotation

```r
get_ko_info()
get_pathway_info()
plot_votu_function()
plot_family_function()
plot_diff_pathway()
```

### Network Analysis

```r
find_phage_host_interactions()
plot_interaction_network()
plot_interaction_network_static()
```

---

## Citation

If you use PDmicroProfiler in your research, please cite:

> Integrated Metagenomics Tool PDmicroProfiler: A Novel R Package for Efficient Profiling of Gut Bacterial and Viral Signatures in Parkinson's Disease

---

## License

MIT License
