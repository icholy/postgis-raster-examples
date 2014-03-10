postgis-raster-examples
=======================

``` sql
SELECT * FROM
  ST_MetaData(
    ST_MakeEmptyRaster(
      3, 3,  -- width, height
      0, 0,  -- origin (top-left corner)
      1, -1, -- pixel size, negative pixel size?
      0, 0,  -- skewx, skewy ... :/ ?
      0      -- srid coordinate system (0 = None)
    )
  )
```
