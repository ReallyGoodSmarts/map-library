

waterfile:
	## I first downloaded all of the California water files and put them in 
	## a "water" directory. See the README in this directory.
	cd water; unzip '*.zip'
	npx mapshaper -i 'water/*.shp' combine-files \
		-simplify 40% \
		-merge-layers \
		-proj EPSG:4326 \
		-o format=geojson california_water.json

oakland-boundary:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip places 
	cd tmp; curl -O https://www2.census.gov/geo/tiger/GENZ2020/shp/cb_2020_06_place_500k.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/cb_2020_06_place_500k.shp \
		-filter 'NAME == "Oakland"' \
		-simplify 70% \
		-erase california_water.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson oakland_boundary.json
		
oakland-zips:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip us zip codes
	cd tmp; curl -O https://www2.census.gov/geo/tiger/TIGER2020/ZCTA5/tl_2020_us_zcta510.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/tl_2020_us_zcta510.shp \
		-simplify 70% \
		-clip oakland_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson oakland_zips.json

oakland-tracts:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip us zip codes
	cd tmp; curl -O https://www2.census.gov/geo/tiger/GENZ2020/shp/cb_2020_06_tract_500k.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/cb_2020_06_tract_500k.shp \
		-simplify 70% \
		-clip oakland_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson oakland_tracts.json

oakland-blockgroups:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip block groups
	cd tmp; curl -O https://www2.census.gov/geo/tiger/GENZ2020/shp/cb_2020_06_bg_500k.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/cb_2020_06_bg_500k.shp \
		-simplify 70% \
		-clip oakland_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson oakland_block_groups.json
		
oakland-blocks:
	# make the temporary directory
	mkdir -p tmp
	
	# download 2020 blocks
	cd tmp; curl -O https://www2.census.gov/geo/tiger/TIGER2020/TABBLOCK20/tl_2020_06_tabblock20.zip
	cd tmp; unzip '*.zip'
	
	npx mapshaper tmp/tl_2020_06_tabblock20.shp \
		-simplify 80% \
		-clip oakland_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson oakland_blocks_2020.json
	
	# clean up the temp folder
	rm -rf tmp
	mkdir -p tmp
	
	# download 2010 blocks
	cd tmp; curl -O https://www2.census.gov/geo/tiger/TIGER2020/TABBLOCK/tl_2020_06_tabblock10.zip
	cd tmp; unzip '*.zip'
	
	npx mapshaper tmp/tl_2020_06_tabblock10.shp \
		-simplify 80% \
		-clip oakland_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson oakland_blocks_2010.json
	

oakland-blockgroups-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper oakland_block_groups.json \
		-drop fields=id,STATEFP,COUNTYFP,TRACTCE,BLKGRPCE,AFFGEOID,NAME,NAMELSAD,LSAD,ALAND,AWATER \
		-o format=topojson for_datawrapper/oakland_block_groups_for_dw.json

oakland-tracts-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper oakland_tracts.json \
		-drop fields=id,STATEFP,COUNTYFP,TRACTCE,BLKGRPCE,AFFGEOID,NAME,NAMELSAD,LSAD,ALAND,AWATER \
		-o format=topojson for_datawrapper/oakland_tracts_for_dw.json
		
oakland-zips-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper oakland_zips.json \
		-drop fields=id,CLASSFP10,MTFCC10,FUNCSTAT10,ALAND10,AWATER10 \
		-each 'ZIP_CODE=ZCTA5CE10' \
		-o format=topojson for_datawrapper/oakland_zips_for_dw.json
		
oakland-blocks-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper oakland_blocks_2020.json \
		-drop fields=id,STATEFP20,COUNTYFP20,TRACTCE20,BLOCKCE20,NAME20,MTFCC20,UR20,UACE20 \
		-each 'GEOID=GEOID20, delete GEOID20' \
		-o format=topojson for_datawrapper/oakland_blocks_2020_for_dw.json
	npx mapshaper oakland_blocks_2010.json \
		-drop fields=id,STATEFP10,COUNTYFP10,TRACTCE10,BLOCKCE10,NAME10,MTFCC10,UR10,UACE10 \
		-each 'GEOID=GEOID10, delete GEOID10' \
		-o format=topojson for_datawrapper/oakland_blocks_2010_for_dw.json


berkeley-boundary:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip places 
	cd tmp; curl -O https://www2.census.gov/geo/tiger/GENZ2020/shp/cb_2020_06_place_500k.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/cb_2020_06_place_500k.shp \
		-filter 'NAME == "Berkeley"' \
		-simplify 70% \
		-erase california_water.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson berkeley_boundary.json
		
