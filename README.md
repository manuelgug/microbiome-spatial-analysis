# Microbiome-Environment Spatial Analysis Pipeline

[![R](https://img.shields.io/badge/R-%3E%3D4.0.0-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive R pipeline for modeling microbial diversity patterns using real environmental data layers, spatial statistics, and machine learning approaches.

![predictions](https://github.com/manuelgug/microbiome-spatial-analysis/blob/main/imgs/diversity_environmental_driver.png "Predictions")

## 🌟 Overview

This pipeline demonstrates advanced spatial analysis techniques for environmental microbiome research, combining:

- **Real environmental data** from WorldClim and SoilGrids
- **Spatial autocorrelation analysis** using Moran's I and Mantel tests
- **Spatially-aware machine learning** with XGBoost
- **Interactive visualization** and prediction mapping

The workflow is designed for both research applications and as a demonstration of technical capabilities in spatial data science and microbiome analytics.

## 📋 Table of Contents

- [Features](#-features)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [Usage](#-usage)
- [Data Sources](#-data-sources)
- [Methodology](#-methodology)
- [License](#-license)

## ✨ Features

### 🔬 **Microbiome Analytics**
- Phyloseq integration for standard microbiome workflows
- Alpha diversity calculation (Shannon, Simpson indices)
- Environment-driven community simulation
- Realistic sequencing depth modeling

### 🌍 **Environmental Data Integration**
- WorldClim climate layers (BIO1, BIO12)
- SoilGrids soil properties (pH, organic carbon)
- Automatic spatial resolution matching
- Multi-source data harmonization

### 📊 **Spatial Statistics**
- Moran's I test for spatial autocorrelation
- Mantel test for distance-decay relationships
- Spatial cross-validation with blockCV
- Geographic distance matrix calculations

### 🤖 **Machine Learning**
- XGBoost regression with hyperparameter tuning
- Spatially-aware cross-validation
- Overfitting diagnostics and early stopping
- Variable importance analysis

### 🗺️ **Visualization & Mapping**
- Interactive leaflet maps
- Raster prediction mapping
- Model diagnostic plots
- Publication-ready figures

## 🚀 Installation

### Prerequisites

- R (≥ 4.0.0)
- RStudio (recommended)
- Internet connection for downloading environmental data

### Required R Packages

```r
# Install required packages
install.packages(c(
  "phyloseq", "vegan", "tidyverse", "sf", "terra", 
  "geodata", "xgboost", "caret", "leaflet", "leafem",
  "geodist", "rnaturalearth", "rnaturalearthhires",
  "spdep", "blockCV", "geosphere"
))

# Install development version of rnaturalearthhires
devtools::install_github("ropensci/rnaturalearthhires")
```

### Clone Repository

```bash
git clone https://github.com/manuelgug/microbiome-spatial-analysis.git
cd microbiome-spatial-analysis
```

## ⚡ Quick Start

### Run the Complete Pipeline

```r
# Open R/RStudio and run:
rmarkdown::render("spatial_microbiome_analysis.Rmd")
```

## 📖 Usage

### Basic Workflow

1. **Data Preparation**: Generate sample locations and fetch environmental data
2. **Microbiome Simulation**: Create realistic microbiome count data
3. **Spatial Analysis**: Test for spatial autocorrelation
4. **Machine Learning**: Train XGBoost model with spatial CV
5. **Prediction**: Generate landscape-scale diversity maps
6. **Visualization**: Create interactive maps and diagnostic plots

### Customization Options

```r
# Modify key parameters
n_samples <- 50          # Number of sampling locations
study_region <- "Spain"  # Study area
env_driver <- "pH"       # Primary environmental driver
```

### Advanced Usage

```r
# Custom environmental layers
custom_layers <- c("bio_1", "bio_12", "phh2o", "ocd")

# Modified spatial CV parameters
spatial_cv_params <- list(
  k = 5,                 # Number of folds
  size = 50000,          # Block size (meters)
  selection = "random"   # Block selection method
)

# XGBoost hyperparameters
xgb_params <- list(
  eta = 0.05,
  max_depth = 3,
  subsample = 0.5,
  colsample_bytree = 0.5
)
```

## 🗃️ Data Sources

### Environmental Data

| Source | Variables | Resolution | Coverage |
|--------|-----------|------------|----------|
| [WorldClim](https://worldclim.org/) | Temperature, Precipitation | 5 arcmin | Global |
| [SoilGrids](https://soilgrids.org/) | pH, Organic Carbon | 250m | Global |

### Spatial Data

| Source | Type | Usage |
|--------|------|-------|
| [Natural Earth](https://www.naturalearthdata.com/) | Administrative boundaries | Study area definition |
| [rnaturalearth](https://docs.ropensci.org/rnaturalearth/) | Country/state polygons | Spatial masking |

## 🔬 Methodology

### 1. Environmental Data Processing
- Fetch climate and soil data from global databases
- Harmonize spatial resolutions using bilinear resampling
- Extract values for sample locations
- Handle missing data and spatial gaps

### 2. Microbiome Data Simulation
- Generate realistic OTU abundance matrices
- Apply environmental gradients to community composition
- Simulate sequencing depths and sampling variance
- Create phyloseq objects for downstream analysis

### 3. Spatial Autocorrelation Testing
- **Moran's I**: Tests for spatial clustering in diversity values
- **Mantel Test**: Correlates community dissimilarity with geographic distance
- Conditional spatial cross-validation implementation

![blocks](https://github.com/manuelgug/microbiome-spatial-analysis/blob/main/imgs/spatial_blocks.png "Spatial Blocks")

### 4. Machine Learning Pipeline
- XGBoost regression for diversity prediction
- Spatial vs. random cross-validation based on autocorrelation
- Hyperparameter tuning and early stopping
- Model validation and performance assessment

![blocks](https://github.com/manuelgug/microbiome-spatial-analysis/blob/main/imgs/xgboost_rmse_plots.png "Model Performance")

### 5. Spatial Prediction
- Apply trained models to environmental raster layers
- Generate landscape-scale diversity predictions
- Uncertainty quantification and validation


## 📧 Contact

- **Author**: Manuel García Ulloa Gamiz, PhD.
- **LinkedIn**: [manuelgug](https://linkedin.com/in/manuelgug)
- **ORCID**: [0000-0002-6194-9565](https://orcid.org/0000-0002-6194-9565)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Keywords**: microbiome, spatial analysis, environmental modeling, machine learning, XGBoost, phyloseq, R programming, spatial statistics, biodiversity, ecology

⭐ **Star this repository if you find it useful!**
