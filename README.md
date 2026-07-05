<div align="center">

<img src="assets/ga-logo-color.png" width="180" alt="Grassland Analytica Corp."/>

# CP2025 — Canadian Prairie 2025 Grassland Mapping Project

*Prepared by **Grassland Analytica Corp.** for the **Canadian Forage and Grassland Association (CFGA)***

[![Live Report](https://img.shields.io/badge/Live%20Report-View%20Online-C62828?style=for-the-badge)](https://grasslandanalytica.github.io/cfga-cp2025/)
[![Download Data](https://img.shields.io/badge/CP2025.tif-Download%20630%20MB-1F3864?style=for-the-badge)](https://github.com/GrasslandAnalytica/cfga-cp2025/releases/download/v2025-data/CP2025.tif)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-548235?style=for-the-badge)](https://grasslandanalytica.github.io/cfga-cp2025/)

</div>

---

## Overview

This repository hosts the interactive assessment report and web deliverable for the **2025 Grassland Classification** of the Canadian Prairie Ecozone, covering Alberta, Saskatchewan, and Manitoba. The project maps three ecologically distinct grassland subtypes — **Native**, **Tame**, and **Mixed Grassland** — at 10 m spatial resolution using multi-temporal Sentinel-2 imagery and a two-stage Random Forest classification workflow implemented in Google Earth Engine.

The 2025 assessment is compared against a 2023 baseline to quantify grassland dynamics, class transitions, and landscape stability across the Prairie region.

---

## Live Report

**[https://grasslandanalytica.github.io/cfga-cp2025/](https://grasslandanalytica.github.io/cfga-cp2025/)**

The interactive report includes:

- 📍 **Zoomable satellite map** — 2025 grassland classification overlay on ESRI World Imagery with place-name labels
- 📊 **Sankey diagram** — grassland class transition flows from 2023 → 2025
- 📈 **Charts** — area comparison (2023 vs 2025), class distribution, classification accuracy radar
- 📋 **Full methodology**, accuracy assessment, ecological interpretation, and management implications
- ⬇ **Direct download buttons** for `CP2025.tif` and `CP2025_metadata.json`

> **Note:** The interactive map requires an internet connection for the satellite basemap (ESRI World Imagery).

---

## Data Products

All raster deliverables are available in the [**Releases**](https://github.com/GrasslandAnalytica/cfga-cp2025/releases/tag/v2025-data) section of this repository.

| File | Size | Description |
|---|---|---|
| [`CP2025.tif`](https://github.com/GrasslandAnalytica/cfga-cp2025/releases/download/v2025-data/CP2025.tif) | 630 MB | 2025 Grassland Classification Mosaic — EPSG:3347 · 10 m · LZW |
| [`CP2025_metadata.json`](https://github.com/GrasslandAnalytica/cfga-cp2025/releases/download/v2025-data/CP2025_metadata.json) | 18 KB | ISO 19115-adapted dataset metadata |

### Pixel Value Encoding

| Value | Class | Colour |
|---|---|---|
| `0` | No Data / Non-Grassland | Transparent |
| `2` | Tame Grassland | `#4CAF50` Green |
| `3` | Native Grassland | `#EF5350` Red |
| `5` | Mixed Grassland | `#FFD600` Yellow |

> 1 pixel = 10 m × 10 m = **0.01 ha**

---

## Key Results (2025)

| Grassland Class | Area (ha) | Share | Change vs 2023 |
|---|---|---|---|
| Native Grassland | 8,262,857 | 56.9% | −0.9% |
| Tame Grassland | 3,848,467 | 26.5% | −5.8% |
| Mixed Grassland | 2,405,314 | 16.6% | +24.9% |
| **Total Classified** | **14,516,638** | 100% | +1.2% |

**69.3%** of co-classified pixels retained the same grassland class between 2023 and 2025, indicating broad landscape stability.

---

## Classification Accuracy

| Stage | Year | Overall Accuracy | Kappa |
|---|---|---|---|
| Stage 1 — Broad Land Cover | 2023 | 99.18% | 0.986 |
| Stage 1 — Broad Land Cover | 2025 | 99.20% | 0.987 |
| Stage 2 — Grassland Types | 2023 | 71.92% | 0.561 |
| Stage 2 — Grassland Types | 2025 | 70.71% | 0.540 |

---

## Methodology Overview

```
Sentinel-2 L2A  →  Cloud Masking  →  Seasonal Composites (May–Jun / Jul–Aug / Sep–Oct)
       ↓
Feature Engineering (54 candidate features: spectral, phenological, texture, terrain)
       ↓
Stage 1: Random Forest → 5 Land Cover Classes → Grassland Mask
       ↓
Feature Selection (top 20 by importance)
       ↓
Stage 2: Random Forest → 3 Grassland Subtypes (Tame / Native / Mixed)
       ↓
Post-classification Change Detection (2023 vs 2025) → Transition Matrix
```

---

## Technology Stack

| Component | Technology |
|---|---|
| Satellite imagery | Sentinel-2 Level-2A (Copernicus Programme) |
| Cloud processing | Google Earth Engine |
| Classifier | Random Forest (150 decision trees) |
| Interactive map | Leaflet.js + ESRI World Imagery |
| Sankey diagram | D3.js + d3-sankey |
| Charts | Chart.js 4 |
| Map tiles | gdal2tiles (EPSG:3857, zoom 5–12, TMS) |
| Hosting | GitHub Pages |

---

## Study Area

The Canadian Prairie Ecozone, extending approximately **116°W – 96°W** longitude and **49°N – 54°N** latitude, encompassing the agricultural and grassland regions of **Alberta**, **Saskatchewan**, and **Manitoba**.

| Parameter | Value |
|---|---|
| Coordinate Reference System | EPSG:3347 — NAD83 / Statistics Canada Lambert |
| Spatial Resolution | 10 m × 10 m |
| Mosaic Dimensions | 123,691 × 80,225 pixels (~9.9 billion total) |
| Output Format | GeoTIFF · LZW compressed · Tiled (256×256) |

---

## Reference

Full grassland class definitions and ecological descriptions are provided in:

> Mousavi, M.; Biney, J.K.M.; Kishchuk, B.; Youssef, A.; Cordeiro, M.R.C.; Friesen, G.; Cattani, D.; Namous, M.; Badreldin, N. A Hierarchical Machine Learning-Based Strategy for Mapping Grassland in Manitoba's Diverse Ecoregions. *Remote Sens.* 2024, 16, 4730. https://doi.org/10.3390/rs16244730

---

## Contact

**Grassland Analytica Corp.**
[service@grasslandanalytica.com](mailto:service@grasslandanalytica.com)
[www.grasslandanalytica.com](https://www.grasslandanalytica.com)

---

<div align="center">

*Prepared for the [Canadian Forage and Grassland Association (CFGA)](https://www.canadianfga.ca/en/) · June 2026*

**Measuring Change. Guiding Conservation.**

</div>
