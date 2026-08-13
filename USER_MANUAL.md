# BiofilmQ-HT User Manual

## 1. Overview

BiofilmQ-HT is a browser-based utility for analysis of 96-well crystal violet biofilm assays using Tecan i-control plate-reader export files.

The utility provides two workflows:

1. **SBF Index — Biofilm Formation**
2. **Antibiofilm Activity — % Inhibition**

No software installation is required. The supplied utility is opened directly in a modern web browser.

> **Release integrity:** This manual documents the supplied BiofilmQ-HT utility. The application file itself has not been modified for GitHub distribution.

---

## 2. Starting BiofilmQ-HT

1. Download `BiofilmQ-HT.html` from the repository.
2. Open the file in a modern web browser.
3. Click **Start Assay**.
4. The application opens at the **Plate map** step.

The interface is organized into three main steps:

1. Plate map
2. Upload data
3. Results

---

## 3. Choose the experiment type

BiofilmQ-HT provides two modes.

### 3.1 SBF Index — Biofilm Formation

Use this mode when biofilm biomass is normalized to bacterial growth.

The analysis uses:

- OD570 for crystal violet-associated biofilm biomass
- OD600 for growth/cell density

Two wavelength files are therefore required.

### 3.2 Antibiofilm Activity — % Inhibition

Use this mode to compare treated or experimental conditions with an untreated Positive control using OD570.

Only the OD570 file is required.

---

## 4. Plate map

The 96-well plate is represented as rows A–H and columns 1–12.

Each well can be assigned one of the following types:

- **Strain/Condition**
- **Blank**
- **Positive ctrl**
- **Negative ctrl**
- **Empty**

### 4.1 Assigning an individual well

Select the required well type and click a well. The dialog allows entry of:

- Well type
- Media / Condition
- Strain / isolate or condition name
- Replicate number

### 4.2 Bulk assignment

Select **Select region**, highlight the required group of wells, and use **Assign selected** to assign them together.

Replicate numbers can be automatically assigned sequentially when using bulk assignment.

### 4.3 Media / Condition matching

For correct blank subtraction, assign the same Media / Condition name to samples and their corresponding Blank wells.

For example:

```text
Sample:       TSB
Blank:        TSB
```

If more than one media/condition is used, each condition can have its own blank group.

Positive controls used for % inhibition are also matched by Media / Condition.

---

## 5. Saving and loading a plate template

Use **Save template** to save the current plate layout as a JSON file.

The saved template contains the plate well information and the selected experiment mode.

Use **Load template** to restore a previously saved layout.

Loading a template replaces the current plate map after confirmation.

---

## 6. Uploading Tecan data

### 6.1 SBF mode

Upload both:

- **OD600** Tecan export file
- **OD570** Tecan export file

### 6.2 Antibiofilm mode

Upload:

- **OD570** Tecan export file

Files can be selected by clicking the upload area or by drag-and-drop.

The utility reads the first worksheet of the uploaded Excel file and extracts the 96-well plate values. It also displays available Tecan metadata, including device, wavelength, date, time and temperature.

If the expected plate-grid anchor cannot be found, the utility reports an upload error.

---

## 7. Calculation settings

The calculation page displays the equations and classification thresholds.

### 7.1 SBF Index

The software calculates:

`SBF = (OD570 sample − OD570 blank) / (OD600 sample − OD600 blank)`

The default thresholds are:

| Category | Threshold |
|---|---:|
| Weak biofilm | SBF ≥ 0.5 |
| Moderate biofilm | SBF ≥ 1.0 |
| Strong biofilm | SBF ≥ 2.0 |

Values below the weak threshold are classified as **Non-biofilm**.

### 7.2 % Inhibition

The software calculates:

`% Inhibition = 100 − [((OD570 sample − blank) / (OD570 Positive control − blank)) × 100]`

The default thresholds are:

| Category | Threshold |
|---|---:|
| Weak inhibition | ≥ 25% |
| Moderate inhibition | ≥ 50% |
| Strong inhibition | ≥ 75% |

