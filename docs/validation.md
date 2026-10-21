# Reproduction record

## Local clean-environment validation

- Date: 2026-10-21 (Asia/Shanghai).
- Operating system: Windows 11 Pro; Python: Python 3.13.9.
- Hardware: Intel Core i5-14600KF, approximately 32 GB RAM.
- An independent virtual environment was created for this repository without system site packages.
- Dependencies were installed from PyPI using `requirements.txt`; `pip check` reported no broken requirements.
- Complete suite: 5 tests passed. The research demo exported PNG, PDF and SVG.

| Stage | Measured elapsed time |
| --- | --- |
| Create the empty virtual environment | 3.351 seconds |
| Install dependencies | 39.856 seconds |
| Research demo and export all formats | 1.579 seconds |

These are single-run observations, not performance guarantees. The two repository installations ran concurrently. Pip reused some cached wheels and downloaded others; these are new-environment installation times rather than cold-download benchmarks. Tests ran before the timed demo, so font caches may already have been populated.

## Resolved environment

The [complete Windows snapshot](../requirements-windows-py313.lock.txt) records the environment used in this check. `requirements.txt` remains the cross-platform direct-dependency list used by CI.

```text
contourpy==1.4.0
cycler==0.12.1
et_xmlfile==2.0.0
fonttools==4.67.0
kiwisolver==1.5.1
matplotlib==3.10.6
numpy==2.3.5
openpyxl==3.1.5
packaging==26.3
pillow==13.0.0
pyparsing==3.3.3
python-dateutil==2.9.0.post0
scipy==1.16.3
six==1.17.0
```

## Automated validation

The [Reproducibility checks workflow](https://github.com/misland4/CD8-T-cell_melanocyte_density_cloud/actions/workflows/ci.yml) installs dependencies, checks them, runs the complete suite and generates the research demo on Windows, Ubuntu and macOS with Python 3.13. Each run records its actual operating system and Python patch version. A configured matrix alone is not evidence of passing; inspect the individual job conclusions and logs.

Demo PNG/PDF/SVG files are retained as workflow artifacts for seven days. Font substitutions can change typography between operating systems even when input values and pairing are identical.
