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

1. Extract **vegetation indices** (NDVI, NDRE, NDWI, SAVI, MSAVI, EVI) around geolocated grazing point
2. Compare LDT vs SDT sites in terms of:
  - **Vegetation productivity** (NDVI, MSAVI, NDRE)
  - **Chlorophyll richness** (NDRE)
  - **Vegetation resilience** (MSAVI persistence)
  - **Topographic context** (slope, aspect)
3. Assees the feasability of indirectly approximating the **perenial/annual ratio** via temporal proxies

---

## Key Indicators

| Name | Formula / Method | Ecological Meaning |
|------|------------------|--------------------|
| `MSAVI_mean` | Mean value within buffer | Instant green biomass |
| `MSAVI_std` | Standard deviation | Spatial heterogeneity |
| `MSAVI_mean` | NDRE buffer mean | Chlorophyll maturity |
| `NDRE_vs_MSAVI` | NDRE / MSAVI ratio | Relative pigment content |
| `MSAVI_persistence` | `1 - (std / mean)` or `min / max` | Temporal stability (vegetation persistence) |
| `slope_mean` | Average slope in ° | Grazing accessibility constraint |
| `aspect_mean` | Mean aspect (0–360°) | Solar exposure (N, S, E, W) |

---

## Workflow summary

1. **Import spatial data** (points, pasturelands, NDVI/NDRE rasters, slope/aspect)
2. **Buffer generation** around points (e.g 200 meters, 500 meters and 1000 meters radius)
3. **Zonal statistics** computation using ´rasterstats
4. **Multi-month MSAVI processing** to calculate persistene indices
5. **Statistical comparison** of LDT vs SDT sites
6. **Visualization**: boxplots, scattersplots, profile charts, thermatic maps

---

## Expected Outcomes (based on article hypothèses)

- **Higher NDVI persistence** in LDT zones -> indicative of perennial vegetation
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

