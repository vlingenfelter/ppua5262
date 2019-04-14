Final
================
Violet Lingenfelter
March 22, 2019

Correlation
-----------

For looking at correlations, I decided calculate a matrix for all variables I might find interesting in a sort of exploratory approach. I included the following variables in my matrix:

-   building, land, and total values
-   list price
-   number of rooms
-   residential area
-   building area

This matrix can be seen below.

``` r
# import package that we need
require(Hmisc)

# look at relationships between a TON of columns 
# columns looked at: building, land, other, and total value, lot size, list price, year built, number of rooms, and residential area size. 
correlations<-rcorr(as.matrix(luxury[c(5,6,8,12,32,33,36,45)]))
# class(correlations)


require(formattable)
r <- do.call(rbind.data.frame, correlations[1])

r <- round(r, digits = 3)

# look at r
r <- formattable(r, list(BLDG_VAL = color_tile("white", "#a3dec9"),
                    LAND_VAL = color_tile("white", "#a3dec9"),
                    TOTAL_VAL = color_tile("white", "#a3dec9"),
                    LS_PRICE = color_tile("white", "#a3dec9"),
                    UNITS = color_tile("white", "#a3dec9"),
                    RES_AREA = color_tile("white", "#a3dec9"),
                    NUM_ROOMS = color_tile("white", "#a3dec9"),
                    LUXURY = color_tile("white", "#a3dec9")))

r
```

<table class="table table-condensed">
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
BLDG\_VAL
</th>
<th style="text-align:right;">
LAND\_VAL
</th>
<th style="text-align:right;">
TOTAL\_VAL
</th>
<th style="text-align:right;">
LS\_PRICE
</th>
<th style="text-align:right;">
UNITS
</th>
<th style="text-align:right;">
RES\_AREA
</th>
<th style="text-align:right;">
NUM\_ROOMS
</th>
<th style="text-align:right;">
LUXURY
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
r.BLDG\_VAL
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #e0f4ed">0.347</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #aae0cd">0.919</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ebf8f3">0.218</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #fafdfc">0.064</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #b7e5d5">0.793</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d7f0e7">0.485</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d7f0e7">0.468</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.LAND\_VAL
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #e3f5ee">0.347</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #c1e8da">0.688</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f9fcfb">0.073</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #fefefe">0.023</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #e8f6f1">0.306</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f5fbf9">0.184</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #e5f5f0">0.324</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.TOTAL\_VAL
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #aae0cd">0.919</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #c0e8da">0.688</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #edf8f4">0.198</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #fafdfc">0.059</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #bce7d7">0.744</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #daf1e9">0.455</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d4efe5">0.502</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.LS\_PRICE
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #eff9f6">0.218</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #fafdfc">0.073</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f1faf7">0.198</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.013</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f9fdfc">0.127</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.094</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.067</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.UNITS
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.064</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.023</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.059</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.013</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff">0.076</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f8fcfb">0.160</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #fbfdfc">0.107</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.RES\_AREA
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #b7e5d4">0.793</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #e4f5ef">0.306</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #bce6d7">0.744</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f4fbf8">0.127</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f9fcfb">0.076</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d7f0e8">0.479</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #dcf2ea">0.420</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.NUM\_ROOMS
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d5f0e6">0.485</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #eff9f6">0.184</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d8f1e8">0.455</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f7fcfa">0.094</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f1faf6">0.160</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d6f0e7">0.479</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #bee8d9">0.717</span>
</td>
</tr>
<tr>
<td style="text-align:left;">
r.LUXURY
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d7f0e7">0.468</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #e2f4ee">0.324</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #d3efe5">0.502</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f9fdfc">0.067</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #f6fbf9">0.107</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #dcf2ea">0.420</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #bfe8d9">0.717</span>
</td>
<td style="text-align:right;">
<span style="display: block; padding: 0 4px; border-radius: 4px; background-color: #a3dec9">1.000</span>
</td>
</tr>
</tbody>
</table>
From looking at this matrix, we can see how correlated some of our variables are with each other. To make this more readily apparent, I chose to highlight each piece of the table based on the value of r. We can see that the least correlated variable to any other variable is LS\_PRICE. This means that list prices have little correlation with any of the other variables I chose to include in the matrix.

An interesting column to look at is the NUM\_ROOMS column. We can see that the number of rooms a building on a parcel had has a strong positive correlation with every variable besides LS PRICE. This is interesting because it is not something I expected.

``` r
require(ggplot2)
require(cowplot)
 
# make scatter plot with regression 
plot1 = ggplot(luxury, aes(x=LUXURY, y=RES_AREA)) +
  theme_classic() +
  geom_point(size=2, color="#a3dec9", shape=17) + 
  geom_smooth(method=lm, color="#499491") +
  xlab("Luxury") + 
  ylab("Residential Area")

plot2 = ggplot(luxury, aes(x=LUXURY, y=TOTAL_VAL)) +
  theme_classic() +
  geom_point(size=2, color="#a3dec9", shape=17) + 
  geom_smooth(method=lm, color="#499491") +
  xlab("Luxury") + 
  ylab("Total Parcel Value")

plot_grid(plot1, plot2)
```

