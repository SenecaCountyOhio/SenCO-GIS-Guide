# Seneca County Land Code Dataset
Brendan Cullen - 2019

## Purpose
The purpose of this paper is to provide documentation of Seneca County’s Land
Dataset and outline improvements made to the structure and maintenance of the
dataset in 2019.

## Background
Land information (i.e. the cover and use of land) is vital to the daily
operations of Seneca County. There are many ways to interpret land information,
and different organizations have developed similar, yet varying systems. In the
Seneca County Auditor’s Office there is a difference between Land Use
Codes, which are determined by the State of Ohio, and Land Codes, which are
determined by the County Auditor. A parcel is assigned one Land Use Code, which
describes the overall use of the land, and at the same time assigned multiple
Land Codes, which describe specific sections of the parcel.

The Seneca County Auditor’s Office uses Land Codes in 3 distinct ways;
1. Valuation of a property’s residual or agricultural land.
2. Current Agricultural Use Valuation (CAUV).
3. Determining if a property is eligible for CAUV.

Although each of these processes use land information, each have specific
definitions of land that sometimes require different levels of detail. Seneca
County invested in a Geographic Information System (GIS) in order to develop and
maintain a Land Code Dataset that maps every parcel’s Land Codes. The original
Land Code Dataset included a mix of cover and uses of land and was developed in
2004 by the Seneca County Engineer and Seneca County Regional Planning
Department. Around 2017, the original layer was stripped down and rebuilt using
new aerial imagery from Pictometry by Alex Rodd of the Seneca County Auditor's
Office.

In recent years, the types of agricultural uses and conservation programs
recognized in CAUV has increased, and so the Land Code Dataset has grown to
reflect these changes. Figure 1 details the current attributes included in the
2017 Land Use Dataset. Since the dataset’s breadth expanded, it was decided that
the single Land Code dataset should be separated between the Land Codes and Land
Programs. With this system, conservation practices and other land contract
programs can be maintained separately from the generalized Land Codes. The two
datasets can then be combined when used for valuation of properties.

## Improved GIS Dataset Structure
Rather than maintain one large dataset trying to describe Land Codes and Land
Programs, the improved workflow will separate General Land Codes and Land
Programs information. Land Codes usually describes physical land types
(Woodland, River, Cropland, etc.) while Land Programs describe Federal, State,
or County managed land contracts that identify how people are using the land
(Conservation, Commercial Woodland, Golf Course, etc.)

The new structure uses smaller datasets that are more manageable, and describe
similar yet independent land information. The layers can then be combined in
order to build a single dataset for property valuation. Figure 2 outlines the
individual land dataset’s types, codes, and descriptions.

**The General Land Code layer acts as the initial base all other Land Programs
are added upon.**


Example: A farm in the CAUV program could have wetlands, half of which are under
a FSA Conservation Contract. With the current system, the Land Code for half the
wetland would be CRP, without identifying what the land under the contract
originally was. Using the new system, the land is represented as wetland under a
conservation contract. This allows for the general land cover to be
maintained as well as property owner specific land use, which changes much more
often.


## New GIS Workflow
The Land Update Workflow Geodatabase & Toolbox contain the GIS layers and a
geoprocessing tool to combine the GIS layers. The project folder is located at
“B:\\Projects\\Land Use\\Land Update Workflow”. The tool’s only required input
is a path to the Land Update Workflow geodatabase, however, the geodatabase must
contain a feature class named “Land_General” and a feature class named
“Land_Programs”. The tool will output a feature class to the Geodatabase named
“Land_Combined”.

**Only the Land_Combined layer should be used when assessing a property and
should never be directly edited.**

Edits should only be made to the Land_General or Land_Programs layers. Figure 3
provides descriptions of the fields in the Land_General and Land_Programs
feature classes;

## Dataset Integrity
The dataset currently has a few inaccuracies that should be identified.

1. The Land_Programs layer is missing a lot of vital information and has not be
regularly maintained to the proper standards.
2. Due to how the dataset was maintained previously, a lot of general land
information was lost when a land program was mapped. All land under a land
program should be re-mapped according to the Land_General standards.
3. A process to more accurately represent residential properties should be
investigated.
4. No current system in place to validate Conservation Practices 25%.

