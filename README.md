# Project Lambda Tune File Autotuner

## Overview

This project uses a comprehensive analysis and model of ECU (Engine Control Unit) tune files for a JDM Subaru WRX STi EJ207 engine to analyze a data log and perform autotuning to a given PL tune file. 

## Quick Start: Fueling Analysis Script

Use `fueling_analysis.py` to analyze datalogs against a tune file and optionally write updated `fuel_base` values.

From the project root (with `venv` activated and `numpy`/`pandas` installed):

```bash
python fueling_analysis.py ^
  --tune "example_tune_files\Keith Proseus_1999JDMSTI_DW740_VF28_21builtStroker_v8.tune" ^
  --logs "datalogs\tuner_log_25-11-27_1038_V8.csv" ^
  --min-samples 20 ^
  --change-limit 5.0 ^
  --output "reports\fueling_report_v8.md" ^
  --output-tune "tunes\v8_fueling_updated.tune"
```

- **`--tune`**: Source tune used for analysis and as the baseline for `fuel_base` and change limits.  
- **`--logs`**: One or more CSV datalogs to analyze.  
- **`--output`**: Optional Markdown fueling summary.  
- **`--output-tune`**: Optional tune file with updated `fuel_base`.  
- **`--modify-tune`** (optional): Template tune for non-fuel tables; fuel_base always comes from `--tune`.

## Notes

- The system is configured for **MAF-only mode** - Speed Density (SD) tables are ignored
- All Speed Density related tables are documented but marked as not applicable
- The documentation includes open questions where detailed ECU logic is proprietary or unavailable

## Version Information

This analysis is based on the latest schema version **v1.6.33.2** as found in the base tune file.