![](final_files/figure-markdown_github-ascii_identifiers/plot-1.png)

``` r
regression<-lm(LUXURY~TOTAL_VAL+UNITS+RES_AREA, data=luxury)


summary(regression)
```

    ## 
    ## Call:
    ## lm(formula = LUXURY ~ TOTAL_VAL + UNITS + RES_AREA, data = luxury)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -5.2446 -0.7310 -0.0972  0.6014 17.6002 
    ## 
    ## Coefficients:
    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) -3.895e+00  1.578e-01 -24.685  < 2e-16 ***
    ## TOTAL_VAL    9.760e-06  4.418e-07  22.089  < 2e-16 ***
    ## UNITS        7.705e-01  1.341e-01   5.746 9.72e-09 ***
    ## RES_AREA     2.238e-04  4.297e-05   5.207 2.00e-07 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.233 on 4488 degrees of freedom
    ##   (5 observations deleted due to missingness)
    ## Multiple R-squared:  0.2625, Adjusted R-squared:  0.262 
    ## F-statistic: 532.5 on 3 and 4488 DF,  p-value: < 2.2e-16

``` r
luxury<-merge(luxury,data.frame(regression$residuals),by='row.names',all.x=TRUE)
```

``` r
par(bg = "#e8fff2")
plot(luxury$LUXURY, luxury$regression.residuals, 
     ylab="Residuals", 
     xlab="Luxury", 
     main="Linear Regression Residuals",
     pch = 17,
     col = "#F98866",
     family = "mono", 
     col.main = "#274F3B", 
     col.lab = "#274F3B",
     fg = "#80BD9E") 
abline(0, 0) 
```

![](final_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-1-1.png) \#\# Regression

We can see from this regression, where we looked at total value, number of units, and residential area as explanatory variables for number of rooms, that our model is okay but missing some variables. We can see that 89% of the variation in number of rooms can be explained by total value, number of units, and residential area. We can map these residuals so as to see if any geographic areas are not explained by this non geographically weighted regression.

``` r
require(rgdal)
require(sp)

gdb <- "../M248_parcels_gdb/M248_parcels_sde.gdb"

assessor_geo<-readOGR(dsn=gdb, layer="M248TaxPar")
```

    ## OGR data source with driver: OpenFileGDB 
    ## Source: "/Users/vlingenfelter5/Desktop/bigData/M248_parcels_gdb/M248_parcels_sde.gdb", layer: "M248TaxPar"
    ## with 12838 features
    ## It has 12 fields

``` r
require(ggplot2)
require(ggmap)
```

    ## Loading required package: ggmap

    ## Warning: package 'ggmap' was built under R version 3.4.4

    ## Google's Terms of Service: https://cloud.google.com/maps-platform/terms/.

    ## Please cite ggmap if you use it! See citation("ggmap") for details.

    ## 
    ## Attaching package: 'ggmap'

    ## The following object is masked from 'package:cowplot':
    ## 
    ##     theme_nothing

``` r
require(maptools)
```

    ## Loading required package: maptools

    ## Warning: package 'maptools' was built under R version 3.4.4

    ## Checking rgeos availability: TRUE

    ## 
    ## Attaching package: 'maptools'

    ## The following object is masked from 'package:Hmisc':
    ## 
    ##     label

``` r
require(rgeos)
```

    ## Loading required package: rgeos

    ## Warning: package 'rgeos' was built under R version 3.4.4

    ## rgeos version: 0.4-2, (SVN revision 581)
    ##  GEOS runtime version: 3.6.1-CAPI-1.10.1 
    ##  Linking to sp version: 1.3-1 
    ##  Polygon checking: TRUE

    ## 
    ## Attaching package: 'rgeos'

    ## The following object is masked from 'package:Hmisc':
    ## 
    ##     translate

``` r
assessor_geo<-fortify(assessor_geo, region = "LOC_ID")
assessor_geo<-merge(assessor_geo,luxury,by.x='id',by.y='LOC_ID',duplicateGeoms=TRUE)

assessor_geo<-assessor_geo[order(assessor_geo$order),]
```

``` r
library(RColorBrewer)
my_colors = brewer.pal(9, "BrBG") 
my_colors = colorRampPalette(my_colors)(6)
ggplot() + 
  geom_polygon(aes(x=long, y=lat, group=group, fill=regression.residuals), data=assessor_geo) +
  scale_fill_gradientn(colors = my_colors)
```

![](final_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-3-1.png)

We can see from this map that there is a little cluster of parcels by the beach where ther is a low number of rooms but potentially high expected value given our regression model. This suggests to me that there is a geographic element that is missing in our model.

Conclusion
----------

From this exploratory analysis, I conclude that I want to look further into the effect the number of rooms a building has on its value. I think I would like to look at how this relationship changes based on the building code that a parcel is coded under.
