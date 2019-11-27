# Seneca County Addressing

#### Author
Brendan Cullen  
GIS Programmer/Analyst  
Seneca County Auditor’s Office  
October 2019  

## Purpose
The purpose of this paper is to document the current Addressing Authorities in Seneca County, outline Seneca County’s addressing procedure, and identify issues with the integrity and maintenance of the Seneca County Address Dataset.

## Background
Addressing refers to the process of assigning an address to a property or
structure. Addresses are used by various public and private institutions as the
principal means of locating and communicating with an individual or
organization. Seneca County primarily assigns and maintains addresses for mail
delivery and emergency services. The public relies upon local governments to
maintain an efficient and orderly addressing system.

The Seneca County Emergency Management Association (EMA) is actively pursuing
implementation of a Next Generation 9-1-1 (NG 911) system to improve routing and
situational awareness for emergency services. A Geographic Information System
(GIS) is an integral component of NG 911. Seneca County has invested in the
development and maintenance of accurate and up-to-date GIS datasets for the NG
911 system, including an Address Point Dataset.

Over time, the technology used to maintain the Address Point Dataset has
changed, as well as the entities responsible for maintaining it. Addresses
within Seneca County are assigned and maintained by various government entities,
each utilizing different procedures. The entities then report address changes to
the primary Addressing Authority responsible for maintaining the Address Point
Dataset.

## Addressing Authorities in Seneca County
Addressing Authorities are the government entities responsible for the assignment of addresses. Currently, there are nine Addressing Authorities in Seneca County. Figure 1 lists the Addressing Authorities and their contact information. Incorporated areas of the county are responsible for their own addressing system. The Ohio Revised Code (ORC) affirms the county only has the right to assign and change addresses in unincorporated areas. The ORC directly states:

> The board of county commissioners may designate street names and assign numbers
> to buildings along streets in unincorporated areas. The owners of such buildings
> shall number or renumber such buildings in accordance with the numbers assigned
> by the county commissioners (ORC 303.021).

Effective April 1st, 2019, the Seneca County Auditor’s Office manages the assignment of addresses in unincorporated areas (Seneca County Resolution 19-60). The Seneca County Auditor’s Office serves as the primary Addressing Authority for the county and is responsible for maintaining and distributing the Address Point Dataset.

## Unincorporated Areas Addressing Procedure

An address consists of the following values;

1. House number
2. Unit number
3. Street Direction
4. Street Name
5. Street Type
6. City
7. State
8. Zip Code

Example:  
Seneca County Auditor's Office  
109 S. Washington St. Suite 2206 Tiffin, OH 44883

|Type | Value|
|----------|-----------|
| House Number | 109 |
| Unit Number | Suite 2206 |
| Street Direction | S |
| Street Name | Washington |
| Street Type  | St |
| City | Tiffin |
| State | OH |
| Zip Code | 44883 |


Seneca County uses an addressing grid indicated in Figure 2, “Highway Map of
Seneca County, Ohio” produced by the Seneca County Engineer. Each axis generally
aligns with the Township Sections of Seneca County. The Township Sections are
approximately 1 square mile, creating an evenly spaced grid of address blocks
across the county. The following values need to be determined (in this order) to
calculate the final House Number;

##### Address Block
A block outlined by the addressing grid. The addressing
blocks are in increments of 1000. Each block has a pair of (X, Y) values. X is
the axis E/W, and Y is the axis N/S.

##### Street Name
The name of the street of the new address. The street that
provides main access the structure or property should be used.

##### Street Direction
The street prefix assigned to the street. The Street Name
is used to determine the street prefix. If there is no street prefix, then the
general cardinal direction (N/S or E/W) the street runs is used.

##### Address Block Starting Line
The axis line that is used to measure the House
Number. If the Street Direction is N/S, the Address Block’s Y Value is used. If
the Street Direction is E/W, the Address Block’s X Value is used.

##### Address Distance
The distance (in miles) from the new address to the
Address Block Starting Line.

##### Side
The side of the street the address is on. If the address is West of a
N/S street or South of an E/W street, the address is even. If the address is
East of a N/S street or North of an E/W street, the address is odd. The House
Number should be rounded to fit within the Even/Odd pattern.

##### House Number
The combination of the address’s Address Block and the Address
Distance (taking into consideration which Side of the road the address is on).
The Address Distance is multiplied by 1000, and then added to the Address
Block’s Starting Line value.

```
Example: An address is requested for a house in Hopewell Township. According to
the addressing axis, the house will be in (4000 W, 1000 S). The main access to
the house is on W US 224, which means the 4000 W Address Block Starting Line
will be used to measure the Address Distance. The house is measured to be 0.321
Miles from the 4000 W axis line. The House Number should be 4321 W US 224;
however, the address is on the even side of the road. In this case, the address
would be rounded up to 4322 W US 224.
```

