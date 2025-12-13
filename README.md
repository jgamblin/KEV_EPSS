# CISA Known Exploited Vulnerabilities Enrichment

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter Notebook](https://img.shields.io/badge/jupyter-notebook-orange.svg)](https://jupyter.org/)

This project provides an automated analysis of the [CISA Known Exploited Vulnerabilities (KEV)](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) catalog, enriched with real-time [Exploit Prediction Scoring System (EPSS)](https://www.first.org/epss/) scores and [Common Vulnerability Scoring System (CVSS) v3](https://www.first.org/cvss/) base scores from the National Vulnerability Database (NVD).

By combining these critical vulnerability metrics, this tool helps security professionals, researchers, and organizations prioritize remediation efforts based on exploitability and impact.

## Table of Contents

- [Features](#features)
- [Data Sources](#data-sources)
- [Installation](#installation)
- [Usage](#usage)
- [Automated Updates](#automated-updates)
- [Visualization](#visualization)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Automated Data Collection**: Downloads and processes the latest KEV catalog, EPSS scores, and NVD CVSS data.
- **Comprehensive Enrichment**: Merges CVE data with EPSS and CVSS scores for holistic vulnerability assessment.
- **Local and Remote Execution**: Includes both GitHub Actions-compatible and local execution notebooks.
- **Data Export**: Generates CSV files for integration with other security tools.
- **Visualization**: Creates scatter plots to visualize relationships between CVSS and EPSS scores.
- **Scheduled Updates**: Automatically updates data via GitHub Actions every 12 hours.

## Data Sources

- **CISA KEV Catalog**: Official list of vulnerabilities known to be exploited in the wild.
- **EPSS Scores**: Probabilistic scores predicting the likelihood of exploitation in the next 30 days.
- **NVD CVSS Scores**: Standardized severity scores for vulnerabilities.

## Installation

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Required Python packages (see `requirements.txt`)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/jgamblin/KEV_EPSS.git
   cd KEV_EPSS
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. (Optional) Install Jupyter if not already installed:
   ```bash
   pip install jupyter
   ```

## Usage

### GitHub Actions Version (KEV-EPSS.ipynb)

This notebook is designed for automated execution in GitHub Actions. It downloads data directly from URLs and processes it.

1. Run the notebook:
   ```bash
   jupyter notebook KEV-EPSS.ipynb
   ```

2. Execute all cells to generate the enriched dataset and visualizations.

### Local Execution Version (KEV-EPSS-Local.ipynb)

For local development or offline analysis, use this notebook which downloads and caches data locally.

1. Run the notebook:
   ```bash
   jupyter notebook KEV-EPSS-Local.ipynb
   ```

2. Execute all cells. Data will be downloaded to the `data/` directory (ignored by Git).

### Output

Both notebooks generate:
- `epss_kev_nvd.csv`: Enriched CSV with CVE, CVSS, EPSS, and KEV details.
- `epss_kev_nvd.png`: Scatter plot visualization.
- Local version also generates `epss_kev_nvd_local.csv` and `epss_kev_nvd_local.png`.

## Automated Updates

This repository uses GitHub Actions to automatically update the dataset and visualizations every 12 hours. The workflow:

1. Downloads latest NVD and EPSS data.
2. Executes the analysis notebook.
3. Commits updated CSV and images back to the repository.

View the workflow file: [`.github/workflows/Update.yml`](.github/workflows/Update.yml)

## Visualization

The scatter plot shows the relationship between CVSS v3 base scores (x-axis) and EPSS scores (y-axis) for all KEV vulnerabilities:

![Current Scatter Plot](epss_kev_nvd.png)

Higher CVSS scores indicate greater severity, while higher EPSS scores suggest higher exploit likelihood.

## Contributing

Contributions are welcome! Please:

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature-name`.
3. Make your changes and test thoroughly.
4. Submit a pull request with a clear description of changes.

### Development Guidelines

- Follow PEP 8 style guidelines.
- Add docstrings to new functions.
- Update README for any new features.
- Test notebooks in both local and GitHub Actions environments.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

- **Author**: John Gamblin
- **GitHub**: [@jgamblin](https://github.com/jgamblin)
- **Issues**: [Report bugs or request features](https://github.com/jgamblin/KEV_EPSS/issues)

---

*Stay secure: Regularly monitor and prioritize your vulnerability remediation efforts with data-driven insights.*
