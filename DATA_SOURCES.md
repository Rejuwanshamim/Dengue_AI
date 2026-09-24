# Data sources

This project uses **two public datasets** (four CSV files in total). Neither is modified at source; download them yourself and place them in the folders shown below.

## 1. OpenDengue (version 1.3)

Global database of publicly reported dengue case counts.

- Download page: https://opendengue.org/data.html
- GitHub (all versions): https://github.com/OpenDengue/master-repo
- Data paper: https://doi.org/10.1038/s41597-024-03120-7
- Dataset (Figshare): https://doi.org/10.6084/m9.figshare.24259573
- Licence: CC BY-SA (share adaptations under the same terms)

**Files to download** (no login needed): on the download page, use the buttons in the "Download global data" section.

| File | Button on the website | Used for |
|---|---|---|
| `national.csv` | Download global national data | Sections 3–5 (main analysis) |
| `Spatial_extract_V1_3.csv` | Download global highest spatial resolution data | Section 5.6 (sub-national transfer test) |

Do **not** download "highest temporal resolution data"; it is not used.

**Check your download** (national extract): about 29,873 rows, 129 countries and territories, years 1924–2025. If the numbers differ, a newer version may have been released; use version 1.3 to reproduce the paper.

## 2. DengAI (DrivenData competition)

Weekly dengue cases for San Juan (Puerto Rico) and Iquitos (Peru). Used only for the external validation in Section 5.9.

- Competition page: https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/
- Free DrivenData account required. Join the competition, open the **Data** tab and download:

| File on the website | Save as |
|---|---|
| Training Data Features | `dengue_features_train.csv` |
| Training Data Labels | `dengue_labels_train.csv` |

Test Data Features and Submission Format are not used. Please read DrivenData's terms of data use before reusing the data, and cite the competition.

## Folder layout

```
project/
├── dengue_revised.ipynb
├── national.csv
├── Spatial_extract_V1_3.csv
└── data/dengai/
    ├── dengue_features_train.csv
    └── dengue_labels_train.csv
```

The notebook reads these paths from environment variables, which you can change:

| Variable | Default | Meaning |
|---|---|---|
| `DENGUE_CSV` | `national.csv` | OpenDengue national extract |
| `OUT_DIR` | `results` | Output folder |
| `DENGAI_DIR` | `data/dengai` | Folder holding the two DengAI files |

The spatial extract file name is set by `SPATIAL_RAW_CSV` in the notebook (it is only needed the first time, to build the cached file).

## How to cite

- Clarke J, Lim A, Gupte P, Pigott DM, van Panhuis WG, Brady OJ. A global dataset of publicly available dengue case count data. *Scientific Data* 11, 296 (2024). https://doi.org/10.1038/s41597-024-03120-7
- DrivenData. DengAI: Predicting Disease Spread. https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/
