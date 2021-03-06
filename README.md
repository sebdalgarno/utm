
<!-- README.md is generated from README.Rmd. Please edit that file -->

# this is just a sketch! no actual code here yet…

# utm

<!-- badges: start -->
<!-- badges: end -->

`utm` is a simple, lightweight R :package: that has 1 main function:  
- `utm_zone()` - determine UTM zone from longitude and latitude

This returns the UTM zone and epsg as a named list and accepts a list of
coordinates as input.

For fun, there is also  
- `utm_sample_coords()` - sample a random lon/lat coordinate on earth

And for folks who live in British Columbia, there is  
- `utm_bc_stream()` - accepts an official [gazzetted stream name](TODO)
- `utm_bc_code()` - accepts an official BC [watershed code](TODO)

For example, let’s sample a random coordinate and get UTM zone and epsg

``` r
# library(utm)
# coords <- utm_sample_coords(4)
# utm_zone(coords)
```

The table for converting UTM zone to epsg is also provided as a data
object

``` r
# utm_lookup
```

A typical use case might be to transform a point to UTM given no
knowledge of where it is. This could be done e.g. with the
[sf](https://r-spatial.github.io/sf/) :package like this (given this
:package: is so small, I didn’t think it is worth including `sf` as a
dependency):

``` r
# utm <- sf_point %>%
#   sf::st_zm() %>% # remove Z coord if present
#   sf::st_transform(4326) %>% # ensure that in lat/lon
#   sf::st_coordinates() %>% # get coordinates as list
#   utm_zone() 
# 
# sf_point_utm <- sf::st_transform(sf_point, utm["epsg"])
```

Note that the special cases of Norway and Svalbard are taken into
account in the `utm_zone` function.
