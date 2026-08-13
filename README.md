# BiofilmQ-HT

**A browser-based utility for high-throughput crystal violet biofilm assay analysis**

BiofilmQ-HT is a browser-based analytical utility designed for analysis of 96-well crystal violet biofilm assays using Tecan i-control plate-reader data.

The utility provides two analytical workflows:

- **SBF Index — Biofilm Formation:** quantification of biofilm formation using crystal violet absorbance (OD570) normalized to bacterial growth (OD600).
- **Antibiofilm Activity:** estimation of percentage biofilm inhibition relative to the untreated positive control.

No software installation or programming knowledge is required.

## Quick Start

1. Download `BiofilmQ-HT.html`, or launch the application through GitHub Pages when available.
2. Open the HTML file in a modern web browser.
3. Select the required assay mode.
4. Create or load a 96-well plate template.
5. Upload the required Tecan i-control Excel file(s).
6. Review the calculated results.
7. Export results as required.

For detailed instructions, see the [User Manual](USER_MANUAL.md).

## Example Use Cases

Three complete experimental examples are provided to demonstrate the application using real experimental datasets.

### Use Case 1 — Media Optimization

Demonstrates the SBF Index workflow for evaluating the effect of different culture media conditions on biofilm formation.

The example includes:

- OD570 data
- OD600 data
- 96-well plate template
- BiofilmQ-HT output
- Generated PDF report

### Use Case 2 — Antibiofilm Activity

Demonstrates the Antibiofilm Activity workflow for evaluating biofilm inhibition by different treatments and treatment combinations.

The example includes:

- OD570 data
- 96-well plate template
- BiofilmQ-HT output
- Generated PDF report

### Use Case 3 — Screening for Biofilm-Forming Capabilities of Isolates

Demonstrates the SBF Index workflow for screening multiple isolates for their ability to form biofilms.

The example includes:

- OD570 data
- OD600 data
- 96-well plate template
- BiofilmQ-HT output
- Generated PDF report

The example datasets are provided to demonstrate the complete workflow from raw plate-reader data and plate layout through analysis and reporting.

## Features

- 96-well plate mapping
- Strain/condition and media assignment
- Blank and control assignment
- Media-matched blank subtraction
- SBF Index calculation
- Antibiofilm activity calculation
- Configurable classification thresholds
- Results table
- Plate heatmap
- CSV export
- PNG export
- PDF report generation
- Plate-template saving and loading

## Requirements

- Modern web browser
- Tecan i-control exported Excel files in the supported format
- Internet connection may be required for externally hosted application resources

No installation of Python, R, Node.js, or other software is required.

## Documentation

- [User Manual](USER_MANUAL.md)
- [Release Notes](docs/RELEASE_NOTES.md)
- [Example Data Inventory](docs/EXAMPLE_DATA_INVENTORY.md)

## Citation

If you use BiofilmQ-HT in your research, please cite the software using the citation information provided in `CITATION.cff`.

## Software Integrity

The distributed `BiofilmQ-HT.html` file is preserved as the released utility. The SHA-256 checksum of the released HTML file is provided in `UTILITY_SHA256.txt`.

## License

See the repository for licensing information.
