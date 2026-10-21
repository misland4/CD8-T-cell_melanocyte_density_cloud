# CD8+ T-cell and melanocyte density cloud

Python scripts for visualizing CD8+ T-cell and melanocyte counts per scan view as a two-dimensional kernel density cloud. The supplied research example contains **7 paired counts in one group**.

![Density cloud generated from the supplied research observations](docs/images/density_cloud_demo.png)

## 1. System requirements

### Software dependencies and operating systems

Use **Python 3.13**. The exact tested dependencies are pinned in `requirements.txt`:

| Package | Tested version |
| --- | --- |
| NumPy | 2.3.5 |
| SciPy | 1.16.3 |
| Matplotlib | 3.10.6 |
| openpyxl | 3.1.5 |

The verified environment is **Windows 11 Pro, Python 3.13.9**. Other operating systems and Python versions have not been tested for this release. The macOS/Linux command variants below are provided for convenience.

### Hardware

A standard desktop CPU is sufficient for these small inputs. No GPU, CUDA, or other non-standard hardware is required. The demo was timed on an Intel Core i5-14600KF desktop with approximately 32 GB RAM; this is the test machine, not a minimum hardware requirement.

## 2. Installation guide

### Windows PowerShell or CMD

```powershell
git clone https://github.com/misland4/CD8-T-cell_melanocyte_density_cloud.git
cd CD8-T-cell_melanocyte_density_cloud
python -m venv .venv
.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Alternatively, download and extract the repository ZIP, enter its directory, and run the last two commands. No package activation is required.

### macOS/Linux command variant

```sh
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
```

Use `.venv/bin/python` in place of `.venv\Scripts\python.exe` in the following commands.

**Installation time:** allow approximately 2–5 minutes with a working internet connection. This is a planning estimate; a clean installation was not timed, and package download speed can change it substantially.

## 3. Demo

### Research example

From the repository root, run:

```powershell
.venv\Scripts\python.exe density_cloud.py --input examples/research_density.xlsx --output-dir output
```

Expected files and console output on Windows:

```text
output\density_cloud.pdf
output\density_cloud.png
output\density_cloud.svg
```

The PNG is saved at 300 dpi. PDF and SVG retain vector contours and points. The preview above is generated from this workbook and plots exactly seven observations in a single dark green cloud. Output files with the same names are overwritten on subsequent runs.

**Measured runtime:** about **1.4 seconds** for the research example and all three output formats in one run on the test desktop, with dependencies already installed. This is a single-run observation, not a benchmark across machines.

### Data provenance

[Download the included research workbook](examples/research_density.xlsx). It is a byte-for-byte copy of the supplied `Simulated dataset to demo the code.xlsx`, with a simpler repository filename. The dataset provider confirmed that these are **real research observations**. The original worksheet name, `Simulated dataset`, is retained; the wording in that source name does not reflect the provider's confirmation.

The source workbook is not rewritten. The script reads `B2:C8` from that worksheet and preserves all seven numeric pairs and their order. No second group is inferred or generated.

## 4. Instructions for use

### Use your own workbook

```powershell
.venv\Scripts\python.exe density_cloud.py --input "C:/data/counts.xlsx" --sheet "Sheet1" --output-dir "C:/data/figures"
```

`--input` is required. `--sheet` selects a worksheet by name; otherwise the active worksheet is read. `--output-dir` defaults to `output/` next to the script. The script does not search neighboring folders for input files.

### Preferred input layout

| Excel location | Meaning |
| --- | --- |
| B1 | Header: `CD8+ T cells` |
| C1 | Header: `Melanocyte` (or `Melanocytes`) |
| B2:B... | CD8+ T-cell counts per scan view |
| C2:C... | Corresponding melanocyte counts per scan view |

Column A is unused. Each row is one paired `(CD8+ T cells, melanocytes)` observation; all rows after the headers are read as one group. Completely blank rows are skipped; half-empty rows are rejected. At least three finite, non-negative, non-collinear points are required for 2D KDE. Use numeric cells; formulas require cached numeric results saved by a spreadsheet application.

### Legacy two-group layout

The original two-group layout remains supported when the preferred B1/C1 headers are absent:

| Excel cells | Meaning |
| --- | --- |
| D17:E23 | First group: CD8+ T-cell counts / melanocyte counts |
| D24:E30 | Second group: CD8+ T-cell counts / melanocyte counts |

`examples/synthetic_density.xlsx` is the earlier, explicitly synthetic example of that legacy layout. It is separate from the supplied research workbook:

```powershell
.venv\Scripts\python.exe density_cloud.py --input examples/synthetic_density.xlsx --output-dir output_synthetic
```

### Plot conventions and reproduction

- x axis: **No. of CD8+ T cells per scan view**; range 0–600.
- y axis: **No. of melanocytes per scan view**; range 0–500.
- The single research group uses the original dark green color and KDE bandwidth 0.58. The optional legacy second group uses light green and bandwidth 0.64.
- Each cloud is normalized to its own maximum and uses a cutoff of 0.04. Intensity shows within-group relative density rather than comparable absolute density between groups.
- Counts outside the original axis ranges are rejected so observations cannot disappear silently. Adjust the ranges and KDE grid in the code if larger limits are needed.

To reproduce the repository preview, run the research demo with the pinned dependencies. No random values are added to the data.

### Checks

```powershell
.venv\Scripts\python.exe -m unittest discover -s tests -v
```

The checks use Python's built-in `unittest`; `pytest` is not required.

## Authors

Project creators and lead maintainers:

- Chunying Li, Email: <lichying@fmmu.edu.cn>
- Yinghan Wang, Email: <wang.yinghan@qq.com>

## Credits

We would like to thank Shuo Yang for his assistance with this project.

## Academic citation

Academic citation information for this code will be added here when available.

## License

No license has been selected. Add an appropriate license if you intend to grant reuse rights.