Addresses can only be requested by the property owner. An address can be
requested by email, phone, or in person, and no formal documents are required.
The Auditor’s Office has set up a specific email for address requests,
addressing@senecacountyohio.gov . After the address is created, an Official
Notification of Address form is filled and given either digitally or in paper to
the requestor. All Official Notification of Address forms are filed and logged
with the Auditor’s Office. The form can be found at
“B:\Projects\Addressing\County_Addressing\BLANK_OFFICIAL NOTIFICATION OF
ADDRESS.docx”. The logs of requests can be found at “B:\Information
Requests\ADDRESS_REQUESTS”.

## Utilization of GIS in Addressing Workflow
The following GIS layers contain all the information needed to assign an address;
-	Current Addresses
-	Current Parcels
-	Road Centerlines
-	Township Sections
-	ZIP Districts
-	Highway Map
-	Aerial Imagery

A .aprx can be found at “B:\Projects\Addressing\County_Addressing”, which
contains all these layers. The measure tool in ArcGIS Pro can be used to
determine the distances outlined in the Addressing Procedure. As many of the
fields in Current_Address feature class should be filled as possible. Figure 3
provides a description of each filed, and how the data should be entered.

A python geoprocessing script has begun to be developed in order to automate
this process. The code repository can be found here
https://github.com/bren96/Addressing_Workflow. *NOTE:The current state is still
in a debugging phase*

## Data Integrity & Maintenance Issues
There are several issues with the current addressing workflow and GIS dataset;
1. There is very little communication between the Seneca County Auditor’s Office
and incorporated areas. Many new address requests have been forwarded to the
other Addressing Authorities since the property or structure is in an
incorporated area. After, there is no information sent to the Auditor’s Office
that the address was created. This means there are addresses in the county that
are not within the 911 system.

2. An audit of the GIS dataset identified approximately 6% of the addresses have
some type of error. The audit looked for Addresses with missing, conflicting, or
non-logical required attributes. Many of these addresses fall within
incorporated areas, therefore, the respective Addressing Authorities will need
to assist in making corrections to the dataset.

3. There are approximately 2,000 Addresses in the Auditor’s iASWorld Database
that are not in our 911 system (about 8% of the total addresses in the county).
This may be a result of various issues, such as data entry error or addresses
lost in the transfer of the address dataset over the years.

## Discussion & Conclusion
Overall, Seneca County effectively manages addressing, but not efficiently.
Seneca County needs to improve the reporting workflow between Addressing
Authorities, as well as improve the overall integrity of the Address GIS
dataset.

To improve the reporting workflow, I recommend Seneca County should
utilize the many web-GIS tools the Auditor’s Office has access to through its
ESRI license. There are customizable web-based apps the Auditor’s Office can
develop that would greatly simplify and automate the process of reporting
address changes.

To improve data integrity, I recommend a committee backed by
the EMA should be formed to review the data errors. With the assistance of the
addressing authorities, address errors should be individually reviewed and
corrected. This would not require any changes to addresses, just validation of
addresses before they are corrected in the 911 system. These improvements can be
accomplished; however, this would call for the mutual effort of the Seneca
County Auditor’s Office, Seneca County EMA, and all City and Village Addressing
Authorities in order to be a productive use of Seneca County’s time and
financial resources.
## Figures
#### Figure 1 – Seneca County Addressing Authorities

| Region | Addressing Authority | Contact Information |
| ------ | -------------------- | ------------------- |
| Seneca County (Unincorporated Areas) | Seneca County | Brendan Cullen - GIS |
| | | addressing@senecacountyohio.gov |
| | | (419) 447-0692 |
| | | 109 S. Washington St. Suite 2206 Tiffin, OH 44883 |
| City of Tiffin | City of Tiffin | Dan Brickner - Zoning Inspector |
| | | dbrickner@tiffinohio.gov |
| | | (419) 448-5425 |
| | | 51 E. Market St. Room A20, Tiffin, OH 44883 |
| City of Fostoria | Compliance/Project Manager | compliance@fostoriaohio.gov |
| | | (419) 435-9775 |
| | | 213 S. Main St., Fostoria, OH 44830 |
| Village of Attica | Village Administrator | voa@bright.net |
| | | (419) 426-9611 |
| | | 20 S. Main St., Attica, OH 44807 |
| Village of Bettsville | Village Administrator | villageofbettsville@yahoo.com |
| | | (419) 986-5636 |
| | | 308 Emma St., Bettsville, OH 44815 |
| Village of Bloomville | Village Administrator | bloomville.ohio@gmail.com |
| | | (419) 983-4745 |
| | | 10 Beeghly Ave, Bloomville, OH 44818 |
| Village of Green Springs | Village Administrator | streets@villageofgreensprings.com |
| | | (419) 603-8150 |
| | | 120 Catherine St., Green Springs, OH 44836 |
| Village of New Riegel | Village Administrator | - |
| | | - |
| | | 14 Findlay St., New Riegel, OH, 44853 |
| Village of Republic | Village Administrator | - |
| | | (419) 595-2839 |
| | | 219 Washington St., Republic, OH 44867 |


