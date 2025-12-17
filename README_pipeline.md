Raw TBDeff rasters (3, 7, 19, 37 GHz)
        │
        ▼
normalize_tbdeff.py
    • Robust per-channel normalization (median/MAD)
    • Outputs: *_norm.tif rasters + extreme masks
        │
        ▼
normalised_thermal_excursions.py
    • Zonal means per ROI shapefile
    • Outputs: *_zonal_means.csv (Table 1, Fig. 2)
        │
        ▼
compute_unit_slopes.py
    • Fits linear model of T_norm vs depth
    • Outputs: unit_aggregates.csv (slopes, intercepts, R²)
        │
        ├───────────────┐
        ▼               ▼
make_table2.py      make_table3.py
    • Correlations      • Channel-by-parameter correlations
      slope vs params     (3, 7, 19, 37 GHz)
    • Outputs:           • Outputs:
      table2_summary.csv    table3_summary.csv
      table2_markdown.md    table3_markdown.md
    • Manuscript Table 2   • Manuscript Table 3