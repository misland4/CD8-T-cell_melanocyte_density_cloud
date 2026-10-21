# Research data dictionary

## Source and provenance

The project contact confirmed that `examples/research_density.xlsx` contains real research observations and that reuse is permitted. A named data license and its detailed scope have not yet been specified by the authors.

The workbook is a byte-for-byte copy of the supplied `Simulated dataset to demo the code.xlsx`; the original worksheet name `Simulated dataset` is retained. The historical source name is not used to classify the observations as synthetic.

- Source SHA-256: `248baa3371a525ef44e21161619536eaa1adfc047cfafd1316dd6b8d48035b8a`.
- Worksheet: `Simulated dataset`.
- Data range: B2:C8, seven paired observations in one group.

## Fields and interpretation

| Field | Excel location | Meaning used by the code | Recorded unit |
| --- | --- | --- | --- |
| CD8+ T cells | B1 header; B2:B8 values | Horizontal coordinate | Cell count per scan view, following the requested axis label |
| Melanocyte | C1 header; C2:C8 values | Vertical coordinate | Cell count per scan view, following the requested axis label |
| Observation ID | Not present | Input row order only | No subject identifier is inferred |
| Group | Not present | All seven rows are plotted together | One supplied group; no biological group name was supplied |

Column A is unused. Both values in a row are read together. The workbook does not state whether different rows belong to different subjects or multiple scan views from the same sample. Seven observations must therefore not be described as seven independent subjects without author information.

The observed CD8+ T-cell counts range from 33 to 549, and the melanocyte counts range from 7 to 432. These are descriptions of the supplied cells, not additional inclusion criteria.

## Display calculations

The plot is a two-dimensional joint KDE of the two cell counts with scatter points. The single research group uses dark green and bandwidth 0.58; color does not identify one cell type. Density is divided by its own maximum and values below 0.04 are masked. The script does not perform a hypothesis test, estimate subject-level independence or add observations.

## Research context awaiting author information

The supplied files do not specify the study/sample population, biological group name, number of subjects, scan-view area/magnification, cell-identification method or associated paper/figure. These fields will be added from the authors' description; they are not inferred from the numerical values.

`examples/synthetic_density.xlsx` is a separate, explicitly synthetic legacy example. It is not combined with the research workbook.
