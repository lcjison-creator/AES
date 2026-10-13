# Early myocardial injury in critically ill children with acute encephalopathy: analysis code

Analysis code for the manuscript "Early Myocardial Injury and Subsequent Deterioration in Critically Ill Children With Acute
Encephalopathy" (Xiaolong Yu, Changjian Li, Yong Zhang, Dan Hu). The notebooks reproduce every number, table, and figure of the
manuscript and its Supplemental Digital Content from the research data platform exports of Wuhan Children's Hospital.

**This repository contains code only. No patient data are included.**

## Contents

| File | Purpose |
|---|---|
| `AES_ITES_classification.ipynb` | Reclassifies acute encephalopathy admissions with the 2024 international consensus definitions of infection-triggered encephalopathy syndromes (ITES) and writes an adjudication worksheet for the investigators |
| `AES_cardiac_involvement_analysis.ipynb` | Cardiac analyses: cohorts, models, sensitivity analyses, tables, and figures (embeds the ITES classification) |
| `AES_publication_pipeline.ipynb` | One click from the exports to the publication tables (Word, Excel), figures (EPS, PDF, TIFF, PNG), figure legends, and an internal cleaned-data workbook |
| `frozen_dataset_build/AE_freeze_build_v1_2.ipynb`, `frozen_dataset_build/load_frozen.py` | Build and loader of the versioned frozen dataset (version 1.2), which supplies the labels for critical discharge against medical advice, organ support, and resuscitation |
| `requirements.txt` | Python packages and the versions used |

## How to run

Put the notebook in one folder together with:

1. the main export from the hospital research data platform (Excel workbook with sheet `病案首页基本信息`);
2. the supplementary export (Excel workbook with sheet `病案首页其他信息`);
3. the frozen dataset folder `AE_freeze_v1.2/` (the analyses read `tables/admission_summary.csv` and `tables/support_events.csv`).

Then choose *Restart Kernel and Run All Cells*. Results are written to `output_ites/`, `output_aes_cardiac/`, or
`output_publication/`. The first run parses the exports and caches them in `cache_aes_exports/`.

Rebuilding the frozen dataset needs the same two exports plus the clinicians' adjudication workbook for discharges against
medical advice, which contains free text from medical records and is not shared.

## Data availability

The data are available from the corresponding author on reasonable request. The exports, the frozen dataset, the adjudication
worksheets, and the cleaned-data workbook contain research identifiers and admission dates; they are excluded from this repository
(see `.gitignore`).

## Software

Python 3.13 with the packages in `requirements.txt`. Analysis code was written with the assistance of a large language model
(Claude; Anthropic) and verified by the authors.
