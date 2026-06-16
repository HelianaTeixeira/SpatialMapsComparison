# SpatialMapsComparison
Reproducible workflow in R using **spdep** to compute Bivariate Moran's I for grid-cell data.

Add spatial data to be analysed in folder **dataInput**.

**Input data requirements:**
It can be **raster** or **csv** or **shapefile**. 

If input data is Shapefile with point geometry, you should have values to compare in a single shapefile (e.g., posES and negES).

- `grid.shp` — geometry
- `grid.dbf` — attribute table with `NegES` and `PosES` columns' values
- `grid.shx` — shape index
- `grid.prj` — coordinate reference system (CRS)
- No missing values (or handle them explicitly) (zeros are accepted)

**Analytical logic:**

The analysis follows three sequential steps of increasing spatial specificity:

1. **Co-occurrence** (OR condition to cells selection) — do NegES and PosES share the same space?
2. **Pearson correlation** (AND condition to cells selection) — within shared space, are values correlated?
3. **Bivariate Moran's I** (AND condition to cells selection) — is that correlation spatially structured?

Summary of steps in script **bivariateMoranIndex.Rmd**, with indication of code chuncks that need user minimum edits (e.g., file name or tailor options for analyses):

1) Input data — **EDIT THIS**
2) Load & reproject
3) Choose neighbour method — **EDIT THIS**
4) Co-occurrence summary (OR condition — descriptive)
5) Pearson correlation (AND condition)
6) Build spatial weights (AND condition)
7) Global Bivariate Moran's I
8) Local Bivariate Moran's I (LISA)

LISA maps produced will be automatically saved in folder **outputs**, in 2 formats:

- TIFF (300 dpi, CMYK-compatible) and
- PDF vector format, ideal for resizing without quality loss.
