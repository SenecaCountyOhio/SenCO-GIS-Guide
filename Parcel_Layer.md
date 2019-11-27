# Seneca County Parcel Layer

#### Author
Brendan Cullen  
GIS Programmer/Analyst  
Seneca County Auditor’s Office  
October 2019

## Background
The Parcel Layer is controlled, maintained and developed by the Seneca County
Engineer’s Tax Map Office. The layer itself was originally produced
and maintained by Mark Zimmerman (the County Engineer) in a CAD environment.
It was later brought into an ArcView Landscape and eventually then loaded into
a Parcel Fabric.

The Parcels were originally maintained on paper, and drafted using different
techniques. The need for a digital representation was eventually brought into
light and Mark took it upon himself to learn GIS and develop the layer we use
today. The layer is maintained now by the Tax Map Staff.

Parcels are a critical base layer for many GIS operations. Accuracy is of key
importance due to the analytical nature of CAUV calculations and property
assessments. There are some errors in the dataset since the parcel layer is
really only meant for reference, however, if you notice an error and bring it to
their attention they will promptly fix it. When running a calculation on a
property, always double check for topology errors. Over time, there will be less
and less issues with the layer as issues are spotted.

## Cross-Department Data Sharing
The Engineer has a [Tax Parcel App](http://sencoeng-oh.maps.arcgis.com/apps/webappviewer/index.html?id=5bef53ea29e147c9a1f250994fd75f2d)
that is updated with the Tax Map Office's up-to-date parcel layer on a nightly
basis. A script located at "B:\Projects\Automated Tasks\Daily_Parcel_PULL" will
pull the parcel layer from the Tax Parcel App, create a backup of the outdated
parcel layer, and export a new feature class called "Current Parcels". The
current parcels layer is loaded into many of the map documents , and it is a
best to always use the most current information. This script is scheduled to run
every night.
