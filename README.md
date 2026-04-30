# NYC Pothole Politics Analysis

This repository contains the code and processed data behind the write-up [Getting filled in on Mayor Mamdani’s “Pothole Politics”](https://observablehq.com/@mpkhinda/nyc-pothole-politics) about the scale of New York City's pothole issue and the Mamdani administration's response as of April 2026. 

### Data 
All data used in this analysis were downloaded via the [NYC Open Data Portal](https://opendata.cityofnewyork.us/) accessed on April 30, 2026:
- [Street Pothole Work Orders - Closed (NYC DOT)](https://data.cityofnewyork.us/Transportation/Street-Pothole-Work-Orders-Closed-Dataset-/x9wy-ing4/about_data)
- [311 Service Requests from 2020 to Present (NYC OTI)](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2020-to-Present/erm2-nwe9/about_data) **filtered for Problem Detail contains "Pothole"**
- [Street Centerlines (NYC OTI)](https://data.cityofnewyork.us/City-Government/Centerline/inkn-q76z/about_data)

To reproduce this analysis you will need to download those datasets as `.geojson` files and save them without the date suffix to `data/raw`. These links are also provided in the `sources.txt` file in that same folder.

### Repository Structure
```
├── data/
│   ├── raw/                # Source datasets (not tracked in this repo — see sources.txt)
│   │   └── sources.txt     # Dataset download links
│   └── processed/          # Aggregated outputs from analysis notebooks
├── notebooks/              # Python analysis notebooks
└── environment.yml         # Conda environment specification
```

### Analysis
The `/notebooks` folder contains three notebook files, written in Python, that each analyze the data and output aggregated `.csv` or `.geojson` files which can be used for visualization. Prior to running the analysis, you will need to create a conda environment which requires installing [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or [Anaconda](https://www.anaconda.com/download) then, after cloning the repo, running:

```bash
conda env create -f environment.yml
conda activate nyc-pothole-politics-analysis
```

### Visualization
The interactive charts and write-up are published on Observable. The `/data/processed` folder contains the aggregated outputs from the analysis notebooks that are loaded directly into the Observable notebook.

### Notes
- Pothole work order data is updated monthly by NYC DOT. This analysis reflects data accessed on April 30, 2026 and does not capture work orders closed after that date.
- 311 service request data was filtered for pothole complaints only and deduplicated by removing complaints at matching cross streets in the same borough within 7 days.
- Work order counts differ from NYC DOT's publicly reported pothole fill counts, which are based on internal tracking not available in the public dataset.

### License
Data is sourced from NYC Open Data and subject to the [NYC Open Data Terms of Use](https://opendata.cityofnewyork.us/overview/#termsofuse). Analysis and visualization code is available under the [MIT License](https://opensource.org/license/MIT).

### Contact
If you have questions or comments about this analysis feel free to get in touch: [mattkhindahas@gmail.com](mailto:mattkhindahas@gmail.com)