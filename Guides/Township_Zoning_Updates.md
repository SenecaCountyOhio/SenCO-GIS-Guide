One task that you will have to perform from time to time is doing zoning updates for townships within Seneca county. This is something that will be done too often, but will have to be done by the GIS person.

These are used to show what a parcel of land is being used for at a glance. These updates are few and far between and most of the files
associated with them are all works in progress. 

Map files have been created for each township in Seneca County and can be found in the "Projects" folder in the B:\ drive. All of the parcels are considered to be "Agricultural" until we recieve notice that it is no longer "Agricultural". This is to save time instead of having to do an audit of all the parcels in a township whenever we get a notification that a parcel is having its zoning type changed.

To produce one of the zoning maps from scratch, you will need to pull in both the parcel layer for Seneca County and the Township layer
that is in the Seneca County GeoLibrary. You won't need to do this since all of the Zoning maps are already made, but just in case they get deleted, I'm going to outline the process that I used below.

I then did a spatial join of both layers so that there was a layer that gave each parcel data on which Township it was located in. You can remove the other layers once you have finished the spatial join. 

You might have to go into the attributes table for some of the parcels to get them in the proper Township as some of them might fall within a city's limits and we will need to make sure that parcel in within a Township if the zoning for the parcel is being amended. 

After you run the spatial join and confirmed that all of the parcels you are updating are in the Township you need them to be in, you will need to remove all of the parcels that are in Townships that you are not doing the update for. 

To do this, click "Select By Attributes" and choose your zoning layer as the layer you want to search in. You will want to make a new SQL expression to select all of the parcels in Townships you are not working in, so when I created the Hopewell Township Zoning map, I did "Name <> 'Hopewell Township'", the "<>" told ARCGIS Pro to select anything that didn't have Hopewell Township in the "Name" column of the attributes table. When creating a new Zoning map, the expression will be "Name <> 'Township Name'".

Now that all the parcels outside of the Township that you're update the zoning for are selected, you can delete all of the unneeded parcels. Now you need to add a column to the attributes table for the Zoning purpose. 

Once you have that created, then you will need to do "Find and Replace" in the attributes table for the new column and replace all of the "< Null >" (without the spaces) fields with "Agricultural". Before you can add a column to the table, you have to go to the Edit tab and save your edits.
  
Now you can select by attribute for the Parcel(s) you need to change and style them to show the different Zonings for the parcels in the township

Note: Double check to make sure that the zoning changes were approved before making changes to the parcels. It's easy enough to change them back, but for the sake of efficiency, it's best to do.