#### Figure 2 – Highway Map of Seneca County, Ohio

![Highway Map of Seneca County, Ohio](/Img/HighwayMap_front_Print-1.jpg)
  
#### Figure 3 – Address Shapefile Attribute Metadata

| General Name | Attribute Field | Data Type | Description |
|------------- | --------------- |-----------| ----------- |
| Object ID | OBJECTID | Numeric | Unique ID |
| Shape | Shape | Geometry | Required Geometry Field |
| Feature ID | FEATUREID | Numeric | Reserved |
| Road Type | ROADTYPE | Text | The type of road the address is on. P – Private, M – Municipal, T – Township, C – County, U – US Highway, S – State Route, I – Interstate, R – Ramp, N – State Park Roads, F – Federal Park Roads |
| Road Number| ROADNUMBER | Text | The number of the road the address is on, where appropriate. For example, US 224 would have a road number of 224. |
| House Number | HOUSENUM | Numeric | Address house number. |
| Unit Number| UNITNUM | Text | Address house/lot/unit number. |
| House Number Range | HNRANGE | Text | One entrace for multiple addresses |
| Unit Information| UNITEXTRA | Text | Additonal address information: Building, Floor, or Other |
| Unit Building | BUILDING | Text | Unit building name. |
| Unit Floor | FLOOR | Text | Unit floor name. |
| Street Prefix | ST_PREFIX | Text | Address street name prefix.|
| Street Name| ST_NAME | Text | Address street name. |
| Street Type| ST_TYPE | Text | Address street name type. RD – Road, ST – Street, BLVD – Boulevard, AVE – Ave or Avenue, CT – Court, CIR – Circle |
| Street Suffix | ST_SUFFIX | Text | Address street suffix. N – North, S – South, E – East, W – West |
| Street Suffix 2 | ST_SUFFIX2 | Text | Populated with the primary intercardinal directions. NE - Northeast, SE - Southeast, NW - Northwest, SW - Southwest |
| Municipality | MUNI | Text | City or Village name the address is located in.|
| Alternative Street Prefix | ALTPREFIX | Text | Address alternative street name prefix. |
| Alternative Street Name | ALTNAME | Text | Address alternative street name.|
| Alternative Street Type | ALTTYPE | Text | Address alternative street name type. RD – Road, ST – Street, BLVD – Boulevard, AVE – Ave or Avenue, CT – Court, CIR – Circle |
| Alternative Street Suffix | ALTSUFFIX | Text | Address alternative street suffix. N – North, S – South, E – East, W – West |
| Alternative Street Suffix 2 | ALTSUFFIX2 | Text | Populated with the alternate intercardinal directions. NE - Northeast, SE - Southeast, NW - Northwest, SW - Southwest|
| Subdivision| SUBDIV| Text | Subdivision name, if applicable.|
| Village | VILLAGE | Text | Village Name|
| | SIDE | Numeric | Reserved |
| Side | ABSSIDE | Text | Address side of the road. N – North, S – South, E – East, W – West |
| Structure Type | STRUC_TYPE | Numeric | Type of structure. 1 – House, 2 – Duplex, 3 – Trailer, 4 – Single Apartment, 5- Secondary structure, 6 – Utility, 7 – Commercial, 8 – Address with no visible structure, 9 – Multiple unit apartments with unique suffixes, 12 – Multiple unit apartments with unique addresses |
| Source| SOURCE| Numeric | Address data collection source |
| General Comment | COMMENT | Text | Field comment about the structure. |
| Field Note | FIELDNOTE | Text | Field notes recored by GPS field technicians |
| State | STATE | Text | 2 letter postal code. OH - Ohio |
| County| COUNTY| Text | County code. SEN – Seneca County|
| Address | LSN | Text | Full Address|
| Alternative Address | ALSN | Text | Alternate Full Address|
| House Number Label | LHN | Text | Contains house number and unit number. Used for display in AccuGlobe E-911 |
| New Designation | NLFIDNEW | Text | New designation for road due to renumbering |
| Zip Code | ZIPCODE | Text | USPS zip code |
| Mailing City | USPS_CITY | Text | USPS city based on ZipCode |
| Segment Id | SEGID | Numeric | Road segement the point is assocaited with by name set |
| Segment Type | TSSEGID | Numeric | Road segement the point is associated with by type set |
| Point Length | PT_LEN| Numeric | Distance along segment from beginning of the segment. See Coordinate ID for units |
| Milepost | MPVAL | Double | Milepost value for point |
| Federal Information Processing Standards Code | FIPSCODE | Text | Federal Information Processing Standards Code |
| Community Name | COMM | Text | Community Name |
| X Coordinate | X| Double | X Coordinate|
| Y Coordiante | Y| Double | Y Coordiante|
| Date Modified | DATE_MOD | Date | Date the address was last modified. |




 
## References
- ORC 303.021
- Seneca County Resolution 19-60
