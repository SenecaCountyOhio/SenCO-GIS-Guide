One task that you will have to perform from time to time is doing zoning updates for townships within Seneca county

These are used to show what a parcel of land is being used for at a glance. These updates are few and far between and most of the files
associated with them are all works in progress. 

There are currently 3 townships that have a Zoning file associated with them, Hopewell, Clinton, and Pleasant Townships. All of the parcels are considered to be "Agricultural" until we recieve notice that it is no longer "Agricultural". This is to save time instead of having to dig through records to find out what each and every parcel of land in Seneca County is being used for.

To produce one of the zoning maps from scratch, you will need to pull in both the parcel layer for Seneca County and the Township layer
that is in the Seneca County GeoLibrary.

I then did a spatial join of both layers so that there was a layer that gave each parcel data on which Township it was located in. You can remove the other layers once you have finished the spatial join. 

You might have to go into the attributes table for some of the parcels to get them in the proper Township as some of them might fall within a city's limits and we will need to make sure that parcel in within a Township if the zoning for the parcel is being amended. 

After you run the spatial join and confirmed that all of the parcels you are updating are in the Township you need them to be in, you will need to remove all of the parcels that are in Townships that you are not doing the update for. 

To do this, click "Select By Attributes" and choose your zoning layer as the layer you want to search in. You will want to make a new SQL expression to select all of the parcels in Townships you are not working in, so when I created the Hopewell Township Zoning map, I did "Name <> 'Hopewell Township'", the "<>" tells ARCGIS Pro to select anything that doesn't have Hopewell Township in the "Name" column of the attributes table. When creating a new Zoning map, the expression will be "Name <> 'Township Name'".

Now that all the parcels outside of the Township that you're update the zoning for are selected, you can delete all of the unneeded parcels. Now you need to add a column to the attributes table for the Zoning purpose. 

Once you have that created, then you will need to do "Find and Replace" in the attributes table for the new column and replace all of the "< Null >" fields with "Agricultural". 
  
Now you can select by attribute for the Parcel(s) you need to change and style them to show the different Zonings for the parcels in the township