Values below 25% are classified as **No/low inhibition**.

### 7.3 Thresholds are editable

The threshold fields can be changed before calculation. The values used for classification and reporting are the values present when **Calculate** is run.

---

## 8. Blank correction and grouping

The utility groups Blank wells according to Media / Condition and calculates the mean blank OD for each condition.

In SBF mode, both OD570 and OD600 blank values are used.

For % inhibition, OD570 blank values are used.

Sample/condition wells are grouped by:

- well type
- strain/condition name
- Media / Condition

Replicate wells belonging to the same group are averaged.

The standard deviation is also calculated when more than one replicate is present and is displayed in the results table.

---

## 9. Results

After calculation, BiofilmQ-HT displays:

### 9.1 Summary

The summary includes:

- number of strains/conditions analysed
- number of media conditions
- total blank wells
- highest SBF or % inhibition
- numbers classified into each category

### 9.2 Chart

A horizontal bar chart displays the active analysis metric for each strain/condition.

Threshold lines are shown on the chart.

### 9.3 Detailed results table

The results table includes relevant information such as:

- strain/condition or control name
- type
- media
- number of replicates
- mean OD600 where applicable
- mean OD570
- blank OD values
- SBF Index where applicable
- % inhibition
- classification

### 9.4 Plate heatmap

The 96-well plate heatmap displays the classification associated with each analysed well/group and distinguishes blanks, positive controls and negative controls.

---

## 10. Exporting results

BiofilmQ-HT provides the following export functions:

### CSV

Exports the detailed results table as CSV.

### PNG

PNG export is available for the chart, detailed results table and plate heatmap.

### PDF

The **Generate PDF report** function creates a publication-oriented report containing methodology, thresholds used, instrument metadata, summary information, results, chart and plate heatmap.

The PDF is generated in landscape A4 format.

---

## 11. Interpretation and quality control

BiofilmQ-HT performs the calculations defined by the supplied utility. Users should ensure that:

- the Tecan files correspond to the intended plate
- OD570 and OD600 files correspond to the same experiment and plate layout
- blank wells are correctly identified
- Media / Condition names are matched correctly
- Positive control wells are correctly assigned for inhibition analysis
- replicate assignments are correct
- thresholds are appropriate for the intended assay and are documented when results are reported

BiofilmQ-HT is an analytical utility and does not independently validate the experimental design or biological appropriateness of the input data.

---

## 12. Troubleshooting

### The Calculate button is disabled

In SBF mode, both OD600 and OD570 files must be successfully loaded.

In Antibiofilm mode, the OD570 file must be successfully loaded.

### A Tecan file cannot be parsed

Check that the file is an Excel export compatible with the expected Tecan i-control format and that the plate grid is present in the first worksheet.

### Blank correction is unexpected

Check that the sample/condition and Blank wells use exactly the intended matching Media / Condition names.

### % inhibition is not calculated

Check that a Positive ctrl has been assigned for the same Media / Condition and that the corresponding OD570 values are present.

### SBF is not calculated for a group

Check that OD600 and OD570 values are available for the relevant wells and that the blank-corrected OD600 denominator is positive and above the utility's internal calculation floor.

---

## 13. Data handling and privacy

The utility processes the selected files in the browser. The application does not contain a server-side database or an account-based data submission workflow.

Users should nevertheless follow their institutional policies when handling experimental data.

---

## 14. External resources used by the current utility

The supplied HTML loads selected libraries and fonts from external web resources, including:

- SheetJS (`xlsx`)
- Chart.js
- html2canvas
- jsPDF
- Google Fonts

The repository does not alter these dependencies.

Because these resources are externally loaded by the supplied HTML, full functionality of the current standalone version may require internet connectivity.

---

## 15. Reproducibility

For reproducible reporting, retain:

1. the BiofilmQ-HT version used
2. the plate template, where applicable
3. the original Tecan export files
4. the threshold values used
5. the exported CSV/PDF report

When BiofilmQ-HT is used in a publication, cite the software release and the associated manuscript when available.
