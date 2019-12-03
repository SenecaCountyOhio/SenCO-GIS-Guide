# Seneca County Parcel Layer

## Background
The Parcel Layer is maintained by the [Seneca County Engineer's](https://sencoeng.com/) Tax Map Office.
The layer itself was originally developed by Mark Zimmerman (the County
Engineer) in a CAD environment. It was later brought into an ArcView Landscape
and eventually then loaded into a Parcel Fabric.

Parcels were originally maintained on paper, and drafted using different
techniques. The need for a digital representation was eventually brought to
light and Mark took it upon himself to learn GIS and develop the layer we use
today. The layer is maintained by the Tax Map Staff using ArcGIS.


## Regular Data Updates
The Engineer has a [Tax Parcel App](http://sencoeng-oh.maps.arcgis.com/apps/webappviewer/index.html?id=5bef53ea29e147c9a1f250994fd75f2d)
that is updated with the Tax Map Office's up-to-date parcel layer on a nightly
basis. A script located at "B:\\Projects\\Automated Tasks\\Daily_Parcel_PULL" will
pull the parcel layer from the Tax Parcel App, create a backup of the now
outdated parcel layer, and export a new feature class called "Current Parcels".
The current parcels layer can be accessed at any time at "B:\\Projects\\Parcel
Update\\Parcel_Update.gdb". This script is scheduled to run every night.

## Data Integrity
Parcels are a critical base layer for many GIS operations. Accuracy is of key
importance due to the analytical nature of CAUV calculations and property
assessments. There are errors in the dataset since the parcel layer was
developed primarily for reference, not analysis. The Tax Map Office is
continually fixing errors when identified. When running an analysis on a
property, always double check for topology errors. Over time, there will be less
and less issues with the layer as issues are spotted.
