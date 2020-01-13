# Permit Field Inspections
The Seneca County Auditor's Office partners with a 3rd Party Vendor, [Pivot Point](https://pivotpoint.us/), to manage annual field inspections performed by our in-house inspector. Permits are assigned and statistics can be reviewed using their [web interface](https://field.pivotpoint.us/DataSetStats?dataSetID=7668ba65-3806-4dca-aa3a-494f27a272fb).

Pivot Point is sent our IasWorld AA407 report nightly, which contains our permit information. The script is  located here;
```
B:\Projects\Automated Tasks\Pivot_Point
```

Pivot Point provides an app that is currently installed on the Auditor's ipad. The app is configured to use a [ArcGIS Web Mapping Application](https://senecacountygis.maps.arcgis.com/home/item.html?id=c4ad0edf3b2440fab10de5361c47452f) to provide routing information for the field inspector. The web map collects time and locational information, as well as geotagged photos.
