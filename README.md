# Forest Landscape Restoration (FLR) priority index for Togo, Cameroon, Benin, Madagascar and Ethiopia

This repository maps **where forest landscape restoration is most needed** in five African countries, on one scale that is comparable between countries, and shows how that need may shift under future climate.

It contains three things:

| What | Where | For whom |
|---|---|---|
| Ready-to-use maps and charts | [`outputs/figures/`](outputs/figures/) | Decision-makers: no software needed |
| Result tables (CSV, open in Excel) | [`outputs/data/`](outputs/data/) | Decision-makers and analysts |
| The notebook that produces everything | [`FLR_global_comparison.ipynb`](FLR_global_comparison.ipynb) | Analysts who want to re-run or adapt the analysis |

If you only need the results, read sections 1 to 5. Sections 6 to 9 are for people who run the notebook.

---

## 1. What the index means

The **FLR restoration priority index** is a number between 0 and 1 for every piece of land. **A higher value means more degraded land and a greater need for restoration.** It combines 20 factors (vegetation, rainfall, temperature, soil, slope, erosion, land cover, fire, cropland, population, tree-cover loss and others), weighted by expert judgement (AHP method).

The index is cut into four **priority classes**. The classes are the index itself, read in levels:

| Class | Index value | Meaning |
|---|---|---|
| Low | below 0.37 | Land in good condition; little restoration need |
| Moderate | 0.37 to 0.47 | Some degradation |
| High | 0.47 to 0.54 | Degraded; restoration recommended |
| Very high | above 0.54 | Most degraded; first priority |

The same limits apply to all five countries, so "Very high" in Togo means the same as "Very high" in Ethiopia. Open water and built-up land are left out: they cannot be restored.

**What the index does not tell you.** It measures *need*, not *feasibility*. It does not include land tenure, cost, community priorities or the likelihood that planting succeeds. See section 5.

---

## 2. Main results

### Restoration need today

Area in each priority class, in million hectares (Mha), restorable land only:

| Country | Restorable area | Low | Moderate | High | Very high | High + Very high |
|---|---|---|---|---|---|---|
| Ethiopia | 108.6 | 11.1 | 16.7 | 21.3 | 59.5 | 74 % |
| Madagascar | 58.1 | 12.1 | 10.1 | 16.4 | 19.6 | 62 % |
| Benin | 11.4 | 0.6 | 4.3 | 4.8 | 1.8 | 57 % |
| Togo | 5.6 | 1.0 | 2.2 | 1.6 | 0.9 | 44 % |
| Cameroon | 46.0 | 32.9 | 7.0 | 3.4 | 2.7 | 13 % |

Source: [`flr_class_area_Mha.csv`](outputs/data/flr_class_area_Mha.csv); 95 % confidence intervals are in [`flr_class_area_Mha_ci.csv`](outputs/data/flr_class_area_Mha_ci.csv).

### Where the need is concentrated

Regions (first administrative level) with the highest mean index in each country:

| Country | Highest-priority regions (mean index) |
|---|---|
| Togo | Savanes (0.55), Kara (0.47), Maritime (0.45) |
| Benin | Alibori (0.52), Atakora (0.50), Borgou (0.47) |
| Cameroon | Extrême-Nord (0.54), Nord (0.46), Adamaoua (0.36) |
| Madagascar | Androy (0.58), Atsimo Andrefana (0.56), Ihorombe (0.55) |
| Ethiopia | Afar (0.61), Somali (0.61), Tigray (0.57) |

Source: [`strata_adm1.csv`](outputs/data/strata_adm1.csv), which ranks every region with at least 30 sample points.

### National pledges compared with the need

| Country | AFR100 pledge (Mha) | High + Very high area (Mha) | Pledge as share of that area |
|---|---|---|---|
| Togo | 1.4 | 2.5 | 57 % |
| Cameroon | 12.0 | 6.1 | 195 % |
| Benin | 0.5 | 6.5 | 8 % |
| Madagascar | 4.0 | 36.0 | 11 % |
| Ethiopia | 15.0 | 80.8 | 19 % |

