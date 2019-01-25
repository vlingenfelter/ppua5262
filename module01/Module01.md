Module01
================
Violet Lingenfelter
January 20, 2019

Revere Tax Assessor Data
------------------------

My group was assigned to look at tax assessor data. We chose to look at data for Revere, MA, because we were interested in looking at property values around transit locations. The data we are looking at is stored in a geodatabase.

This geodatabase includes:

-   "M248TaxPar", the feature layer that parcels are associated with
-   "M248Assess", the assessor data (including values, ownership, land use)
-   "M248OthLeg", which includes legal data associated with each parcel (like Registry of Deeds info)
-   "M248\_LUT", a look up table for the MISC\_TYPE and the LEGAL\_TYPE attributes found in respective .dbf files within the .gdb
-   "M248UC\_LUT", look up table for the state use codes found in the assessing table
-   and "M248Misc" which includes miscellaneous land use type info (like wetland, island, water, etc)

This data was downloaded at [MassGIS](http://massgis.maps.arcgis.com/apps/View/index.html?appid=4d99822d17b9457bb32d7f953ca08416). Information on which land use codes correspond to land use types came from [Land Use Codes](https://www.mass.gov/files/documents/2016/08/wr/classificationcodebook.pdf), per the MassGIS website.


    # import packages for reading .gdb
    require(rgdal)
    require(sf)

    gdb <- "~/Downloads/M248_parcels_gdb/M248_parcels_sde.gdb"

    # List all feature classes in a file geodatabase
    subset(ogrDrivers(), grepl("GDB", name))
    fc_list <- ogrListLayers(gdb)
    # print(fc_list) <<< this would print the names of associated layers, if I needed to see that 

    # Read the feature class
    fc <- readOGR(dsn=gdb, layer="M248TaxPar") 

    # read the assessor database file 
    # (no geometries associated, error is thrown and it turns the .dbf into a dataframe)
    # sort the assessor values by total combined parcel value
    assessor <- sf::st_read(dsn = gdb, layer = "M248Assess")

    # Duplicate Geoms = true becaus multiple Assessor data points have same LOC_ID (to be fixed later)
    fc <- merge(fc, assessor, by="LOC_ID", duplicateGeoms=TRUE)

    # View the feature class (make sure the geometries match the boundaries of Revere MA)
    plot(fc, main="REVERE, MA", lwd=0.075)


    # Get most valuable parcel
    assessor <- assessor[rev(order(assessor$TOTAL_VAL)),]
    module01 <- assessor[1,]

    # exact middle (median) value parcel
    module01[2,] <- assessor[floor(NROW(assessor)/2),]

    # get most valuable single residence parcel
    module01[3,] <- assessor[assessor$USE_CODE=='101', ][1,]

    # get oldest church 
    assessor <- assessor[order(assessor$YEAR_BUILT),]
    module01[4,] <- assessor[assessor$USE_CODE=='960', ][1,]

    print(module01[,c("TOTAL_VAL", "LOT_SIZE", "OWNER1", "YEAR_BUILT", "UNITS", "STYLE", "STORIES", "NUM_ROOMS", "SITE_ADDR")])

Data Story
----------

Located at 230 Beach St, every Sunday, the oldest church in Revere MA opens its doors to the community. The First Congregational Church was built in 1849, the same year that whispers of "Eureka! I found gold" began to spread eastward from California. Now the parcel it sits on and its 3 stories are worth more than $1 million, according to tax assessors.

71 years later, at 673 Revere Beach Blvd, a 2 story, multi-garden style house was built that would later be owned by Travelers Revere Realty Trust, and would be the most valuable single occupancy home by tax assessment. 40 years later, the year that the first Massachusetts-born Catholic was elected as president, a bungalow was built at 175 Fenley St. that sits on what would become the median valued parcel in Revere.

The same year that a magnitude 6.3 earthquake destroyed an estimated 60,000 houses in Indonesia, 2006, an apartment building was built at 19 Overlook Ridge Dr. This apartment is comprised of 412 units, over 9.87 acres, and is worth more than $70 million. It is the most valuable building in Revere by tax estimates.
