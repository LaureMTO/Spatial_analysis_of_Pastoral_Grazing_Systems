# Spatial Analysis of Pastoral Grazing Systems (Long Distance Transhumance and Short Distance Transhumance)

This project investigates ecological difference between **long distance transhumance (LDT)** and **short distance transhumance(SDT)** grazing sites across the Andalusian municipalities of Castril, Santiago and Pontones. Using remote sensing, GIS and topographic data, we assess vegetation dynamics on pasturelands.

> We based that analysis on the eco-anthropological Framework developed in Godoy-Sepúlveda et al. (2024), *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*

---

## Repository Structure

- `README.md` - project overview
- `notebooks/`
  - `spatial_analysis_grazing_LDT_SDT.ipynb` — 
- `data/`
  - `Buffers/` - 200m, 500m, 1000m radius buffers shapefiles
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

## 🌿 Key Indicators

| Variable             | Description                                      | Ecological Interpretation                                |
|----------------------|--------------------------------------------------|----------------------------------------------------------|
| `NDVI_mean`          | Average NDVI from April to July                  | General vegetation productivity                          |
| `NDVI_std`           | NDVI standard deviation over the season          | Seasonal variation in greenness                         |
| `MSAVI_mean`         | Mean MSAVI during the growing season             | Green biomass proxy, less sensitive to bare soil         |
| `MSAVI_amplitude`    | Difference between max and min MSAVI             | Intensity of seasonal growth dynamics                    |
| `NDRE_mean`          | Average NDRE over growing season                 | Proxy for leaf chlorophyll content (plant health)        |
| `NDRE_peakMonth`     | Month with highest NDRE value                    | Timing of peak chlorophyll richness                      |
| `slope_mean`         | Mean slope within buffer                         | Constraint for grazing movement or accessibility         |
| `aspect_category`    | Dominant aspect class (N, S, E, W)               | Sunlight exposure and microclimate (affects vegetation)  |

---

## Workflow summary

 ### Main Steps

1. **Define grazing areas**  
   - Import polygon buffers around grazing locations  
   - Fixed radius (e.g., 500 m) 

2. **Import Sentinel-2 Harmonized imagery**  
   - Timeframe: April to July (2017, 2018, 2019)  

3. **Calculate monthly vegetation indices**  
   - **NDVI**: photosynthetic activity  
   - **MSAVI**: green biomass (better in sparse vegetation)  
   - **NDRE**: chlorophyll richness  

4. **Zonal statistics per buffer**  
   - Mean for each index  
   - Standard deviation, min, max  
   - Derived indicators:  
     - Seasonal mean  
     - Amplitude (max - min)  
     - Peak month (phenology)  
     - Persistence (`min / max` or `1 - std/mean`)

5. **Export results**  
   - CSV tables (one per year) via `Export.table.toDrive`  

6. **Comparative analysis**  
   - Compare LDT vs SDT mobility regimes  
   - Visualizations: boxplots, thematic maps, heatmaps  
   - Relate to topographic context: slope, aspect 

##  Expected Outcomes

Based on the hypotheses and conclusions of the original study, the analysis aims to verify the following patterns:

- **Greater vegetation stability** in LDT (long-distance transhumance) zones, reflected by:
  - Lower seasonal variability in MSAVI or NDVI
  - More consistent vegetation cover during the grazing season (April–July)

- **Higher photosynthetic activity** and **leaf pigment content** in LDT areas, evidenced by:
  - Higher NDRE values (proxy for chlorophyll richness)
  - Higher seasonal NDVI and MSAVI means

- **More favorable ecological conditions** in well-managed or strictly governed areas (Pontones), associated with:
  - Smoother seasonal profiles (lower NDVI/MSAVI fluctuation)
  - Earlier or more stable seasonal peaks (peak month patterns)

- **Challenging grazing environments** in SDT (short-distance transhumance) zones, potentially linked to:
  - Steeper slopes (mean slope higher)
  - Less favorable solar exposure (e.g., southern aspects with higher evapotranspiration)

- **Temporal vegetation dynamics** as a potential proxy for identifying areas dominated by **perennial vs. annual species**, where:
  - More persistent MSAVI/NDVI signals could indicate perennial vegetation
  - Greater amplitude and variability may reflect dominance of fast-growing annuals


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

