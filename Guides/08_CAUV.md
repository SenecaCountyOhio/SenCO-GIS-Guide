[Return to Homepage](../index.html)
# Current Agricultural Use Valuation Program

## Purpose
The purpose of this document is to provide an overview of Seneca County's
administration of the Current Agricultural Use Valuation program, as well as
identify changes to the process in 2019 and 2020.

## Background
In order to support Ohio's agricultural producers, the State of Ohio established
the [Current Agricultural Use
Valuation](https://www.tax.ohio.gov/real_property/cauv.aspx) (CAUV) program.
The program allows Land enrolled in CAUV to be taxed at agricultural-use value rates that are revised
by the State of Ohio annually, rather than market value. Each county in Ohio is
required to administer this program, as well as calculate acreage breakdown of
each property's agricultural-use by soil type.

In order to efficiently and accurately calculate the acreage breakdown, Seneca
County invested in a Geographic Information System (GIS). The GIS allows the
county to accurately map and maintain the agricultural-use and soil information,
as well as perform the complex analysis of breaking down the acreages of
agricultural-use by soil type.

When a property owner requests to be enrolled in the program, the County Auditor
must first determine if the property qualifies for CAUV. One of the following
requirements must be met in order to qualify:

- Land Devoted Exclusively for Agricultural Use >= 10 Acres. (*Listed Below*)

  | Agricultural Use    | Description                              |
  |---------------------|------------------------------------------|
  | Commodity Crops     | Corn, Soybean, Wheat, Oats, Etc.         |
  | Hay                 | Baled at least twice a year              |
  | Permanent Pasture   | Used for commerical animal husbandry     |
  | Commerical Woodland | Must have certified forestry plan        |
  | Other Crops         | Nursery Stock, Vegetables, Flowers, etc. |
  | Other Use           | Algaculture, Aquaculture, Aplculture     |

- Land in Accepted Conservation Program. (*Listed Below*)

  | Accepted Conservation Programs | Description                                                                 |
  |--------------------------------|-----------------------------------------------------------------------------|
  | Conservation Reserve Program   | Must provide FSA Contract & Map                                             |
  | Conservation Practice 25%      | Land used to abate soil erosion. Only accept up to 25% of all land in CAUV. |

- Gross annual income produced from Agricultural Products >= $2,500.(*Must
  provide evidence*)



Each year, individuals with property enrolled in CAUV are required to
submit a Renewal Application to the County Auditor. At that time, any changes to
the agricultural-use or income are recorded. The Auditor then reviews the
applications for errors, and determines if any properties no longer qualify. If
a individual fails to submit a Renewal Application, they are removed from the
program.

Occasionally, the program's requirements are updated by the State of Ohio, which
the County Auditors are required to comply with. Since 2017, the Renewal
Applications require a written and precise breakdown of all land enrolled in
CAUV. Listed below are the land types used in 2019;

| Anticipated land use for the current year                                        |
|----------------------------------------------------------------------------------|
| Commodity crops – corn/soybeans/wheat/oats                                       |
| Hay – baled at least twice a year                                                |
| Permanent pasture – used for commercial animal husbandry                         |
| Noncommercial woodland – contiguous to 10 (ten) acres of farmed land             |
| Commercial timber                                                                |
| Other crops – nursery stock/vegetables/flowers                                   |
| Homesite(s) – minimum 1 (one) acre per house                                     |
| Roads/waste/pond                                                                 |
| Conservation program – CRP/CREP/etc. (provide the contract and map)              |
| Conservation practices limited to 25% or less of the total acreage (provide map) |
| Other use, e.g. agritourism, biofuel production                                  |


The Seneca County Auditor's Office has developed and adopted a new GIS-centric
workflow to better manage updates and changes to acreage calculations, as well
as to assist land owners with submitting their Renewal Applications.


## GIS-Centric Workflow

The GIS-centric workflow adds 3 new methods to the previous administration
procedures;
- CAUV Database
- CAUV Web Map
- CAUV Form Application

These methods combined will have the following affect on the current workflow;
- Provide land owners easy access to their CAUV Values.
- Reduce the number of incorrectly keyed applications.
- Reduce the number of applications mailed back to land owners due to needed corrections on the form.
- Easily identify errors in either the application or the database.
- Easily identify applications that were never submitted to the office.

### CAUV Database

The CAUV database is a SQL database of each property's CAUV agricultural-use
acreages and gross income. [SQLite](https://sqlite.org/index.html) was used as
the database engine since the database can be stored in a common network
filesystem that multiple users to access without the need of a dedicated
database server. SQLite is also the recommended database system of the Library
of Congress for storing data.

A database of specifically CAUV related information had never been built, so
current records were derived from 2019's Renewal Applications. Overall, the
reported acreages are accurate but not very precise, meaning small changes in
almost every application needed to be made. To do this, the records were
compared to Agricultural Land values already in IasWorld's AG Land table. This
allowed errors to be easily identified and corrected.

AG Land has the following fields;

| AG Land Field | Description               |
|---------------|---------------------------|
| CON25         | Conservation Practice 25% |
| CONP          | Conservation Program      |
| CROP          | Cropland                  |
| DTCH          | Ditch                     |
| HOME          | Homesite                  |
| ROW           | Right of Way              |
| WOOD          | Woodland                  |
| WSTE          | Wasteland                 |


Although the AG Land table uses more generalized land types than CAUV, it is
more accurate than the submitted CAUV forms since AG Land values are calculated
using the GIS. The table below shows the relationship between CAUV land types
and AG land types;

| CAUV Land                   | AG Land           |
|-----------------------------|-------------------|
| Commodity Crop              | CROP              |
| Hay                         | CROP              |
| Permanent Pasture           | CROP              |
| Other Crop                  | CROP              |
| Other Use                   | CROP              |
| Noncommercial Woodland      | WOOD              |
| Commercial Woodland         | WOOD              |
| Homesite                    | HOME              |
| Roads/waste/pond            | ROW + WSTE + DTCH |
| Conservation Practices 25%  | CON25             |
| Conservation Program        | CRP               |


This relationship table was used to identify and correct errors in the Renewal
Applications. The values were then added to the new CAUV database.
Below is an example of a correction;

```
Example: A property has a total of 102 acres of “CROP” in AG Land, but the CAUV
agricultural use breakdown is 75 acres of "Commodity Crops" and 25 acres of
"Hay" (Only 100 acres total). The database adjusts to 77 Acres of Commodity
Crops and 25 Acres of Hay since AG Land is considered more accurate.
```

The logic used to calculate the acreage adjustment is identified below;

  *Note: Each application is analyzed in this order. Again, AG Land acreage
   is considered more accurate.*

- CROP == (Commodity Crop + Hay + Permanent Pasture + Other Crop + Other Use)
 - Extra acreage is removed from the highest value in group
 - Missing acreage is assigned to highest value in group


- WOOD == (Noncommercial Woodland + Commercial Woodland)
  - If there is only Commercial Woodland OR if there is only Noncommercial Woodland
    - Extra acreage is removed
    - Missing acreage is added
  - If there is both Commercial Woodland AND Noncommercial Woodland
    - Extra acreage is removed from Noncommercial Woodland
    - Missing acreage is added to Noncommercial Woodland


- HOME == Homesite == 1 Ac. Only Per Parcel with home on it
  - Extra acreage is removed
  - Missing acreage is added


- CON25 == Conservation Practices 25%:
  - Extra acreage is removed
  - Missing acreage is added


- CONP == Conservation Program:
  - Extra acreage is removed
  - Missing acreage is added


- Roads/Waste/Pond == (ROW + WSTE + DTCH)
  - Opposite of other logic, AG Land is more specific than CAUV
  - Extra acreage is removed
  - Missing acreage is added


- Total AG LAND == Total CAUV LAND == Total Acreage of all Parcels
  - If not equal, these cases need to be individually analyzed and adjusted manually

*Note: The database built from this process is only considered a
__Recommendation__, as agricultural-use may change year to year, which the AG
Land table may not reflect. As errors or changes are identified by land owners,
the database will become much more accurate.*


### CAUV Web Map

In order to provide the land owners easy access to their values, a Web Map was
developed using ArcGIS Online's Web App Builder. The Auditor's Office already
has several applications and GIS layers hosted on ArcGIS Online.


The CAUV database was joined to the current parcel layer, and non-CAUV parcels
were removed. The layer's pop-ups were configured to provide all the information
needed for a land owner to fill out the requested form. The search bar in the
Web Map was configured to use the layer's Application Number field (Unique ID of
Renewal Applications). Any private information about the parcels were then
removed (i.e. Owner Name).

[Link to CAUV 2020 Web Map](https://arcg.is/1a5K05)

### CAUV Form Application

To assist the Auditor's Office with reviewing and submitting each application
to the CAUV database, a [CAUV Form Application](http://192.168.26.116:5000/signin)
was developed using the python web-application framework
[Flask](https://palletsprojects.com/p/flask/). The application runs on the local
intranet, so only computers on the Auditor's network can access the web page.

The application serves as a Graphical User Interface (GUI) wrapper around the
CAUV database, so users can easily input a submission's values, check for errors
against the database, and submit the new values to the database.

The application's serve and database are stored in the O:Drive which only the
Auditor's Office has access to;

```
O:\\GIS\\CAUV_Form
```

*Note: To run the server the .bat script on the GIS-PC desktop must be ran. The
application only works if the server is running.*


[Link to CAUV Form Application's code repository](https://github.com/bren96/CAUVForm)


## CAUV Procedures Outline:
The following is an overview of the Seneca County Auditor's workflow;

#### 1. Send out Renewal & Initial Applications

- Generate Mailing List using IasWorld
- Print Applications
- Mail Applications


#### 2. Process Incoming Renewal Applications

  - Input values into [CAUV Form Application](http://192.168.26.116:5000/signin)

    - If validated, update in IasWorld. Scan application and
      attach to parcels.
    - If there is an error, add note to application and put in basket to be
      returned to applicant.
    - If an application should be reviewed in the field, set field review flag
      in IasWorld and include why in Note Field.
    - If application does not meet income requirements, indicate so in note field in IasWorld.



#### 3. Send out First Warnings

  - Send applications with errors back to the applicants.


#### 4. Repeat Step 2

#### 5. Send out Second Warnings

  - Include more serious letter and more detailed error note.


#### 6. Repeat Step 2

#### 7. Field Review

- Pull all "flagged for field review" applications and notes using IasWorld's Inquire.
- Send work order list to Pivot Point
- Field check parcels of each Application

#### 8. Office Review

  - Using notes from Field Check, repeat step 2


#### 9. Issue Denial or Removal Notices

  - Any applicants that haven't returned their application, have under required
    income 3 years in a row, or do not qualify for the program are sent a Denial
    or Removal Notice.



## Field Review Stage

The following are more detailed notes on CAUV Field Review Stage;

#### 1. Pre-Field
- Assign Work Orders using Pivot Point's Work Order Manager
- Download Work Orders to Pivot Point's Field App
- Work by township/word OR Work by Map

#### 2. At Site
- Review CAUV Flag Review Note to determine necessary checks
- If there is a dwelling go to the front door & knock/ring doorbell twice
- If homeowner answers, explain reason for visit and verify/correct necessary data
- If no one is home leave a doorhanger explaining the reason for visit and request owner to call office
- Make necessary notes/changes/recommendations in Pivot Point Field App
- Take photos of dwellings, all outbuildings/land
- Set status of Work Order in Pivot Point Field App

#### 3. Final Review at Site
- Review changes
- Hit "Update Work Order"
- Move on to next Parcel (Repeat Step 2)

#### 4. Post-Field
- Upload notes and photos using Pivot Point Field App
