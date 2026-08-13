# BiofilmQ-HT

**Browser-based high-throughput analysis of crystal violet biofilm assays**

BiofilmQ-HT is a browser-based utility for analysis of 96-well crystal violet biofilm assays using Tecan i-control plate-reader export files.

The utility provides two analysis workflows:

- **SBF Index — Biofilm Formation:** crystal-violet biomass (OD570) normalized to growth (OD600).
- **Antibiofilm Activity — % Inhibition:** comparison of strain/condition OD570 with the corresponding Positive control.

## Key features

- 96-well plate mapping
- Strain/Condition, Blank, Positive control, Negative control and Empty well assignment
- Media/Condition matching for blank subtraction
- Bulk well assignment and region selection
- Save/load plate templates as JSON
- Tecan `.xlsx` file upload by click or drag-and-drop
- SBF Index calculation
- % Biofilm Inhibition calculation
- User-adjustable classification thresholds
- Results summary, chart and 96-well plate heatmap
- CSV export
- PNG export
- Publication-ready PDF report

## Quick start

1. Download or clone this repository.
2. Open `BiofilmQ-HT.html` in a modern web browser.
3. Select the experiment type.
4. Design the 96-well plate map or load a saved JSON template.
5. Upload the required Tecan export file(s).
6. Review the calculation thresholds.
7. Click **Calculate**.
8. Review, export, or report the results.

For complete instructions, see **[USER_MANUAL.md](USER_MANUAL.md)**.

## Input files

### SBF Index mode

Two Tecan i-control Excel files are required:

- OD600 — growth measurement
- OD570 — crystal violet biofilm biomass measurement

### Antibiofilm Activity mode

One Tecan i-control Excel file is required:

- OD570 — crystal violet biofilm biomass measurement

The current parser reads the first worksheet and identifies the 96-well plate grid using the Tecan `< >`-style grid anchor used by the utility. It also reads available instrument metadata such as device, wavelength, date, time and temperature.

## Default classification thresholds

### SBF Index

| Classification | Default threshold |
|---|---:|
| Non-biofilm | < 0.5 |
| Weak | ≥ 0.5 |
| Moderate | ≥ 1.0 |
| Strong | ≥ 2.0 |

### Antibiofilm Activity

| Classification | Default threshold |
|---|---:|
| No/low inhibition | < 25% |
| Weak inhibition | ≥ 25% |
| Moderate inhibition | ≥ 50% |
| Strong inhibition | ≥ 75% |

Thresholds can be changed in the interface before calculation.

## Calculations

### SBF Index

`SBF = (OD570 sample − OD570 blank) / (OD600 sample − OD600 blank)`

The software uses the mean blank value corresponding to the same Media/Condition assigned to the sample.

### % Inhibition

`% Inhibition = 100 − [((OD570 sample − blank) / (OD570 Positive control − blank)) × 100]`

Positive controls are matched by Media/Condition.

## Browser and connectivity

No installation of Python, R, Node.js, or a dedicated desktop application is required.

The current HTML file loads selected JavaScript libraries and web fonts from external web resources. Therefore, the current version may require internet access for full functionality when opened as a standalone local HTML file.

## Repository contents

```text
BiofilmQ-HT/
├── BiofilmQ-HT.html
├── README.md
├── USER_MANUAL.md
├── CITATION.cff
├── CHANGELOG.md
├── docs/
│   └── RELEASE_NOTES.md
└── examples/
    └── README.md
```

## Important release note

The application file in this repository is the supplied BiofilmQ-HT utility. **No changes have been made to its HTML, CSS, JavaScript, calculations, thresholds, interface, or workflow for this repository package.** The additional files are documentation and repository metadata only.

## Citation

If you use BiofilmQ-HT in research, please cite the associated software release and the manuscript describing the utility, when available.

A `CITATION.cff` file is included to support GitHub's citation workflow.

## License

No open-source license has been assigned in this package. The rights holder/institution should specify the appropriate license before public release if redistribution or modification is to be permitted.