## Discussion & Conclusion
Thanks to the hard work of many individuals with Seneca County, a very accurate
land dataset has been developed. With this new workflow, the dataset’s overall
integrity will improve, and the dataset will continue to be efficiently
maintained. As regulations by the State of Ohio or the needs of the Auditor’s
Office change, this dataset can be adjusted without having to manipulate this
new workflow.

## Figures

### Figure 1 – Old Land Use Types, Codes, & Descriptions

| LAND USE                        |CODE| DESCRIPTION                        |
|---------------------------------|:--:|------------------------------------|
| Animal Husbandry                |  3 | Buildings or Structures that House |
|                                 |    | Animals for a Commercial purpose.  |
|                                 |    | Science of breeding and caring for |
|                                 |    | Farm Animals.                      |
| Commercial                      |  6 | Land with Class C/ or Land that is |
|                                 |    | used Commercially, Not Residual or |
|                                 |    | Homesite - To be broken down into  |
|                                 |    | Primary/Secondary Site.            |
| Conservation Practice 25%       | 24 | Practice use of grass waterways,   |
|                                 |    | terraces, diversions,              |
|                                 |    | filter strips, field borders,      |
|                                 |    | windbreaks, riparian buffers,      |
|                                 |    | wetlands, ponds, and cover crops   |
|                                 |    | for that purpose to abate soil     |
|                                 |    | erosion VIA O.R.C.                 |
| Conservation Program Designated | 23 | Land in Federal or State           |
|                                 |    | Conservation Program (Ex: FSA      |
|                                 |    | Program).                          |
| Cropland                        |  2 | Land that is being 'Cropped', and  |
|                                 |    | not vacant of crop for more than 3 |
|                                 |    | years.                             |
| Cropland Default                |  2 | Land that is lumped into being     |
|                                 |    | considered as Cropland for lack of |
|                                 |    | a better use or explanation -      |
|                                 |    | usually areas between fields or    |
|                                 |    | long narrow spaces.                |
| Designated Forest Land          |  0 | Woodland that is in a Federal      |
|                                 |    | Program.                           |
| Ditch/Hydrography               |  5 | Land devoted to waterway, Ditch    |
|                                 |    | Buffer 50, Stream or River Buffer  |
|                                 |    | 60-70.                             |
| Homesite                        |  1 | Homesite = 1 Acre, Ag Parcels.     |
| Industrial                      |  7 | Land with Class I, Not Residual or |
|                                 |    | Homesite - To be broken down into  |
|                                 |    | Primary/Secondary Site.            |
| Lot - Apartment                 |  6 | Land with Class C/ or Land that is |
|                                 |    | used Commercially, Not Residual or |
|                                 |    | Homesite - To be broken down into  |
|                                 |    | Primary/Secondary Site.            |
| Lot - Commercial                |  6 | Land with Class C/ or Land that is |
|                                 |    | used Commercially, Not Residual or |
|                                 |    | Homesite - To be broken down into  |
|                                 |    | Primary/Secondary Site.            |
| Lot - Exempt                    |  6 | Land with Class C/ or Land that is |
|                                 |    | used Commercially, Not Residual or |
|                                 |    | Homesite - To be broken down into  |
|                                 |    | Primary/Secondary Site.            |
| Lot - Residential               |  1 | Homesite = 1 Acre, Ag Parcels.     |
| Pasture                         |  3 | Visible Land used for livestock -  |
|                                 |    | Determination to follow.           |
| Pond                            |  5 | Body of water, Recreational or     |
|                                 |    | Agricultural.                      |
| Primary Site                    |  6 | Primary Site, used in Industrial   |
|                                 |    | and Commercial Class parcels.      |
|                                 |    | Currently used for distinguishing  |
|                                 |    | multi use soil parcels.            |
| Primary Site                    |  6 | Primary Location for Main          |
|                                 |    | Concentration of Commercial or     |
|                                 |    | Industrial Involvement             |
|                                 |    | (Headquarters).                    |
| Rail Road                       |  9 | Property owned by Rail Company, no |
|                                 |    | other use.                         |
| Residential Homesite            |  1 | Parcels Under 5 Ac may have        |
|                                 |    | Homesite < 1 ac -- Residential Non |
|                                 |    | Ag Parcels.                        |
| Residual                        |  2 | Excess Land comprised of secondary |
|                                 |    | buildings, maintained yard, and or |
|                                 |    | drive.                             |
| Right Of Way                    |  9 | Road Right Of Way - Possibly be    |
|                                 |    | removed from Residential Parcels.  |
| Secondary Site                  |  7 | Secondary Location for Main        |
|                                 |    | Concentration of Commercial or     |
|                                 |    | Industrial Involvement (WorkSite). |
| Undeveloped Land                |  2 | Undeveloped Land that is not       |
|                                 |    | Residual that could otherwise be   |
|                                 |    | used for another purpose other     |
|                                 |    | than vacant Undeveloped.           |
| Wetland/ Wasteland              |  5 | Land that normally collects excess |
|                                 |    | water and is unable to yield Crop, |
|                                 |    | Land Unable to be used due to      |
|                                 |    | slope or another factor.           |
| Woodland                        |  4 | Land comprised of mainly Forest,   |
|                                 |    | not wind breaks.                   |
| Woodland- FMP                   |  4 | Woodland in a Forest Management    |
|                                 |    | Plan.                              |

