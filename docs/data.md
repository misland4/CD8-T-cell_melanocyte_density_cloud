# Data dictionary and author-confirmed methods

## Source and provenance

The author confirms that the seven-row example is **simulated demonstration data**. It represents seven biological samples, with one imaging field of view per sample and no repeated fields from the same sample. This describes the example's intended structure, rather than seven measured study observations or seven confirmed human subjects.

`examples/research_density.xlsx` is a copy of the supplied `Simulated dataset to demo the code.xlsx`. The historical repository filename is retained for compatibility and does not imply real observations. The original worksheet name `Simulated dataset` is unchanged. This author clarification supersedes the earlier real-data wording in version 1.0.0.

- Original source SHA-256 (before removing author properties): `248baa3371a525ef44e21161619536eaa1adfc047cfafd1316dd6b8d48035b8a`.

- Repository workbook SHA-256 after removing creator/last-modified-by properties: `46ef4c5f9557f8bd58071c73d61ea0b2cc16fe08e06a858dee89ec5231dabd5e`. Only `docProps/core.xml` changed; all cells, styles, worksheets and other workbook entries are byte-identical to the source.
- Worksheet: `Simulated dataset`.
- Data range: B2:C8, seven paired counts in one group.
- Data and exported figures: [CC BY 4.0](../LICENSES.md).

## Fields and interpretation

| Field | Excel location | Meaning | Unit |
| --- | --- | --- | --- |
| CD8+ T cells | B1 header; B2:B8 values | Horizontal coordinate | Cell count per scan view |
| Melanocyte | C1 header; C2:C8 values | Vertical coordinate | Cell count per scan view |
| Observation ID | Not present | Input row order only | One represented field/sample per row; no supplied subject ID |
| Group | Not present | All seven rows plotted together | One supplied group; no biological group name supplied |

Column A is unused. Both cell counts from the same field are read together. CD8+ T-cell values range from 33 to 549 and melanocyte values from 7 to 432. These describe the included simulated values, not inclusion criteria or estimated population ranges.

Confirmed axis labels:

- x: **No. of CD8+ T cells per scan view**.
- y: **No. of melanocytes per scan view**.

## Author-provided imaging/counting method

> Images were acquired via a 10/20 × 0.5 objective lens for quantitative analysis. Z-stacks were captured at a resolution of 512 × 512 pixels and are presented as maximum intensity projections. The numbers of melanocytes and CD8+ T cells per sample were quantified using the “Analyze Particles” function in ImageJ.

The objective notation is reproduced as supplied. This related imaging-method description does not change the simulated status of the included numerical workbook. The plotting script takes existing cell counts as input; it does not process images or run ImageJ.

## Display calculations

The plot is a two-dimensional joint KDE over the two cell counts, overlaid with scatter points. The single supplied group uses dark green and bandwidth 0.58; color identifies the plotted group rather than a cell type. Density is divided by its own maximum and values below 0.04 are masked. The authors confirm the current bandwidth and do not require these display details in the paper's methods. The script performs no significance test and adds no observations.

## Study context deferred until publication

The authors will update study background, source description and the corresponding paper/figure upon publication. A biological group name, physical field area and definitions of the objective notation have not been supplied. The manuscript is unpublished; cite the software repository in the meantime.

`examples/synthetic_density.xlsx` is a separate, manually specified 14-pair legacy fixture with two color groups. It is not combined with the author-provided seven-row example.
