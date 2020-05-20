# 2020 Land Update
A mass overhaul of Tax Values can occur in 2020. This opportunity will allow the
Auditor to perform a large update of the Land Use & Cover GIS layer. The
original land use dataset was developed by analyzing each parcel and referencing
aerial imagery and other more generalized datasets. Because the individual
components were not mapped separately, revising and updating this information
will be a manual process.

Looking forward, I have outlined a few ways to both update the dataset in 2020,
as well as develop a system that is easy to update in the future. Generally, I
consider the new system a "deconstructed" GIS layer that is made up of
manageable and independent components. The layers can then be quickly combined
or "reconstructed" for tax valuations. The following is a breakdown of the
"deconstructed" land dataset.

```
|- Land_Combined
|   |- Land_Programs
|          |- CRP
|          |- CONP
|          |- WRP
|          |- FMP
|          |- Designated Forest Land
|   |- Land_General
|          |- ROW
|          |- HOME
|          |- DITCH
|             |- Ditches
|             |- Hydrography
|          |- WOOD
|          |- CROP
|

```
In this system, all the independent components are combined to form more general
layers that are combined again to produce the final layer. For example, Ditches
could be updated all at one time, and then recombined with Hydrography,
recombined to the Land_General layer, and then recombined to the final
Land_Combined layer. This process can be performed again and again without
without having to manually re-digitize each affected feature in the final layer.

## Ditch/Hydrography
Ditches and Hydrography are currently the same land code since they are valued
the same, however, these were originally mapped from different sources. Ditches
are managed by the Seneca County Engineer, and he provides the Auditor a Ditch
GIS Layer. Hydrography information is maintained at the federal level by the
USGS. The USGS Hydrography Dataset is mapped at a low resolution, meaning many
of the smaller creeks are spatially inaccurate, if mapped at all.

Due to the precise nature of Tax Valuations, the original development of the
land dataset accurately mapped many of the smaller creeks and rivers, however,
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
Homesites are representations of building outlines and non-agricultural land
(a.k.a. residential grass yard, driveway, etc.). Homesites are restricted to 1
acre, regardless if it is larger or smaller than 1 acre. A comprehensive review
of Homesites should be performed, to ensure the GIS polygons are 1 acre in size,
and if any homesites should be added or removed.

The land use layer has not taken into account any new constructions or
deconstruction completed permits in the past year. Homesites have been mapped
when a property is reviewed after a parcel split or combination, but not
according to completed permits. Permits completed in the past year should be
individually reviewed and then homesites updated in the GIS layer.

Pictometry will be performing a flight in 2020, and will provide us a large
dataset containing changes in building outlines compared to 2018. In combination
with completed permits, these should be individually reviewed and updated in the
GIS layer.

## Bruce Harris Land Use Audit
Bruce Harris has been contracted to perform an audit of our Land Use info so
that agricultural land information matches market land information. Market and
land information have similar, yet differing land codes, and their analysis will
identify areas that in the GIS layer that do not match what is in our IASWorld
database. The land use GIS layer should be updated to correct any differences
Bruce Harris identifies.
