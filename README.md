# PDmicroProfiler

<p align="center">
  <img src="PDmicroProfiler_README_workflow.png" width="1200">
</p>

<p align="center">
  <strong>An R package for exploring Parkinson's disease-associated gut bacteriome, virome, and phage–bacteria interactions</strong>
</p>

---

## Overview

**PDmicroProfiler** is an R package designed for standardized exploration and visualization of Parkinson's disease (PD)-associated gut bacterial and viral signatures.

The package integrates processed multi-cohort metagenomic resources and provides a unified framework for:

- querying bacterial and viral abundance profiles;
- comparing microbial features between PD and healthy control groups;
- exploring viral operational taxonomic units (vOTUs);
- summarizing phage family characteristics;
- visualizing viral functional annotations;
- investigating phage-host and bacteria–phage interaction networks.

PDmicroProfiler was developed to make PD-associated gut microbiome and virome resources easier to access, visualize, and interpret.

---

## Background

Parkinson's disease has been increasingly linked to alterations in the gut microbial ecosystem. However, compared with bacterial communities, the viral component of the gut microbiome, especially bacteriophages, remains relatively underexplored.

PDmicroProfiler was developed from an integrated multi-cohort metagenomic analysis of PD and healthy control fecal samples. It supports reproducible investigation of gut bacterial taxa, viral vOTUs, viral functional features, and inferred bacteria–phage interaction patterns.

---

## Installation

You can install the development version of **PDmicroProfiler** from GitHub using `remotes`:

```r
# install.packages("remotes")
remotes::install_github("1503259274-create/PDmicroProfiler")
````

Alternatively，you can use devtools:

```r
# install.packages("devtools")
devtools::install_github("1503259274-create/PDmicroProfiler")
```

Load the package:

```r
library(PDmicroProfiler)
```

---

## Main features

PDmicroProfiler contains four major functional modules.

| Module                          | Description                                                                             | Representative functions                                                                                                          |
| ------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Microbial abundance profiling   | Query and visualize bacterial taxa or viral vOTUs across PD and healthy control samples | `get_microbe_abundance()`, `plot_microbe_abundance()`                                                                             |
| Phage database exploration      | Query phages by host, family, lifestyle, specialization, and novelty status             | `query_by_host()`, `query_by_id()`, `phage_family_dashboard()`, `plot_phage_summary()`                                            |
| Viral functional annotation     | Retrieve and visualize vOTU-level and family-level KEGG Ortholog annotations            | `get_votu_info()`, `get_ko_info()`, `get_pathway_info()`, `plot_votu_function()`, `plot_family_function()`, `plot_diff_pathway()` |
| Bacteria–phage network analysis | Identify and visualize phage-host or bacteria–phage interaction networks                | `find_phage_host_interactions()`, `plot_interaction_network()`, `plot_interaction_network_static()`                               |

---

## Data resources

PDmicroProfiler includes processed data resources generated from multi-cohort PD gut metagenomic datasets.

| Data type                   | Description                                                             |
| --------------------------- | ----------------------------------------------------------------------- |
| Bacterial abundance         | Bacterial abundance profiles for PD and healthy control samples         |
| Viral vOTU abundance        | Viral operational taxonomic unit abundance profiles                     |
| Sample metadata             | Group and cohort information                                            |
| Viral taxonomy              | Family-level and vOTU-level viral taxonomic annotations                 |
| Viral functional annotation | KEGG Ortholog and pathway annotations for vOTUs                         |
| Phage-host links            | Predicted associations between phages and bacterial hosts               |
| Interaction networks        | Bacteria–phage association networks for PD, HC, and shared interactions |

---

## Quick start

### 1. Query microbial abundance

```r
library(PDmicroProfiler)

abund_df <- get_microbe_abundance(
  microbe = "Bifidobacterium catenulatum"
)

head(abund_df)
```

---

### 2. Visualize abundance differences

```r
plot_microbe_abundance(
  microbe = "Bifidobacterium catenulatum"
)
```

This function can be used to visualize abundance differences between PD and healthy control samples.

---

### 3. Explore viral family abundance

```r
plot_microbe_abundance(
  microbe = "Podoviridae"
)
```

This example can be used to inspect viral family-level abundance patterns.

---

### 4. Query phages by host

```r
phage_hits <- query_by_host(
  host = "Firmicutes",
  lifestyle = "Temperate",
  specialization = "Specialist"
)

