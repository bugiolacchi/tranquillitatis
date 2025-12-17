README: Depth‑Sensitive Microwave Stratigraphy Workflow
Overview

This archive contains five Python scripts that implement the full analysis pipeline described in Depth‑Sensitive Microwave Stratigraphy of Mare Tranquillitatis. Together they take raw TBDeff rasters through normalization, zonal aggregation, slope fitting, and correlation analysis, producing the tables and figures in the manuscript.

Scripts and Workflow Order
- normalize_tbdeff.py
- Input: Raw TBDeff rasters (3, 7, 19, 37 GHz).
- Process: Robust per‑channel normalization using median/MAD.
- Output: Normalized rasters (*_norm.tif) and extreme masks.
- Purpose: Ensures comparability across channels by removing scale/outlier effects.
- normalised_thermal_excursions.py
- Input: Normalized rasters + ROI shapefiles.
- Process: Zonal statistics (mean TBDeff per channel per ROI).
- Output: Per‑transect CSVs (*_zonal_means.csv).
- Purpose: Aggregates channel means for each mapping unit, used in Table 1 and Fig. 2.
- compute_unit_slopes.py
- Input: Zonal mean CSVs.
- Process: Fits linear model of T_norm vs representative depth for each unit.
- Output: unit_aggregates.csv with slope, intercept, R², and per‑channel means.
- Purpose: Formalises the slope metric, providing the dataset for correlation analyses.
- make_table2.py
- Input: unit_aggregates.csv (slope + auxiliary parameters).
- Process: Pearson correlations of slope vs parameters, bootstrap confidence intervals, p‑values.
- Output: table2_summary.csv (numeric results) + table2_markdown.md (manuscript table).
- Purpose: Produces Table 2 in the paper.
- make_table3.py
- Input: unit_aggregates.csv (per‑channel TBDeff + parameters).
- Process: Pearson correlations of each channel vs parameters, bootstrap confidence intervals, p‑values.
- Output: table3_summary.csv (numeric results) + table3_markdown.md (manuscript table).
- Purpose: Produces Table 3 in the paper.

Requirements
- ArcGIS Pro / ArcPy (Python 3.x) with Spatial Analyst extension (for raster processing).
- Python packages (install via pip):
- numpy
- pandas
- scipy

How to Run
- Place raw TBDeff rasters and ROI shapefiles in the workspace.
- Run normalize_tbdeff.py → generates normalized rasters.
- Run normalised_thermal_excursions.py → generates zonal mean CSVs.
- Run compute_unit_slopes.py → generates unit_aggregates.csv.
- Run make_table2.py → produces Table 2 outputs.
- Run make_table3.py → produces Table 3 outputs.

Reproducibility
- Bootstrap settings (N_BOOT, RANDOM_SEED) are explicit in scripts.
- All inputs/outputs are documented per script.
- Include this README, the five scripts, and the seed values in your code archive.
- Cite Methods Section 3.6 for correlation/bootstrap details.
