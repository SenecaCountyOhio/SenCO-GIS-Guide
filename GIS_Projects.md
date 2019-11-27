# GIS Project Descriptions
Author: Brendan Cullen, 2019
Email: brendancullen996@gmail.com
Phone: 914 841 8889

This document outlines many of the responsibilities of this position.
I have edited, contributed to, and re-organized notes left by Alex Rodd in 2018
in order to produce this document. He provided context as to how much of the
important data was created and is maintained.


In general, I have broken up the GIS position's responsibilities into three
general project types; Ongoing, Annual, and Special.



Ongoing Projects | General Description

	Ongoing projects are tasks and responsibilities that will never have a due
	date. These projects are maintained regularly, some even on a daily basis.
	Many of these processes have been automated. The scheduled tasks related to
	this position are under "GIS_Scripts" in the Windows Task Scheduler app.

Ongoing Projects | Seneca County Parcel Layer


Ongoing Projects | Addressing

	An official paper was written to explain the Addressing Process, and can be
	found at "B:\Projects\Addressing\County_Addressing\Seneca County Addressing
	White Paper.docx".

	In short, the Seneca County Auditor’s Office manages the assignment of
	addresses in unincorporated areas. The Seneca County Auditor’s Office serves
	as the primary Addressing Authority for the county and is responsible for
	maintaining and distributing the Address Point Dataset.

	The previous individual responsible for assigning Addresses was Mike Klaiss at
	the Seneca County Emergency Management Association. His email is
	Mklaiss@senecacountyohio.gov and his phone number is 419 447-0266 Ext 13. Mike
	Klaiss is retiring in 2020, so if he no longer works there, contact Brendan
	Cullen.


Ongoing Projects | Auditor's DDTI WebGIS

	The Seneca County Auditor's Website (http://www.senecacountyauditor.org), has
	a WebGIS (http://www.senecacountyauditor.org/Map.aspx) that is used internally
	and by the Public to view tax records and parcel information. The WebGIS and
	website is maintained by a company called DDTI and we provide them the
	data. The configurations are slightly different, and its best to have the most
	current data on the website, so a script was developed to automate this
	process. The script is located at "B:\Projects\Automated Tasks\DDTI". This
	computer is scheduled to send them the GIS data nightly, and Elizabeth has a
	scheduled task to send them the CAMA data nightly as well. Currently this
	computer only sends the reconfigured Address and Parcel data.


Ongoing Projects | EMA's Callworks WebGIS

	The Seneca County Emergency Management Association partnered with Motorola to
	manage 911 calls. Motorola also has a WebGIS system called Emergency CallWorks
	which they maintain and we provide the data. Motorola only updates the WebGIS
	once a month, and so there is a scheduled task that runs the first of every
	month. The script is located here "B:\Projects\Automated Tasks\ECW". Most of
	the data they need is very rarely updated. Currently only Addresses are
	updated monthly.


Ongoing Projects | Land Use/Cover Layer


Annual Projects
	CAUV
	Permit Inspections
	Splits & Combines

Special Projects
	CRA WebMap
	Seneca County GeoLibrary (ArcGIS Hub)
	Develop Con25 Program
	CAUV Form Application
	Automate Land Use Workflow
	Automate Addressing Workflow
	Splits & Combines Tracker
	Pictometry Spring Flight