head(phage_hits)
```

Summarize the family composition of retrieved phages:

```r
plot_phage_summary(phage_hits)
```

---

### 5. Generate a phage family dashboard

```r
phage_family_dashboard(
  family = "Siphoviridae"
)
```

The dashboard summarizes genome length distribution, host distribution, lifestyle, host specialization, and novelty status for a selected phage family.

---

### 6. Query vOTU information

```r
votu_info <- get_votu_info(
  votu_id = "DRR480285__12620"
)

votu_info
```

---

### 7. Visualize vOTU functional annotations

```r
plot_votu_function(
  votu_id = "DRR480285__12620"
)
```

This function generates a bubble plot showing KEGG Ortholog annotations associated with a selected vOTU.

---

### 8. Visualize family-level viral functions

```r
plot_family_function(
  family = "Myoviridae",
  top_n = 10
)
```

This function summarizes the most frequent KEGG Ortholog annotations in a selected viral family.

---

### 9. Visualize differential pathways

```r
plot_diff_pathway()
```

This function compares pathways associated with PD-enriched and HC-enriched vOTUs.

---

### 10. Explore bacteria–phage interactions

```r
interactions <- find_phage_host_interactions(
  target = "Streptococcus",
  group = "PD",
  cor_cutoff = 0.5
)

head(interactions)
```

Generate an interactive network:

```r
plot_interaction_network(interactions)
```

Generate a static network:

```r
plot_interaction_network_static(interactions)
```

---

## Function reference

### Abundance profiling

| Function                   | Description                                                                 |
| -------------------------- | --------------------------------------------------------------------------- |
| `get_microbe_abundance()`  | Retrieve sample-level abundance of a bacterial taxon, viral family, or vOTU |
| `plot_microbe_abundance()` | Visualize microbial abundance differences between groups                    |

### Phage database exploration

| Function                    | Description                                                      |
| --------------------------- | ---------------------------------------------------------------- |
| `query_by_host()`           | Query phages associated with a selected host                     |
| `query_by_id()`             | Query phage or vOTU information by identifier                    |
| `query_by_phage_features()` | Query phages by family, lifestyle, host range, or novelty status |
| `phage_family_dashboard()`  | Generate a summary dashboard for a selected phage family         |
| `plot_phage_summary()`      | Visualize family-level composition of queried phages             |

### Viral functional annotation

| Function                 | Description                                                              |
| ------------------------ | ------------------------------------------------------------------------ |
| `get_votu_info()`        | Retrieve taxonomic, host, and functional information for a selected vOTU |
| `get_ko_info()`          | Retrieve information for a selected KEGG Ortholog                        |
| `get_pathway_info()`     | Retrieve pathway-level annotation information                            |
| `plot_votu_function()`   | Visualize KO annotations for a selected vOTU                             |
| `plot_family_function()` | Visualize frequent KO annotations in a viral family                      |
| `plot_diff_pathway()`    | Compare pathway enrichment patterns between PD- and HC-enriched vOTUs    |

### Network analysis

| Function                            | Description                                                |
| ----------------------------------- | ---------------------------------------------------------- |
| `find_phage_host_interactions()`    | Identify bacteria–phage interactions for a selected target |
| `plot_interaction_network()`        | Generate an interactive bacteria–phage network             |
| `plot_interaction_network_static()` | Generate a static bacteria–phage network                   |

---

## Example outputs

PDmicroProfiler can generate several types of visualization outputs:

* abundance comparison plots;
* multi-cohort abundance plots;
* phage family composition pie charts;
* phage family dashboards;
* vOTU-level functional bubble plots;
* family-level KO bar plots;
* differential pathway plots;
* interactive bacteria–phage networks;
* static network plots.

These outputs are designed to support exploratory analysis and publication-ready visualization of PD-associated gut microbiome and virome features.

---

## Repository structure

```text
PDmicroProfiler/
├── R/                         # R functions
├── data/                      # Built-in package datasets
├── data-raw/                  # Scripts or raw data used to prepare package data
├── man/                       # Function documentation
├── DESCRIPTION                # Package metadata
├── NAMESPACE                  # Exported functions
├── LICENSE                    # License information
├── README.md                  # GitHub README
└── PDmicroProfiler.Rproj      # RStudio project file
```

---

## Citation

If you use **PDmicroProfiler** in your research, please cite the R package:

```bibtex
@software{PDmicroProfiler,
  author = {Jiale Liu and WeiHou},
  title = {Integrated Metagenomics Tool PDmicroProfiler: A Novel R Package for Efficient Profiling of Gut Bacterial and Viral Signatures in Parkinson's Disease},
  year = {2026},
  url = {https://github.com/1503259274-create/PDmicroProfiler},
  version = {0.1.0}
}
```

## License

This project is licensed under the MIT License.

