# 2020 Land Update
A mass overhaul of Tax Values can occur in 2020. This opportunity will allow the
Auditor to perform a large update of the Land Use & Cover GIS layer. The
original land use dataset was developed by analyzing each parcel and referencing
aerial imagery and other more generalized datasets. Because the individual
components were not mapped separately, revising and mass updating this
information will be a manual process. Looking forward, I have outlined a few
ways to both update the dataset in 2020, as well as develop a system to make the
information easily updatable in the future. Generally, I consider the new system
a "deconstructed" GIS layer, that is made up of many manageable components that
are independent of one another, but can also be quickly combined or
"reconstructed" for tax valuations. The following is an outline of the different
aspects of the GIS layer that should be updated.

## Ditch/Hydrography
Ditches and Hydrography are currently the same land code since they are valued
the same, however, these were originally mapped from different sources. Ditches
are managed by the Seneca County Engineer, and he provides the Auditor a Ditch
GIS Layer. Hydrography information is maintained at the federal level by the
USGS. The USGS Hydrography Dataset is mapped at a low resolution, meaning many
of the smaller creeks are spatially inaccurate, if mapped at all.

Due to the precise nature of Tax Valuations, the original land dataset
accurately represented many of the smaller creeks and rivers, however,
hydrographic line data was never created, and so it is difficult to update this
information to reflect changes in the USGS dataset.

Ditches and Hydrographic Lines should be edited and mapped separately, to then
be merged, assigned a buffer, and then added to the general land cover dataset.
ArcGIS can perform these geoprocessing functions relatively quickly, and will
save time compared to manually editing and reviewing each polygon feature.

I recommend the following procedures to update ditch/hydrography;
- Query then export all Ditch/Hydrography polygons in the land use layer.
- Review each ditch/hydrography polygons in land use layer to replace with
  surrounding land use types.
- Use the Ditch layer to select by location all Ditch Polygons in the
  Ditch/Hydrography Polygons.
- Use the USGS Hydrographic Line dataset to review all Hydrography Polygons.
- Using Aerial Imagery digitize any hydrography features not in the USGS dataset.
- Merge the Ditch and Hydrographic Line datasets
- Assign a buffer to the merged dataset.
- Perform an "update" geoprocess on the land layer without ditch/hydrography.

After these steps the following will have been produced;
- A high resolution and accurate Hydrographic Line dataset.
- A general land layer without ditch/hydrographic attributes.
- A dataset structure meant to be easily updated in the future.

## Homesites
Homesites are mappe
New Construction & Deconstruction Permits

Building Outline Shapefile from Pictometry

## Bruce Harris Land Use Audit

Identify areas that need to be updated

## Pictometry Change-finder

Identify areas that need to be udpated
