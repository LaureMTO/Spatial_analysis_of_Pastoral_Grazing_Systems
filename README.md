# Spatial Analysis of Pastoral Grazing Systems (Long Distance Transhumance and Short Distance Transhumance)

This project investigates ecological difference between **long distance transhumance (LDT)** and **short distance transhumance(SDT)** grazing sites across the Andalusian municipalities of Castril, Santiago and Pontones. Using remote sensing, GIS and topographic data, we assess vegetation dynamics on pasturelands.

> We based that analysis on the eco-anthropological Framework developed in Godoy-Sepúlveda et al. (2024), *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*

---

## Repository Structure

- `README.md` - project overview
- `notebooks/`
  - `spatial_analysis_grazing_LDT_SDT.ipynb` — 
- `data/`
  - `Buffers/` - 200, 500, 1000 radius buffers shapefiles
  - `Shapefiles/` 
  - `rasters/`
    - `Terrain analysis/` - slopes, aspect, DEM, hillshade, contour, Roughness
    - `Vegetation indices/` - MSAVI, NDVI, NDRE, MSAVI_series (monthly series (April-July)
  - `ZonalStat500/` ZonalStats_2017, ZonalStats_2018, ZonalStats_2019
- `scripts/` — zonal stats functions, analysis tools, index pastureland, visualisation_indices, ZonalStats_buffer500_2017_2018_2019
- `figures/` — plots, maps, time series visualizations
- `references/` — articles and summaries

---

## Project Goals

1. Extract and summarize **vegetation indices** (NDVI, NDRE, MSAVI) for buffered pasture areas.
2. Compare ecological performance of LDT vs SDT zones using:
   - **Seasonal vegetation productivity** (mean NDVI/MSAVI)
   - **Chlorophyll content proxy** (NDRE)
   - **Temporal stability / resilience** (MSAVI amplitude and persistence)
   - **Topographic constraints** (slope and aspect)
3. Evaluate whether multi-temporal vegetation patterns can help infer the **annual vs perennial composition** of plant communities.

---

## Key Indicators

| Variable | Description | Interpretation |
|----------|-------------|----------------|
| `MSAVI_mean` | Average MSAVI over Apr–Jul | Proxy for green biomass |
| `MSAVI_std` | Std dev over season | Temporal variability |
| `NDRE_mean` | Average NDRE | Proxy for chlorophyll content |
| `NDRE / MSAVI` | Exploratory ratio | Relative pigment concentration (needs caution) |
| `MSAVI_persistence` | `1 - (std / mean)` or `min / max` | Stability/resilience proxy |
| `slope_mean` | Mean slope | Terrain accessibility |
| `aspect_mean` | Mean aspect (degrees) | Solar exposure (N/S bias) |

---

## Workflow summary

 A[Délimitation des pâturages<br/>(buffers géographiques autour des sites)] --> B[Import Sentinel-2 SR<br/>+ Masquage nuages]
  B --> C[Calcul des indices NDVI, MSAVI, NDRE<br/> (par mois d'avril à juillet)]
  C --> D[Zonal statistics<br/>(moyenne, écart-type, min, max)]
  D --> E[Calcul d'indicateurs<br/>- Moyenne saisonnière<br/>- Amplitude<br/>- Pic saisonnier<br/>- Persistance]
  E --> F[Export vers CSV<br/>(Google Drive ou Earth Engine)]
  F --> G[Analyse comparative<br/>LDT vs SDT]
  G --> H[Visualisation dans QGIS / Python<br/>Boxplots, Heatmaps, Cartes]
---

## Expected Outcomes (based on article hypothèses)

- **Higher MSAVI persistence** in LDT zones -> indicative of perennial vegetation
- **Elevated NDRE** in LDT areas -> richer, more stable photosynthetic cover
- **Steeper slopes** and **south-facing aspects** more common in SDT sites -> less favorable conditions
- **Temporal NDVI** profiles in LDT show more stable seasonal trends

---

## About this project

This project was developped as part of my self-guided Learning in geospatial and ecological analysis. It combines scientific research, open data, and remote sensing workflow I designed to strengthen my skills.

---

## Reference
Godoy-Sepúlveda, F., et al. (2024). *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*
https://doi.org/10.1007/s10745-024-00495-4 

---

## Licence

MIT - free to use and share with proper attribution

