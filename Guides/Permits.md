# Permit Field Inspections
The Seneca County Auditor's Office partners with a 3rd Party Vendor, [Pivot Point](https://pivotpoint.us/), to manage annual field inspections performed by our in-house inspector. Permits are assigned and statistics can be reviewed using their [web interface](https://field.pivotpoint.us/DataSetStats?dataSetID=7668ba65-3806-4dca-aa3a-494f27a272fb).

Pivot Point is sent our IasWorld AA407 report nightly, which contains our permit information. The script is  located here;
```
B:\Projects\Automated Tasks\Pivot_Point
```

Pivot Point provides an app that is currently installed on the Auditor's ipad. The app is configured to use a [ArcGIS Web Mapping Application](https://senecacountygis.maps.arcgis.com/home/item.html?id=c4ad0edf3b2440fab10de5361c47452f) to provide routing information for the field inspector. The web map collects time and locational information, as well as geotagged photos.

Once a year, usually sometime in February, the permits for field inspections will need to be loaded onto the ipads. The process for that can be found [here](https://github.com/SenecaCountyOhio/Pivot_Point_Config_Scripts). 

This process is to make sure that all of the permits from the previous year are loaded and ready to go for our field inspectors to check. This will only be done **ONCE** per year. The above link walks through how the data should be formatted to be sent to pivot point. 

Pivot Point will also require PDFs of the property record cards to be sent to them of the commercial and residential work orders that are created. This is done through the scripts that are set up in IasWorld, then exported to list and downloaded and FTP'd to Pivot Point.
