# RMOBI Analysis

<<<<<<< HEAD
This repository contains scripts for statistical analyses, figure generation, and reproduction of manuscript results.
=======
This repository contains scripts used for statistical analyses and figure generation of the RMOBI manuscript.
>>>>>>> c8c1887c07c44adf638aee5a75ebdea4e24f78a6

The related [RMOBI interactive visualization resource](https://slizovskiylab.github.io/RMOBI/) provides network exploration. This repository contains the downstream analysis workflows and input exports, rather than the web application or its companion C++ engine.

## Project structure

```text
RMOBI-Analysis/
├── analysis_scripts/
│   ├── 1_upset.py … 7_heatmaps_graph2.py  # Manuscript figure workflows
│   ├── run_all_analysis.py              # Runs the seven figure scripts
│   └──images/                          # Generated figures
├── statistical_testing/
│   ├── *.py                            # Model inputs and cross-study analyses
│   ├── *.R                             # Mixed models, contrasts, and plots
│   ├── run_all_statistical_testing.sh   # Runs the statistical workflow
│   ├── output/                         # Prepared CSVs, results, models, figures
│   └── README.md                       # Detailed methods and run instructions
├── data/
│   ├── patientwise_colocalization_by_timepoint.csv
│   ├── meta_data.csv                   # Sample, patient, cohort, and study metadata
│   ├── MedImpAMR_taxa.csv               # Clinically relevant ARG list
│   ├── MGE_total_classification.csv     # MGE classification lookup
│   ├── json/                           # Network and temporal-dynamics exports
│   └── output/                         # Derived tables, including temporal dynamics
└── README.md
```


## Software environment

| Component | Version | Purpose |
| --- | --- | --- |
| Python | 3.8.0 | Figure generation, input preparation, cross-study analyses |
| pandas | 2.0.3 | Tabular data processing |
| NumPy | 1.24.3 | Numerical operations |
| Matplotlib | 3.7.4 | Figures |
| seaborn | 0.13.2 | Heatmaps |
| SciPy | 1.10.1 | Statistical calculations and meta-analysis |
| R | 4.5.0 | Mixed models and model-based figures |
| glmmTMB | 1.1.14 | Beta-binomial mixed models |
| emmeans | 2.0.4 | Estimated marginal means and cohort contrasts |
| DHARMa | 0.5.0 | Simulation-based model diagnostics |
| Bash | Available on `PATH` | Statistical workflow runner |

Both `python3` and `Rscript` must be available on `PATH`. For the recorded Python environment, create a virtual environment with a Python 3.8 interpreter:

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install numpy==1.24.3 pandas==2.0.3 matplotlib==3.7.4 seaborn==0.13.2 scipy==1.10.1
```

Install the R packages from an R console:

```r
install.packages(c("glmmTMB", "emmeans", "DHARMa"))
```


## Run the analyses

Run these commands from the repository root after installing dependencies and ensuring the input files are present.

Generate the manuscript figures:

```bash
python3 analysis_scripts/run_all_analysis.py
```


Run the statistical analyses:

```bash
bash statistical_testing/run_all_statistical_testing.sh
```

## License

The project is licensed under the GNU General Public License v3.0 (GPLv3). 
