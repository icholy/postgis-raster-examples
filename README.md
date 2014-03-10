Postgis Raster Examples
=======================

[ST_MakeEmptyRaster](http://postgis.net/docs/RT_ST_MakeEmptyRaster.html)

``` sql
SELECT * FROM
  ST_MetaData(
    ST_MakeEmptyRaster(
      3, 3,  -- width, height
      0, 0,  -- origin (top-left corner)
      1, -1, -- scalex, scaley (pixel size, negative pixel size?)
      0, 0,  -- skewx, skewy
      0      -- srid coordinate system (0 = None)
    )
  )
```

upperleftx | upperlefty | width | height | scalex | scaley | skewx | skewy | srid | numbands
-----------|------------|-------|--------|--------|--------|-------|-------|------|----------
0 | 0 | 3 | 3 | 1 | -1 | 0 | 0 | 0 | 0


``` sql
SELECT x, y, ST_AsEWKT(geom)
FROM
  ST_PixelAsPolygons(
    ST_MakeEmptyRaster(
      3, 3,  -- width, height
      0, 0,  -- origin (top-left corner)
      1, -1, -- pixel size, negative pixel size?
      0, 0,  -- skewx, skewy ... :/ ?
      0      -- srid coordinate system (0 = None)
    )
  )
```

x | y | st_askewkt
--|---|---------------------------------------
1 | 1 | POLYGON((0 0,1 0,1 -1,0 -1,0 0))
1 | 2 | POLYGON((0 -1,1 -1,1 -2,0 -2,0 -1))
1 | 3 | POLYGON((0 -2,1 -2,1 -3,0 -3,0 -2)) 
2 | 1 | POLYGON((1 0,2 0,2 -1,1 -1,1 0))
2 | 2 | POLYGON((1 -1,2 -1,2 -2,1 -2,1 -1))
2 | 3 | POLYGON((1 -2,2 -2,2 -3,1 -3,1 -2))
3 | 1 | POLYGON((2 0,3 0,3 -1,2 -1,2 0))
3 | 2 | POLYGON((2 -1,3 -1,3 -2,2 -2,2 -1))
3 | 3 | POLYGON((2 -2,3 -2,3 -3,2 -3,2 -2)) 

