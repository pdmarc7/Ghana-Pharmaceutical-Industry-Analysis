# Ghana Pharmaceutical Industry Analysis

A multi-dataset, MMDA-level analysis of Ghana's pharmaceutical sector integrating trade microdata, regulatory registrations, licensed pharmacy outlets, and population census data. The analysis underpins a peer-reviewed research paper currently in preparation for submission to global health journals.

---

## Overview

This repository contains the analytical code and supporting data for a national-level study of Ghana's pharmaceutical industry. The study is the first to integrate four administrative datasets at the Metropolitan, Municipal, and District Assembly (MMDA) level to examine pharmaceutical import flows, regulatory product registrations, licensed pharmacy outlet distribution, market structure, and population-weighted access.

**Reference year:** 2022 (trade data); 2024 (pharmacy register); 2026 (FDA registrations); 2021 (population census)

---

## Repository Structure

```
Ghana-Pharmaceutical-Industry-Analysis/
├── Ghana_Pharmaceutical_Industry_Analysis.ipynb   # Main analysis notebook
├── data/                                           # Raw and intermediate data files
├── datasets/                                       # Processed analytical datasets
├── figures/                                        # All output visualisations (PNG, 300 dpi)
├── LICENSE                                         # MIT licence
└── README.md
```

---

## Data Sources

The analysis integrates four administrative datasets:

| Dataset | Source | Coverage |
|---|---|---|
| Trade microdata | Ghana Statistical Service (GSS) | 2022 |
| Product registrations | Food and Drugs Authority (FDA) Ghana | As at 2026 |
| Licensed pharmacy outlets | Pharmacy Council Ghana — List of Pharmacies in Good Standing | 2024 |
| Population and district boundaries | Ghana Population and Housing Census | 2021 |

> **Note:** Raw data files are not included in this repository. Users must obtain datasets directly from the respective authorities. Processed analytical outputs are provided in `datasets/`.

---

## Analysis Components

The notebook is organised around six analytical datasets:

**Dataset 1 — Pharmaceutical Import Analysis**
Analyses Ghana's pharmaceutical imports (HS Chapter 30) from the GSS 2022 trade microdata. Covers source countries, HS4/HS10 product categories, and monthly import trends. Total imports: approximately USD 275.76 million.

**Dataset 2 — FDA Product Registration Analysis**
Examines the FDA Ghana product register, covering registration status, product categories (drug vs. food), country of origin, top registrant companies, active ingredients, and registration year trends.

**Dataset 3 — Pharmacy Outlet Distribution**
Maps the Pharmacy Council 2024 register across all 16 regions and MMDAs. Covers outlet type mix (retail, wholesale/retail, wholesale, hospital pharmacy), geographic concentration, and underserved districts.

**Dataset 4 — Cross-Dataset Integration**
Joins the trade, FDA, and pharmacy datasets to examine the relationship between import reliance, regulatory registration coverage, and licensed outlet density at the regional and MMDA level.

**Dataset 5 — Competitor and Market Structure Analysis**
Identifies pharmacy chains, leading FDA registrant companies, Herfindahl–Hirschman Index (HHI) by region, full-stack market players (import + registration + distribution), and therapeutic area dominance.

**Dataset 6 — Population-Weighted Access**
Computes population per licensed pharmacy outlet at the MMDA level using 2021 census data. Identifies pharmacy deserts, quantifies chain population coverage, and produces HHI–population quadrant analysis.

---

## Key Technical Notes

- **2019 boundary reorganisation:** Ghana's regions expanded from 10 to 16 in 2019. The Pharmacy Council register retains pre-2019 region names. All regional rollups route through an MMDA crosswalk (`mmda_std → GSS district → GSS region`) with manual overrides where required.
- **Ashanti null records:** 78 null Ashanti records in the pharmacy register are a known data quality issue, not crosswalk failures.
- **Terminology:** "Licensed pharmacy outlets" is used throughout (not "community pharmacies") to reflect the full scope of the Pharmacy Council register, which covers retail, wholesale, and manufacturer premises.
- **Visualisation style:** All figures use a consistent palette — `C_POP="#2E75B6"`, `C_PHARM="#5C2D91"`, `C_GOLD="#DAA520"`, `C_WARN="#C8102E"`, `C_GREEN="#1B6B3A"` — with `sns.set_theme(style="whitegrid")` at 300 dpi.

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
python-docx
zipfile (stdlib)
```

The notebook was developed and tested in Google Colab. All scripts are compatible with Python 3.9+.

---

## Usage

1. Obtain the four source datasets from the respective authorities (see Data Sources above).
2. Upload the GSS 2022 trade microdata zip file (`micro_data_trade_2022_CSV.zip`) to the Colab environment when prompted.
3. Place the FDA registrations, Pharmacy Council register, and census population data in the `data/` directory.
4. Run `Ghana_Pharmaceutical_Industry_Analysis.ipynb` sequentially. Each dataset section is self-contained.

---

## Outputs

Each analytical section produces:
- A set of publication-quality PNG figures (300 dpi), saved to `figures/`
- Summary CSV tables, saved to `datasets/`
- A compiled Word report (`ghana_pharma_analysis_report.docx`)

---

## Citation

This repository supports a research paper currently under preparation. A formal citation will be added upon publication. In the interim, please cite the repository directly:

> Marcells, P.D. (2026). *Ghana Pharmaceutical Industry Analysis* [Code repository]. GitHub. https://github.com/pdmarc7/Ghana-Pharmaceutical-Industry-Analysis

---

## Licence

This project is licensed under the MIT Licence. See [LICENSE](LICENSE) for details.

Data sourced from Ghana Statistical Service, FDA Ghana, and Pharmacy Council Ghana remain subject to the terms and conditions of those respective authorities.
