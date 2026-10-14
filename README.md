# Furnace Oxide Thickness Analysis

**Manufacturing data analytics portfolio project** | Python · pandas · matplotlib · statsmodels

## Objective

Investigate whether measured silicon oxide film thickness meets the **560 ± 100 Å** specification and explore variation between furnace runs, zones, and wafer pairs using statistical methods.

## Dataset

Source: [NIST/SEMATECH Engineering Statistics Handbook — Furnace Case Study](https://www.itl.nist.gov/div898/handbook/ppc/section5/ppc51.htm).

- **168 measurements:** 21 runs × 4 zones × 2 sampled wafers per run-zone combination.
- Target: **560 Å**; lower/upper specifications: **460 / 660 Å**.
- The dataset does not include furnace operating parameters or wafer-lot identifiers.

## Methods

1. **EDA:** descriptive statistics, run and zone comparisons, wafer-pair ranges.
2. **SPC:** provisional X-bar and R charts for wafer-pair subgroups (n=2).
3. **ANOVA:** exploratory RUN, ZONE, and RUN × ZONE model.
4. **Capability:** Cp/Cpk from within-pair spread; Pp/Ppk from overall spread.

## Key findings

| Measure | Result |
|---|---:|
| Mean thickness | 563.04 Å |
| Overall standard deviation | 25.38 Å |
| Observed range | 487–634 Å |
| Cp / Cpk | 3.203 / 3.106 |
| Pp / Ppk | 1.313 / 1.273 |

All 168 observed measurements were within specifications. However, multiple X-bar chart signals suggest the process cannot yet be considered demonstrated statistically stable. The large difference between within-pair and overall capability/performance indices suggests important variation beyond wafer pairs. The ANOVA identified RUN and RUN × ZONE associations under its exploratory model, **not proven physical causes**.

**Important:** These indices are exploratory; they do not validate long-term process capability or predict future yield without evidence of stability and appropriate sampling assumptions.

## Repository files

- [`furnace_spc_analysis_annotated.ipynb`](furnace_spc_analysis_annotated.ipynb): executable analysis and interpretations.
- [`furnace_engineering_report.pdf`](furnace_engineering_report.pdf): concise engineering report.
- `data/FURNACE.DAT`: source dataset (download from the NIST case study; include locally if redistribution terms permit).

## Run locally

1. Download the NIST furnace data and save it as `data/FURNACE.DAT` relative to the notebook.
2. Install Python packages: `pip install jupyter pandas matplotlib statsmodels`.
3. Open the notebook in Jupyter and choose **Run All Cells**.

The notebook includes a `%pip install statsmodels` cell; if the package is already installed, that cell may be skipped. The initial cells inspect the working directory and the data file, so keep the relative `data/` folder structure.

## Limitations and next steps

Control limits are provisional (Phase I); wafer-pair subgroup rationality, measurement-system quality and ANOVA assumptions require validation. An actual process investigation would require furnace settings, wafer lots and run history before assigning causes or qualifying capability.

## Attribution

Data: NIST/SEMATECH Engineering Statistics Handbook, [Furnace Case Study](https://www.itl.nist.gov/div898/handbook/ppc/section5/ppc51.htm). Analysis and interpretations are independent educational work.
