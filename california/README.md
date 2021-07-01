# California

## Easy-download Links

To make it super-easy to download, here are the same map files contained in `for_datawrapper` but linked in a way that is simple to download. These are TopoJSON files optimized, simplified, and reprojected for use as base data maps with [Datawrapper](https://datawrapper.de).

### Oakland geo files

Depending on your browser, either click on the links directly or right-click (also option-click on a Mac) and choose "Save link as ..." or the equivalent. 

- [oakland_blocks_2010_for_dw.json](https://raw.githubusercontent.com/ReallyGoodSmarts/map-library/main/california/for_datawrapper/oakland_blocks_2010_for_dw.json)
- [oakland_blocks_2020_for_dw.json](https://raw.githubusercontent.com/ReallyGoodSmarts/map-library/main/california/for_datawrapper/oakland_blocks_2020_for_dw.json)
- [oakland_block_groups_for_dw.json](https://raw.githubusercontent.com/ReallyGoodSmarts/map-library/main/california/for_datawrapper/oakland_block_groups_for_dw.json)
- [oakland_tracts_for_dw.json](https://raw.githubusercontent.com/ReallyGoodSmarts/map-library/main/california/for_datawrapper/oakland_tracts_for_dw.json)
- [oakland_zips_for_dw.json](https://raw.githubusercontent.com/ReallyGoodSmarts/map-library/main/california/for_datawrapper/oakland_zips_for_dw.json)

## Sources

US Census Bureau:

- https://www.census.gov/geographies/mapping-files/time-series/geo/cartographic-boundary.html
- https://www2.census.gov/geo/tiger/TIGER2020/
- https://www2.census.gov/geo/tiger/TIGER2020/2020_TL_Shapefiles_File_Name_Definitions.pdf

## Water files

You can actually download all of the water files by using FTP, at ftp://ftp2.census.gov/.

For the water files, you can go directly to ftp://ftp2.census.gov/geo/tiger/TIGER2020/AREAWATER (just put it in a browser). No login credentials necessary.

The files are numbered by state FIPS code, so all of the California files begin with `tl_2020_06...`.

I made a "water" directory in this folder and downloaded those files into there. 

Then run `make waterfile`

This makes a water file for the entire state.
