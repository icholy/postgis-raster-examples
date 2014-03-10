postgis-raster-examples
=======================

[ST_MakeEmptyRaster](http://postgis.net/docs/RT_ST_MakeEmptyRaster.html)

``` sql
SELECT * FROM
  ST_MetaData(
    ST_MakeEmptyRaster(
      3, 3,  -- width, height
      0, 0,  -- origin (top-left corner)
      1, -1, -- pixel size, negative pixel size?
      0, 0,  -- skewx, skewy
      0      -- srid coordinate system (0 = None)
    )
  )
```

upperleftx | upperlefty | width | height | scalex | scaley | skewx | skewy | srid | numbands
-----------|------------|-------|--------|--------|--------|-------|-------|------|----------
0 | 0 | 3 | 3 | 1 | -1 | 0 | 0 | 0 | 0
