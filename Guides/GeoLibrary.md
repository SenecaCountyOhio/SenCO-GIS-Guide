# Seneca County GeoLibrary

## Purpose
The primary goal of the Seneca County GeoLibrary is to better structure and
document the various Geographic Information relevant to the county. The
GeoLibrary can serve as the main GIS data and map storage repository for the
county.

A secondary goal is to make all the information in the GeoLibrary
available to the public and other departments through ArcGIS Hub.


## Schema
```
├───Primary Theme
│   ├───Data
│   │   └───Secondary Theme
│   │       └───Geographic Area
│   └───Maps
│       └───Secondary Theme
│           └───Geographic Area
```

## Primary Themes
The most general descriptive name for the type of Geographic Information.
The primary themes include;

- Administrative Boundaries
- Emergency Management
- Environment
- Imagery
- Transportation
- Land & Tax Records
- Utilities
- Planning & Development

## Secondary Themes
A more specific descriptive name for the type of Geographic Information.
**There should be no Tertiary Themes.**

```
Example: Emergency Management is broken down into Fire, EMS, Police, EMA.
```




## Geographic Area
Geographic area the information is relative to. For example, Seneca County,
City of Tiffin, State of Ohio, USA, etc. Only included if Secondary Theme has
multiple areas of reference.


## Current Folder structure (05/11/2020):
```
│
├───Administrative Boundaries
│   ├───Election Districts
│   ├───Municipal_Boundaries
│   ├───School_Districts
│   └───Zip Codes
│
├───Emergency Management
│   ├───EMA
│   ├───EMS
│   ├───Fire
│   └───Police
|
├───Environment
│   ├───Ditch
│   ├───Elevation
│   ├───Geology
│   └───Hydrography
|
├───Imagery
|   └───Aerial Imagery
│
├───Land & Tax Records
│   ├───Addresses
│   ├───Buildings
│   ├───Land Use
│   ├───Neighborhood
│   ├───Parcels
│   └───Tax Districts
│
├───Planning & Development
│   ├───Community Reinvestment Areas
│   ├───Landmarks
│   └───Zoning
│       ├───Adams Township
|       ├───Bloom Township
|       ├───City of Tiffin
│       ├───Clinton Township
|       ├───Eden Township
|       ├───Hopewell Township
|       ├───Jackson Township
|       ├───Liberty Township
|       ├───Loudon Township
│       ├───Pleasant Township
|       ├───Reed Township
|       ├───Scipio Township
|       ├───Seneca Township
|       └───Thompson Township
|       
│
├───Transportation
│   ├───Data
│   │   ├───Rail_Roads
│   │   ├───Roads
│   │   ├───Sidewalks
│   │   └───Trails
│   └───Maps
│       └───Highway Map
│
└───Utilities
    └───Sewer
```
