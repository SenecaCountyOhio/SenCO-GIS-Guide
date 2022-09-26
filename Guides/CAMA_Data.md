# CAMA Data


Seneca County works with vendors who require certain data from our CAMA system to be sent to them every day. This data is then required to be zipped and sent to our website 
host to update the website with the up-to-date data.

Nightly, a scripts called AA407 is run by TylerTech and is output in Y:\AT_CMCLEOD\AA407 (as of 9/26/2022). This data needs to be zipped in the morning so that a script can 
then grab that zip file and send it to our website host.

This is also done with real estate data, which has a script that also runs nightly, but is output at Y:\AT_NGAUTAM\BL320OH. There are 3 output files for this, the folders 
are the three most recent folders. The data in these folders will need to be zipped for scripts to grab and sent to our webhost.

There's scripts in place to grab each of the zip files for these data sets to sned through an FTP link to our webhost. The old zip files from the day before should be 
deleted before making a new zipfile of the most recent data.