berkeley-zips:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip us zip codes
	cd tmp; curl -O https://www2.census.gov/geo/tiger/TIGER2020/ZCTA5/tl_2020_us_zcta510.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/tl_2020_us_zcta510.shp \
		-simplify 70% \
		-clip berkeley_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson berkeley_zips.json
	make clean

berkeley-set: berkeley-tracts berkeley-blockgroups berkeley-blocks

berkeley-tracts:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip us zip codes
	cd tmp; curl -O https://www2.census.gov/geo/tiger/GENZ2020/shp/cb_2020_06_tract_500k.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/cb_2020_06_tract_500k.shp \
		-simplify 70% \
		-clip berkeley_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson berkeley_tracts.json
	make clean

berkeley-blockgroups:
	# make the temporary directory
	mkdir -p tmp
	# download and unzip block groups
	cd tmp; curl -O https://www2.census.gov/geo/tiger/GENZ2020/shp/cb_2020_06_bg_500k.zip
	cd tmp; unzip '*.zip'
	npx mapshaper tmp/cb_2020_06_bg_500k.shp \
		-simplify 70% \
		-clip berkeley_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson berkeley_block_groups.json
	make clean
		
berkeley-blocks:
	# make the temporary directory
	mkdir -p tmp
	
	# download 2020 blocks
	cd tmp; curl -O https://www2.census.gov/geo/tiger/TIGER2020/TABBLOCK20/tl_2020_06_tabblock20.zip
	cd tmp; unzip '*.zip'
	
	npx mapshaper tmp/tl_2020_06_tabblock20.shp \
		-simplify 80% \
		-clip berkeley_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson berkeley_blocks_2020.json
	
	# clean up the temp folder
	rm -rf tmp
	mkdir -p tmp
	
	# download 2010 blocks
	cd tmp; curl -O https://www2.census.gov/geo/tiger/TIGER2020/TABBLOCK/tl_2020_06_tabblock10.zip
	cd tmp; unzip '*.zip'
	
	npx mapshaper tmp/tl_2020_06_tabblock10.shp \
		-simplify 80% \
		-clip berkeley_boundary.json remove-slivers \
		-proj EPSG:4326 \
		-o format=topojson berkeley_blocks_2010.json
	make clean
	
berkeley-datawrapper: berkeley-blockgroups-for-datawrapper berkeley-tracts-for-datawrapper berkeley-zips-for-datawrapper berkeley-blocks-for-datawrapper

berkeley-blockgroups-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper berkeley_block_groups.json \
		-drop fields=id,STATEFP,COUNTYFP,TRACTCE,BLKGRPCE,AFFGEOID,NAME,NAMELSAD,LSAD,ALAND,AWATER \
		-o format=topojson for_datawrapper/berkeley_block_groups_for_dw.json

berkeley-tracts-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper berkeley_tracts.json \
		-drop fields=id,STATEFP,COUNTYFP,TRACTCE,BLKGRPCE,AFFGEOID,NAME,NAMELSAD,LSAD,ALAND,AWATER \
		-o format=topojson for_datawrapper/berkeley_tracts_for_dw.json
		
berkeley-zips-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper berkeley_zips.json \
		-drop fields=id,CLASSFP10,MTFCC10,FUNCSTAT10,ALAND10,AWATER10 \
		-each 'ZIP_CODE=ZCTA5CE10' \
		-o format=topojson for_datawrapper/berkeley_zips_for_dw.json
		
berkeley-blocks-for-datawrapper:
	mkdir -p for_datawrapper
	npx mapshaper berkeley_blocks_2020.json \
		-drop fields=id,STATEFP20,COUNTYFP20,TRACTCE20,BLOCKCE20,NAME20,MTFCC20,UR20,UACE20 \
		-each 'GEOID=GEOID20, delete GEOID20' \
		-o format=topojson for_datawrapper/berkeley_blocks_2020_for_dw.json
	npx mapshaper berkeley_blocks_2010.json \
		-drop fields=id,STATEFP10,COUNTYFP10,TRACTCE10,BLOCKCE10,NAME10,MTFCC10,UR10,UACE10 \
		-each 'GEOID=GEOID10, delete GEOID10' \
		-o format=topojson for_datawrapper/berkeley_blocks_2010_for_dw.json

clean:
	rm -rf tmp
	
