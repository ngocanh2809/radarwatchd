# Introduction #

The analysis code is written in C/C++ using the libGD, sqlite and STL libraries.


# Details #

The code performs several functions:
  1. Loads images in radar directory searching for a specific station (NCR/reflectivity only for now) and performs analysis on each matching radar file:
    * Tracks precipitation in image
    * Locates all storm cells (current criterion is fixed threshold 50+ DBZ)
    * Performs basic analysis on cell: size, strength, weighted center of mass, average/max DBZ, standard deviation, etc
    * Writes radar image statistics and storm cell metadata to sqlite database
    * If storm cells found, radar image itself is additionally committed to database
  1. Analyzes radar images in time-domain and performs removal of non-relevant images
    * Sorts images by timestamp and arranges images into groups by searching for gaps in timeline
    * Marks images for removal if no storm data detected and not in chronological proximity to other images with storm activity (removal not actually performed yet)
    * Generates output data files for use with Gnuplot

Code will eventually be extended to provide additional functionality:

  * Track storm cell movement based upon fuzzy logic
  * Issue warnings if cells approaching specified location(s)
  * Perform analysis on Doppler velocity data to identify mesocyclone rotation (adding 3D support with multiple elevation angles from raw level I or II data to do properly)
  * Combine images from several adjacent stations into one composite file

Files used in analysis package:

  * **cached.cpp** - Main C++ analysis package
  * **cached.h** - Header file
  * **Makefile** - Makefile to compile
  * **graph-heatmap.plt**/**graph-pixelcount-xy.plt** - Gnuplot scripts