### Figure 2 – New Layer Types, Codes, & Descriptions

General Land Cover Types:

| Land Cover        |	Code | Description                                    |
|-------------------|:----:|------------------------------------------------|
| Homesite          | 1    | The plot of land on which a house is or can be |
|                   |      | built. Homesite = 1 Acre. Parcels Under 5 Ac   |
|                   |      | may have Homesite < 1 Acre.                    |
| Tillable	        | 2    | Land that is visibly cleared and used for      |
|                   |      | agriculture or could be used for agriculture.  |
| Woodland	        | 4	   | Land comprised of mainly Forest, not wind      |
|                   |      | breaks.                                        |
| Ditch/Hydrography	| 5	   | Land comprised of primarily water features     |
|                   |      | (Ex: Ditch, River, Stream, Pond, Wetland,      |
|                   |      | Wasteland).                                    |
| Primary Site      | 6	   | Primary Location for Main Concentration of     |
|                   |      | Commercial or Industrial Involvement.          |
| Secondary Site    | 7	   | Secondary Location for Main Concentration of   |
|                   |      | Commercial or Industrial Involvement.          |
| Right of Way	    | 9	   | Road or Rail Right of Way.                     |
|                   |      |                                                |
| Residual          | 10   | Land that is not being used for agriculutural  |
|                   |      | means, and is part of a homesite above 2 acres |

Land Program Types:

| Land Cover                      |Code| Description                       |
| ------------------------------- |:--:| --------------------------------- |
| Designated Forest Land	        | 0	 | Woodland that is in a Federal     |
|                                 |    | Program.                          |
| Conservation Program Designated	| 23 | Land in Federal or State          |
|                                 |    | Conservation Program.             |
| Conservation Practice 25%	      | 24 | Practice use of grass waterways,  |
|                                 |    | terraces, diversions, filter      |
|                                 |    | strips, field borders, windbreaks,|
|                                 |    | riparian buffers, wetlands, ponds,|
|                                 |    | and cover crops for that purpose  |
|                                 |    | to abate soil erosion.(VIA O.R.C.)|
| Woodland – FMP	                | 4	 | Woodland in a Forest Management   |
|                                 |    | Plan.                             |



### Figure 3 – Feature Class Field Descriptions

Land_General Feature Class:

| Field Name     | Description                               |
| -------------- | ----------------------------------------- |
| CAMA	         | New generalized code.                     |
| Land Code	     | Code used for assessment in CAMA.         |
| Land Use Notes | General note about specific land feature. |

Land_Programs Feature Class:

| Field Name        | Description                                  |
| ----------------- | -------------------------------------------- |
| CAMA	            | New generalized code.                        |
| Land Code	        | Code used for assessment in CAMA.            |
| Land Use Notes	  | General note about specific land feature.    |
| LINK	            | Path to Document                             |
| FED_PROG	        | Federal Program Name                         |
| Conservation_Type	| Conservation Practice Type                   |
| Start_Date	      | Start Date of Program                        |
| End_Date	        | End Date of Program                          |
| Contract_Acreage	| Acreage directly stated in Program Contract  |
| Contract_Notes	  | Any additional notes                         |
| Field_Number	    | Contract’s individual Field Number           |
| Field_Acreage	    | Field Number’s individual acreage            |
| Practice_Number	  | Contracts’ individual Practice Number        |
| Contract_Number	  | Contract Number                              |
| Tract_Number	    | Contract’s individual Farm Tract Number      |