Source: [`afr100_pledges.csv`](outputs/data/afr100_pledges.csv). The pledge values are those announced by the countries; check them against [afr100.org](https://afr100.org) before quoting them.

### How the need may change with climate

Share of land in the Very high class today and at the end of the century (2081-2100), for the median of five climate models:

| Country | Today | SSP2-4.5 (moderate emissions) | SSP5-8.5 (high emissions) |
|---|---|---|---|
| Togo | 19 % | 26 % | 27 % |
| Benin | 22 % | 29 % | 20 % |
| Cameroon | 9 % | 8 % | 7 % |
| Madagascar | 33 % | 41 % | 46 % |
| Ethiopia | 57 % | 55 % | 50 % |

Madagascar and Togo show the clearest increase. In Ethiopia most climate models project more rain, which lowers the index; more than half of the country still stays in the Very high class. The models disagree strongly with each other, so always look at the per-model figures before drawing conclusions (section 3).

Source: [`cmip6_class_shares_ensemble_maps.csv`](outputs/data/cmip6_class_shares_ensemble_maps.csv). These shares are measured on the map grid (about 1 to 2 km), so the "Today" column differs by a few points from the areas of the first table, which come from the 100 m point sample (for Benin, 22 % here against 16 % there). Use the first table for areas, and this one to compare today with the future.

---

## 3. Guide to the figures

All figures are PNG files in [`outputs/figures/`](outputs/figures/).

### Start here

| Figure | What it shows |
|---|---|
| `flr_index_all_countries.png` | **The main map**: the index in the five countries, one colour scale. The key gives both the four classes and the continuous index. |
| `flr_country_comparison.png` | Share and area of each class per country, and the distribution of the index. |
| `afr100_pledges.png` | Area of each class next to the national AFR100 pledge. |
| `hotspots_gi_star.png` | Statistically significant clusters of high need (hotspots) and low need (cold spots), in five levels. |
| `atlas_<country>.png` | The 20 input variables for one country, to see *why* an area scores high. |

### Future climate

Three horizons are used, the 20-year periods of the IPCC Sixth Assessment Report, each compared with 1995-2014:

| Horizon | Period |
|---|---|
| Near term | 2021-2040 |
| Mid term | 2041-2060 |
| Long term | 2081-2100 |

| Figure | What it shows |
|---|---|
| `cmip6_class_maps_ensemble_ssp245.png`, `..._ssp585.png` | Maps of the classes today and at the three horizons (median of five models). |
| `cmip6_change_by_model_ssp245.png`, `..._ssp585.png` | For each model, country and horizon: change of the share of each class, with the rainfall and temperature change that explain it. |
| `cmip6_priority_classes_by_model_<horizon>.png` | Share of each class today and for each model. |
| `cmip6_area_change_Mha_by_model_<horizon>.png` | Change of the area of each class (Mha) for each model. |
| `hotspots_gi_star_cmip6_ssp245.png`, `..._ssp585.png` | Hotspots today and at the three horizons. |

### Robustness (for technical readers)

`mc_class_shares.png`, `uncertainty_weights.png`, `uncertainty_scores.png`, `sign_sensitivity.png`, `weighting_schemes.png`, `weights_ahp_vs_pca.png`, `shap_vs_ahp.png`, `class_breaks.png`, `factor_correlation.png`, `factor_contributions.png`, `index_distribution.png`, `index_per_country_vs_pooled.png`, `published_griscom.png`, `lodia_validation.png`. Each is explained in the notebook section that draws it.

---

## 4. Guide to the data tables

All tables are CSV files in [`outputs/data/`](outputs/data/). They open in Excel, R or Python. Areas are in million hectares (Mha).

### Which file answers which question

| Question | File |
|---|---|
| How much land is in each priority class in my country? | `flr_class_area_Mha.csv`, `flr_class_area_pct.csv`, `flr_class_area_Mha_ci.csv` |
| How do the five countries compare? | `flr_country_comparison.csv`, `country_framing.csv` |
| Which regions should come first? | `strata_adm1.csv` |
| Does the need differ by biome or inside protected areas? | `strata_biome.csv`, `strata_protection.csv` |
| How does our pledge compare with the need? | `afr100_pledges.csv` |
| How will the classes change with climate, per model? | `cmip6_class_area_Mha_by_model.csv`, `cmip6_class_change_by_model.csv` |
| How will the classes change on the maps? | `cmip6_class_shares_ensemble_maps.csv` |
| Will the hotspots move? | `hotspots_cmip6_by_model.csv` |
| What are the class limits and the weights? | `class_breaks.csv`, `weights_table.csv`, `pooled_normalisation_bounds.csv` |
| How certain are the classes? | `mc_class_shares.csv`, `score_uncertainty_class_shares.csv`, `oat_sensitivity.csv` |
| Which data went in, and how recent is it? | `input_vintage_resolution.csv`, `missing_inputs_pct.csv` |
| How does the index compare with other maps and with field outcomes? | `published_map_comparison.csv`, `validation.csv`, `lodia_validation.csv` |

### The point database

[`samples_analysed.csv`](outputs/data/samples_analysed.csv) is the core database: about 14,700 random points (3,000 per country, sampled at 100 m), one row per point. Use it to make your own maps, statistics or filters.

| Columns | Content |
|---|---|
| `country`, `longitude`, `latitude`, `point_id` | Location |
| `adm1_code`, `biome`, `protected`, `elevation` | Region, biome, protection status (1 = protected), altitude |
| `ndvi`, `precipitation`, `maxTemperature`, `soilMoisture`, `slope`, `erosion`, `soc`, `lulc`, ... | The 20 input factors in their physical units |
| `<factor>_norm` | Need score of each factor, 0 (no need) to 1 (highest need) |
| `ForestLandRestoration` | **The index** (0 to 1) |
| `ForestLandRestoration_Class` | **The class**: 1 Low, 2 Moderate, 3 High, 4 Very high |
| `restorable` | False for water and built-up land |
| `index_original` | Index of the earlier method, kept for comparison only |
| `gain_2000_2012`, `treecover2000`, `ndvi_trend` | Independent observations, used to check the index, not to build it |

`samples_all_countries.csv` is the same sample before filtering (15,000 points, including points without a complete index).

### Climate projection tables

`cmip6_class_area_Mha_by_model.csv` and `cmip6_class_change_by_model.csv` have one row per horizon, scenario, model and country:

| Column | Content |
|---|---|
| `period` | `2021-2040`, `2041-2060` or `2081-2100` |
| `scenario` | `SSP245` (moderate emissions) or `SSP585` (high emissions) |
| `model` | One of five climate models, or `Ensemble median` |
| `<class> today`, `<class> future`, `<class> change` | Area (Mha) or share (%) of each class, and its change |
| `rainfall change (%)`, `max temperature change (deg C)` | Climate change behind the result |
| `moved to a higher class (%)`, `moved to a lower class (%)` | Share of points that change class |

### Files you can ignore

Files named `sample_<country>_*.csv`, `pts_*.csv`, `regen_points_*.csv`, `minmax_*.json` and `country_area_*.json` are download caches. They let the notebook re-run without asking Earth Engine again. They are not meant to be read directly.

---

## 5. To be kept in mind

1. **Need, not feasibility.** A Very high class says the land is degraded. It does not say restoration there is affordable, wanted by communities or likely to succeed.
2. **The index did not predict restoration success in the checks made.** Observed tree-cover gain (2000-2012) occurred mostly on low-priority land, and the index did not separate successful from unsuccessful planting sites in the LoDIA dataset (almost all in Ethiopia). Use the index to locate degradation, and local knowledge to choose sites. Details: `validation.csv`, `lodia_validation.csv`.
3. **Weights are expert judgement.** The uncertainty analyses show how much the classes depend on them (`mc_class_shares.csv`). Class stability is between 83 % and 95 % depending on the country.
4. **Climate projections cover four of the 20 factors**: rainfall, maximum temperature, soil moisture and vegetation greenness (NDVI), about 40 % of the index weight. Soil, terrain, land cover and human pressure are kept as today. The NDVI projection rests on a statistical relation that explains under half of the NDVI variation. The projections show the *direction* of the climate effect on today's landscape, not a forecast of future land use.
5. **Climate models disagree**, above all on rainfall in Ethiopia and Benin. The ensemble median hides this; the per-model figures show it.
6. **Resolution.** Inputs range from 10 m (Sentinel-2) to about 55 km (groundwater). The maps are drawn on a grid of about 1 to 2 km and the statistics come from sample points, so the results suit national and regional planning, not the choice of an individual plot.
7. **Reference period.** "Today" means about 2020, within 2015-2024.

---

## 6. Running the notebook

### Requirements

- Python 3.13 (the versions in `requirements.txt` were tested with it).
- A Google Earth Engine account with a Cloud project. Registration is free for research and non-commercial use: <https://earthengine.google.com>.
- About 8 GB of memory and 2 GB of free disk space.

### Set-up

```bash
python -m venv .venv
.venv\Scripts\activate            # Windows;  on macOS / Linux: source .venv/bin/activate
python -m pip install -r requirements.txt
```

Open `FLR_global_comparison.ipynb` in VS Code or Jupyter and select the `.venv` kernel.

In the second code cell, replace the project with your own:

```python
EE_PROJECT = "your-earth-engine-project"
```

The first run opens a browser window to sign in to Earth Engine.

### Running

Run all cells from top to bottom. The notebook downloads what it needs from Earth Engine and stores it under `outputs/data/` and `outputs/cache/`, so later runs take about 10 minutes.

A first run without the cache is much longer (several hours) and can reach the Earth Engine non-commercial quota. If that happens, requests are retried automatically; re-run the cell that stopped and it continues from where it was. The point samples are already in `outputs/data/`, so only the map grids need downloading.

### Settings you may want to change

All are in the "Configuration" cell at the top:

| Setting | Meaning |
|---|---|
| `COUNTRIES` | Study countries (names as in the LSIB boundary dataset) |
| `N_SAMPLES` | Points per country (3,000) |
| `CMIP6_MODELS`, `CMIP6_SCENARIOS`, `CMIP6_HORIZONS` | Climate models, scenarios and horizons |
| `CMIP6_PROJECT_SOIL_MOISTURE`, `CMIP6_PROJECT_NDVI` | Set to `False` to project rainfall and temperature only |
| `RUN_EXPORTS` | `True` exports the index as GeoTIFF to Google Drive (100 m) for use in GIS software |
| `PUBLISHED_MAPS` | External restoration maps to compare with |

Changing the countries or the sample changes the common scale and the class limits, because both are computed from the pooled sample.

---

## 7. What the notebook does

| Sections | Content |
|---|---|
| 1 - 6 | Study areas, satellite and climate inputs, soil-loss model, common normalisation, weights, the index and its classes |
| 7 - 9 | Interactive maps, area per class, comparison between countries |
| 11 - 21 | Variable atlas, descriptive statistics, collinearity, weight uncertainty, sensitivity, validation, breakdown by biome, protection status and region |
| 22 - 27 | Checks of every design choice, comparison with published maps and AFR100 pledges |
| 28 - 29 | Future climate (three horizons, two scenarios, five models) and spatial hotspots |
| 30 - 33 | Country selection, validation with planting sites, weights learned from observed regrowth, remaining work |

Every section starts with a short text that explains the method and how to read the result.

---

## 8. Input data

| Factor | Dataset | Resolution | Period |
|---|---|---|---|
| NDVI, bare-soil, water and built-up indices | Sentinel-2 surface reflectance | 10-20 m | 2020-2024 median |
| Rainfall | CHIRPS | about 5.5 km | 2015-2024 mean |
| Max temperature, soil moisture | TerraClimate | about 4 km | 2015-2024 mean |
| Groundwater trend | GRACE and GRACE-FO | about 55 km | 2015-2024 trend |
| Slope | SRTM | 30 m | static |
| Soil loss | RUSLE (CHIRPS, OpenLandMap, MERIT, Sentinel-2) | 90-250 m | 2015-2024 |
| Soil organic carbon, soil texture | iSDAsoil | 30 m | about 2021 |
| Land cover | ESA WorldCover | 10 m | 2020 |
| Fire | MODIS MOD14A1 | 1 km | 2020-2024 |
| Cropland | GLAD global cropland | 30 m | 2019 |
| Population density | GPW v4.11 | about 1 km | 2020 |
| Biomass carbon | ESA CCI Biomass | 100 m | 2020 |
| Settlements | GHSL built-up surface | 100 m | 2020 |
| Tree-cover loss | Hansen Global Forest Change | 30 m | 2015-2024 |
| Upstream drainage area | MERIT Hydro | 90 m | static |
| Future climate | NASA GDDP-CMIP6 (GFDL-ESM4, IPSL-CM6A-LR, MPI-ESM1-2-HR, MRI-ESM2-0, UKESM1-0-LL) | 0.25 degree | 1995-2014 and three horizons |

All are read from Google Earth Engine. Two external datasets are used for comparison:

- **Griscom et al. 2017 reforestation opportunity**: a clipped copy is included in `external_data/griscom_2017/`.
- **LoDIA reforestation dataset** (planting sites, used in section 31): 1.2 GB, not included because it exceeds the GitHub file limit. Download it from Harvard Dataverse, [doi:10.7910/DVN/ZJODGO](https://doi.org/10.7910/DVN/ZJODGO), and save it as `external_data/lodia_2025/updated_LoDIA_Reforestation_Dataset.parquet`. Without it, section 31 cannot run; its results are already in `outputs/data/lodia_validation.csv`.

---

## 9. Repository layout

```
FLR_global_comparison.ipynb    the analysis
requirements.txt               Python packages
outputs/figures/               maps and charts (PNG)
outputs/data/                  result tables and the point database (CSV)
outputs/cache/                 downloaded map grids (created on first run, not in the repository)
external_data/                 external maps used for comparison
LICENSE                        MIT licence
```

---

## Licence and citation

Code and results are released under the [MIT licence](LICENSE), copyright 2026 Kueshi Semanou Dahan.

If you use the maps, tables or code, please cite this repository and its author. The input datasets keep their own licences and should be cited as their providers request.
