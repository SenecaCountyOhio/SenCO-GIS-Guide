GIS Project Descriptions
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

	The Parcel Layer is controlled, maintained and developed by the Seneca County
	Engineer’s Tax Map (office next door). The layer itself was originally produced
	and maintained by Mark Zimmerman (the County Engineer) in a CAD environment.
	It was later brought into an ArcView Landscape and eventually then loaded into
	a Parcel Fabric.

	The Parcels were originally maintained on paper by Dawn, and drafted using
	different techniques. The need for a digital representation was eventually
	brought into light and Mark took it upon himself to learn what he could of GIS
	and has developed the layer we use today. The layer is maintained now by the
	Tax Map Staff (currently Dawn and Alexa) who are under the guidance of Mark.

	For the Auditor, the Parcels are a critical base layer for many GIS
	operations. Accuracy is of key importance due to the analytical nature of CAUV
	calculations and property assessments. There are some errors in the dataset
	since the parcel layer is really only meant for reference, however, if
	you notice an error and bring it to their attention they will promptly fix it.
	When running a calculation on a property, always double check for topology errors.
	Over time, there will be less and less issues with the layer as issues are spotted.

	The Engineer has a Tax Parcel App
	(http://sencoeng-oh.maps.arcgis.com/apps/webappviewer/index.html?id=5bef53ea29e147c9a1f250994fd75f2d)
	that is updated with the parcel layer on a nightly basis. A script located at
	"B:\Projects\Automated Tasks\Daily_Parcel_PULL" will pull the parcel layer
	from the Tax Parcel App, and create a new feature class called "Current
	Parcels". The current parcels layer is loaded into many of the map documents ,
	and it is a best to always use the most current information. This script is
	scheduled to run every night as long as this computer is left running.



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

	An official was written to explain the development and maintenance of the Land
	Use/Cover Layer. The paper can be found at "B:\Projects\Land Use\Seneca County
	Land White Paper.docx".

	In short, Seneca County invested in GIS in order to develop and maintain a
	Land Code Dataset that maps every parcel’s Land Codes. The original Land Code
	Dataset included cover and uses of land and was developed by individually
	assessing each parcel in Seneca County. The Land Codes are used by the Seneca
	County Auditor’s Office in 3 different ways; 1) Valuation of a property’s
	residual or agricultural land. 2) Current Agricultural Use Valuation (CAUV).
	3) Determining if a property is eligible for CAUV.

	As the dataset’s breadth expanded, it was decided in 2019 that the single Land
	Code dataset should be separated between the General Land Codes and Land
	Programs. With this system, conservation practices and other land contract
	programs can be maintained separately from the General Land Codes. The two
	datasets can then be combined when used for valuation of properties.

	This paper explains where the GIS data is and how the final layer is created.
	Julie Adkins and Kelly Zoeller are the best people to go to with more general
	questions regarding the land use codes, but if you have questions about the
	GIS data you should contact Brendan Cullen.


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
