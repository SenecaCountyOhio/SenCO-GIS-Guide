# Seneca County Auditor WebGIS

The [Seneca County Auditor](http://www.senecacountyauditor.org), has
a [WebGIS](http://www.senecacountyauditor.org/Map.aspx) that is used internally
and by the public to view tax records and parcel information. The WebGIS and
website is maintained by a company called DDTI. The Seneca County Auditor's
Office provides them updated data regularly. The data configurations are
slightly different, so a script was developed to automate this process. The
script is located at "B:\\Projects\\Automated Tasks\\DDTI".

This script has been updated to only pull the address and current parcel shapefiles
from Seneca County's ArcHub. If the service URL for either of the shapefiles,
then all that needs to be done is to put the new service URL where the old
URL was to direct the script to pull from the new location.
