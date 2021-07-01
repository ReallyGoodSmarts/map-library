# California


## Sources

US Census Bureau:

- https://www.census.gov/geographies/mapping-files/time-series/geo/cartographic-boundary.html
- 

## Water files

You can actually download all of the water files by using FTP, at ftp://ftp2.census.gov/.

For the water files, you can go directly to ftp://ftp2.census.gov/geo/tiger/TIGER2020/AREAWATER (just put it in a browser). No login credentials necessary.

The files are numbered by state FIPS code, so all of the California files begin with `tl_2020_06...`.

I made a "water" directory in this folder and downloaded those files into there. 

Then run `make waterfile`

This makes a water file for the entire state.
