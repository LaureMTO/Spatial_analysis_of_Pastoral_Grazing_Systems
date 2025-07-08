# Spatial Analysis of Pastoral Grazing Systems (Long Distance Transhumance and Short Distance Transhumance)

This project investigates ecological difference between **long distance transhumance (LDT)** and **short distance transhumance(SDT)** grazing sites across the Andalusian municipalities of Castril, Santiago and Pontones. Using remote sensing, GIS and topographic data, we assess vegetation dynamics on pasturelands.

> We based that analysis on the eco-anthropological Framework developed in Godoy-Sepúlveda et al. (2024), *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*

---

## Repository Structure

- `README.md` - project overview
- `notebooks/`
  - `spatial_analysis_grazing_LDT_SDT.ipynb` — 
- `data/` - ZonalStat_indices_terrain_2017_2022.geojson, zonalstat_slope_aspect_roughness.geojson, ZonalStats_2017_2022_csv.csv
- `scripts/` — zonal stats functions, analysis tools, index pastureland, visualisation_indices, ZonalStats_buffer500_2017_2022
- `figures/` — plots, maps, time series visualizations
- `references/` — articles and summaries

---

## Project Goals

1. Extract and summarize **vegetation indices** (NDVI, SAVI, NDRE, MSAVI) for buffered pasture areas.
2. Compare ecological performance of LDT vs SDT zones using:
   - **Seasonal vegetation productivity** (mean NDVI/MSAVI/SAVI)
   - **Chlorophyll content proxy** (NDRE)
   - **Temporal stability** (SAVI amplitude)
   - **Topographic constraints** (slope and aspect)
3. Evaluate whether multi-temporal vegetation patterns can help infer the **annual vs perennial composition** of plant communities.

---

## Key Indicators

## 🌿 Key Indicators

| Variable             | Description                                      | Ecological Interpretation                                |
|----------------------|--------------------------------------------------|----------------------------------------------------------|
| `NDVI_mean`          | Average NDVI from April to July                  | General vegetation productivity                          |
| `NDVI_std`           | NDVI standard deviation over the season          | Seasonal variation in greenness                        b |
| `SAVI_mean`          | Mean SAVI during the growing season             | Green biomass proxy, less sensitive to bare soil         |
| `SAVI_amplitude`     | Difference between max and min SAVI              | Intensity of seasonal growth dynamics                    |
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

### 2. Remote Sensing Data Processing (Google Earth Engine)

- **Satellite source:** Sentinel-2 Level 2A (`COPERNICUS/S2_HARMONIZED`)
- **Time frame:** April to July, from **2017 to 2022** (transhumance period)
- Applied a **cloud mask** based on QA60 bit flags
- Computed the following vegetation indices:
  - **NDVI** – Normalized Difference Vegetation Index
  - **SAVI** – Soil-Adjusted Vegetation Index
  - **MSAVI** – Modified SAVI for minimal soil interference
  - **NDRE** – Normalized Difference Red Edge Index
- For each year, calculated **mean**, **standard deviation**, and **amplitude** of each index using monthly composites (April–July)
- Exported **zonal statistics** per buffer zone as a CSV file

### 3. Time Series Analysis and Charting

- Time series of vegetation indices analyzed by grazing type (LDT vs SDT)
- Comparative line charts generated for:
  - **NDVI_mean**
  - **SAVI_mean**
  - **MSAVI_mean**
  - **NDRE_mean**
- Charts created using Earth Engine and Google Sheets
- Exported an animated **SAVI time series map** (2017–2022, April–July) as both **GIF** and **MP4**

## 4. Topographic and Physical Variables (QGIS)

- Used a high-resolution Digital Elevation Model (DEM) to extract topographic features per buffer zone:
  - `slope_mean` – Mean slope (°) per buffer
  - `aspect_mean` – Mean aspect (°) or converted to cardinal categories (e.g., N, S, E, W)
  - `roughness` – Surface ruggedness index (optional but included)
- All layers were clipped to buffer extent, and **zonal statistics** were computed using the **Raster > Zonal Statistics** tool in QGIS.
- Resulting values were merged with vegetation indices into a unified table for multi-variable analysis.

---

## 5. Descriptive Analysis by Grazing Type

- Aggregated the final dataset by **grazing mobility type** (`type_pasto`: LDT, SDT, Mixed) and **year**.
- Computed **mean** and **standard deviation** for key ecological indicators:
  - Vegetation indices:
    - `SAVI_mean`, `SAVI_std`
    - `NDRE_mean`
    - `MSAVI_mean`, `MSAVI_std`
    - `NDVI_mean`, `NDVI_std`
    - Amplitude indicators (e.g., `SAVI_amplitude`, `MSAVI_amplitude`)
  - Topographic variables:
    - `slope_mean`
    - `roughness`
    - `aspect_category` (categorical summary)
- The goal was to explore whether ecological conditions and seasonal dynamics differ significantly across mobility strategies.

---

## About this project

This project was developed as part of my self-guided Learning in geospatial and ecological analysis. It combines scientific research, open data, and a remote sensing workflow I designed to strengthen my skills.

---

## Reference
Godoy-Sepúlveda, F., et al. (2024). *Governance, Mobility, and Pastureland Ecology. An EcoAnthropological Study of Three Pastoral Commons in Northeastern Andalusia*
https://doi.org/10.1007/s10745-024-00495-4 

---

## Licence

MIT - free to use and share with proper attribution

