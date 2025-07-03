# Spatial Analysis of Pastoral Grazing Systems (Long Distance Transhumance and Short Distance Transhumance)

This project investigates ecological difference between **long distance transhumance (LDT)** and **short distance transhumance(SDT)** grazing sites across the Andalusian municipalities of Castril, Santiago and Pontones. Using remote sensing, GIS and topographic data, we assess vegetation dynamics on pasturelands.

> We based that analysis on the eco-anthropological Framework developed in Godoy-Sepúlveda et al. (2024), *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*

---

## Repository Structure

- `README.md` — project overview
- `notebooks/`
  - `spatial_analysis_grazing_LDT_SDT.ipynb` — 
- `data/`
  - `pasture_points.geojson` — LDT and SDT point locations
  - `NDVI_2024_04_10m.tif` — NDVI raster (selected month)
  - `NDRE_2024_04_10m.tif` — NDRE raster (Sentinel-2)
  - `NDVI_series/` — monthly NDVI series (April–September)
  - `slope.tif` / `aspect.tif` — slope and aspect rasters (DEM-based)
- `scripts/` — zonal stats functions, analysis tools
- `figures/` — plots, maps, time series visualizations
- `references/` — articles and summaries

---

## Project Goals

1. Extract **vegetation indices** (NDVI, NDRE, NDWI, SAVI, MSAVI, EVI) around geolocated grazing point
2. Compare LDT vs SDT sites in terms of:
  - **Vegetation productivity** (NDVI, EVI, SAVI, MSAVI)
  - **Chlorophyll richness** (NDRE)
  - **Vegetation resilience** (NDVI persistence)
  - **Topographic context** (slope, aspect)
3. Assees the feasability of indirectly approximating the **perenial/annual ratio** via temporal proxies

---

## Key Indicators

| Name | Formula / Method | Ecological Meaning |
|------|------------------|--------------------|
| `NDVI_mean` | Mean value within buffer | Instant green biomass |
| `NDVI_std` | Standard deviation | Spatial heterogeneity |
| `NDRE_mean` | NDRE buffer mean | Chlorophyll maturity |
| `NDRE_vs_NDVI` | NDRE / NDVI ratio | Relative pigment content |
| `NDVI_persistence` | `1 - (std / mean)` or `min / max` | Temporal stability (vegetation persistence) |
| `slope_mean` | Average slope in ° | Grazing accessibility constraint |
| `aspect_mean` | Mean aspect (0–360°) | Solar exposure (N, S, E, W) |

---

## Workflow summary

1. **Import spatial data** (points, pasturelands, NDVI/NDRE rasters, slope/aspect)
2. **Buffer generation** around points (e.g 50m radius)
3. **Zonal statistics** computation using ´rasterstats
4. **Multi-month NDVI processing** to calculate persistene indices
5. **Statistical comparison** of LDT vs SDT sites
6. **Visualization**: boxplots, scattersplots, profile charts, thermatic maps

---

## Expected Outcomes (based on article hypothèses)

- **Higher NDVI persistence** in LDT zones -> indicative of perennial vegetation
- **Elevated NDRE** in LDT areas -> richer, more stable photosynthetic cover
- **Steeper slopes** and **south-facing aspects** more common in SDT sites -> less favorable conditions
- **Temporal NDVI profiles in LDT show more stable seasonal trends

---

## About this project

This project was developped as part of my self-guided Learning in geospatial and ecological analysis. It combines scientific research, open data, and remote sensing workflow I designed to strengthen my skills.

--

## Reference
Godoy-Sepúlveda, F., et al. (2024). *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*
https://doi.org/10.1007/s10745-024-00495-4 

---

## Licence

MIT - free to use and share with proper attribution

