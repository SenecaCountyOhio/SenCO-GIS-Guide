# Seneca County Auditor WebGIS

The [Seneca County Auditor](http://www.senecacountyauditor.org), has
a [WebGIS](https://senecaoh-auditor-classic.ddti.net/Map.aspx?Todo=Init) that is used internally
and by the public to view tax records and parcel information. The WebGIS and
website is maintained by Pivot Point. The data for the parcels and addresses that Pivot
Point uses is taken from the County's ArcGIS online account.

~~This script has been updated to only pull the address and current parcel shapefiles
from Seneca County's ArcHub. If the service URL for either of the shapefiles,
then all that needs to be done is to put the new service URL where the old
URL was to direct the script to pull from the new location.~~

The scripts that were used to send address and parcel data to our old website manager
has been deactivated, but kept in-place in the B: drive. The only data that gets sent to 
Pivot Point is CAMA data, and that is done nightly by TylerTech when they run the new CAMA
data every night.


A google analytics Monitor Dashboard was created to track user interaction with our GeoLibrary
https://analytics.google.com/analytics/web/#/p395442249/reports/intelligenthome?params=_u..nav%3Dmaui

Summer of 23: 
Search functionality was broadened to include MH_PIN (from the newly created MH_Layer) Parcel Owner or Parcel address.
The Layer for these is hosted as Parcel_Address_LAyer and it should update continuously as sales, splits and other real estate transactions occur
