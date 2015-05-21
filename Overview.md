# Introduction #

This project came about after reading a [post at IBM](http://www.ibm.com/developerworks/library/os-weathermaps/index.html) one day on making your own weather alerts with GD.  This is an attempt at writing a custom radar analysis package to track and predict thunderstorm cells using NEXRAD WSR-88D Doppler radar provided by the NWS.



# Details #

The project is collection of several parts:

**[daemon](BackgroundDaemon.md)** - Downloads and archives radar reflectivity and velocity images from NOAA

**[analysis](AnalysisPlatform.md)** - Analyses radar images and stores data in an sqlite database

**UI** - User interface to view radar images and metadata