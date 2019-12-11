[Return to Homepage](../index.html)
# Current Agricultural Use Valuation Program

## Purpose
The purpose of this paper is to outline Seneca County's administration
procedures of the Current Agricultural Use Valuation program, as well as
document changes to these procedures in 2019 and 2020.

## Background
In order to support Ohio's agricultural producers, the State of Ohio established
the [Current Agricultural Use
Valuation](https://www.tax.ohio.gov/real_property/cauv.aspx) (CAUV) program.
Land enrolled in CAUV is taxed at agricultural-use value rates that are revised
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



Each year, individuals with property that is enrolled in CAUV are required to
submit a Renewal Application to the County Auditor. At that time, any changes to
the agricultural-use or income are reported. The Auditor then reviews the
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

To assist land owners with submitting their Renewal Applications, and the
Auditor with managing updates and changes to acreage calculations, the Seneca County
Auditor's Office has developed and implemented a new GIS-centric
workflow.

## GIS-Centric Workflow

The GIS-centric workflow adds 3 new methods to the previous administration
procedures;
- CAUV Database
- CAUV Web Map
- CAUV From Application

These methods combined will have the following affect on the current workflow;
- Provide land owners easy access to their CAUV Values.
- Reduce the number of incorrectly keyed applications.
- Reduce the number of applications mailed back due to errors on the form.
- Easily identify errors in either the submission or the database.
- Easily identify applications that were never submitted to the office.

### CAUV Database

The CAUV database is a SQL database of each property's CAUV agricultural-use
acreages and gross income. These values were derived from 2019's submitted
Renewal Applications, and then compared to Agricultural Land values already in
IasWorld's AG Land table. This allowed errors to be easily identified and
corrected.

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
Example: A property has a total of 110 acres of “CROP” in AG Land, but the CAUV
agricultural use breakdown is 75 acres of "Commodity Crops" and 25 acres of
"Hay" (Only 100 acres total). The database adjusts to 85 Acres of Commodity
Crops and 25 Acres of Hay since AG Land is considered more accurate.
```

The logic used to calculate the acreage adjustment is identified below;

- CROP == (Commodity Crop + Hay + Permanent Pasture + Other Crop + Other Use)
 - Extra acreage is taken from the highest value in group and assigned to Road/Waste/Pond
 - Missing acreage is taken from Road/Waste/Pond and assigned to highest value in group


- WOOD == (Noncommercial Woodland + Commercial Woodland)
  - If there is only Commercial Woodland OR if there is only Noncommercial Woodland
    - Extra acreage is assigned to Roads/Waste/Pond
    - Missing acreage is taken from Roads/Waste/Pond
  - If there is both Commercial Woodland AND Noncommercial Woodland
    - Extra acreage is taken from Noncommercial Woodland and assigned to Roads/Waste/Pond
    - Missing acreage is taken from Roads/Waste/Pond and assigned to Noncommercial

- HOME == Homesite == 1 Ac. Only Per Parcel with home on it
  - Extra acreage is assigned to Roads/Waste/Pond
  - Missing acreage is taken from Roads/Waste/Pond

- CON25 == Conservation Practices 25%:

- CONP == Conservation Program:

- Roads/Waste/Pond == (ROW + WSTE + DTCH)
  - Opposite of other logic, the AG Land is more specific that the CAUV app in
    this case.
  -



- Total AG LAND == Total CAUV LAND == Total Acreage of all Parcels
  - These cases need to be individually analyzed, and adjusted manually. In this
    case, AG Land should most likely be updated to match parcel acreages.



*Note: The database built from this process is only considered a
__Recommendation__, as agricultural-use may change year to year, which the AG
Land table may not reflect. As errors are identified by land owners, the
database will become much more accurate.*


### CAUV Web Map

In order to provide the land owners easy access to their values, a Web Map was
developed using ArcGIS Online. The Auditor's Office already has several
applications and GIS data layers hosted on ArcGIS Online, and it is quick and
easy to create public-facing web applications using the ArcGIS Online's Web App
Builder.

[Link to CAUV 2020 Web Map](https://arcg.is/1a5K05)

The CAUV database was joined to the current parcel layer, and non CAUV parcel
were removed. The layer's pop-ups were then configured to provide all the
information needed to fill out the paper form. The search bar in the Web Map was
then configured to use the layer's Application Number field (Unique ID of
Renewal Applications). Any private information about the parcels were then
removed i.e. Owner Name.


### CAUV Form Application

To assist the Auditor's Office with reviewing and then adding each application
to the new database, a Forms Application was developed using the python
web-application framework [Flask](https://palletsprojects.com/p/flask/). The
application runs on the local intranet, so only computers on the Auditor's
network can access the web page. The application serves as a GUI wrapper around
the CAUV database, so the office clerks can easily input a submission's values,
check for errors against the database, and submit the new values to the
database.

[Link to CAUV Form Application's code repository](https://github.com/bren96/CAUVForm)


## General Procedures Outline:
1. Send out Renewal & Initial Applications

  1. Generate Mailing List using IasWorld
  2. Print Applications
  3. Mail Applications


2. Process Incoming Renewal Applications

  - Input values into CAUV Form Application

    - If validated, update in IasWorld. Scan application and
      attach to parcels.
    - If there is an error, add note to application and put in basket to be
      returned to applicant.
    - If an application should be reviewed in the field, set field review flag
      in IasWorld and include why in Note Field.



3. Send out First Warnings

  - Send applications with errors back to the applicants.


4. Repeat Step 2

5. Send out Second Warnings

  - Include more serious letter and more detailed error note.


6. Repeat Step 2

7. Field Review

  1. Pull all flagged for field review applications and notes in IasWorld's Inquire.

  2. Upload list to Pivot Point Field App

  3. Field check parcels of each Application

8. Office Review

  - Using notes from Field Check, repeat step 2


9. Issue Denial or Removal Notices

  - Any applicants that haven't returned their application, have under required
    income 3 years in a row, or do not qualify for the program are sent a Denial
    or Removal Notice.



## Field Review Stage
