# Contributing and reporting problems

Report a reproducible problem through [GitHub Issues](https://github.com/misland4/CD8-T-cell_melanocyte_density_cloud/issues). Include the command, Python and operating-system versions, the error message and a small input you are authorized to share.

Install `requirements.txt` and run these checks before proposing changes:

```text
python -m unittest discover -s tests -v
python density_cloud.py --input examples/research_density.xlsx --output-dir output
```

Changes to scientific interpretation, data values, group labels or licensing require information from the authors. Preserve the supplied workbooks when changing code and keep display-only choices separate from observed values. Data fields and workbook hashes are recorded in [docs/data.md](docs/data.md).
