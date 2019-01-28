# Big Data for Cities

Work from PPUA 5262 (Big Data for Cities) at Northeastern University

## Download Guide

Loading required packages - If you haven't downloaded this package yet, then go to the console pane in R and type: install.packages("sf") and then run this code

```
#For importing and extracting data set from geodatabase
library(sf)
```

The 'sf' package helps read files from geodatabases. Geodatabases have multiple kinds of files, including shapefiles and datatable files. Data table files are stored with .dbf extensions within the geodatabase.

Once you've downloaded the file geodatabase from MassGIS and unzipped it, you can read the .dbf files into R using this code:

```
RevereParcels <- st_read(dsn = "M248_parcels_sde.gdb", layer = "M248Assess")
```

Make sure you are referencing the name of the .gdb file, and that the gdb folder is located in the directory your R code is saved in (or that you specify the file path you need). The M248Assess table has all of the assessor's parcel records for the City of Revere. Once you've read them into an R data frame, you should be good to go.

### Look-up Table

There is another data table in the geodatabase that might be helpful. It includes a lookup table that gives a description for the various use codes listed in the parcel table. This is helpful if you need to know that a use code of '101' means that the parcel is a single-family home, etc.

```
USECODELOOKUP <- st_read(dsn = "M248_parcels_sde.gdb", layer = "M248UC_LUT")
```

### Additional Download Info: Saving data as a csv for future use:

If you want to write this data frame to a csv for use later, you can use the `write.csv()` function, where the first argument is the CSV you wish to write, and the second arugment is the file path and file name you want the csv to save to. 

```
write.csv(RevereParcels, "assessor.csv") 
```
It can be useful to write the dataframe you end with to a new CSV when finishing a data assignment, so that you preserve new variables you created. 