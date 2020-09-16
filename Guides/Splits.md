# Property Splits & Combinations

When a parcel is split or combined, the land type acreage breakdown must be calculated for each parcel. Parcel splits are started by the tax map office, who will approve or deny the split/combine, who will then send the parcel split or combination to the Auditor's office. To quickly do this, the Auditor's Office partners with a 3rd Party Vendor, [Bruce Harris](http://www.bruceharris.com/). Bruce Harris has a ArcGIS Extension called the "Farmland Calculator", which performs the analysis on any selected parcel.

Currently, new parcels are provided to the Auditor's office by the Tax map office roughly once a month. If splits/combines need to be calculated for CAUV and is not in the current parcel layer being used from the tax map office, the split/combine can be done manually by the current GIS person. All that needs to be done is to edit the current parcel layer in ArcGIS and to either process the split based on what is shown in the survey map, or to combine the parcels using the 'merge' tool in the editor toolbar. You will then need to change the deeded acres to what the new property record card states the new acreage is for the new parcel parcel. You will also need to change the PIN for the parcel to the new PIN provided by the Tax Map office for the new parcel.

*Note: The extension is currently only available for ArcGIS Desktop.*

Alex Rodd wrote a detailed set of instructions (with screenshots), to show users how to use the tool. The instructions are located here;
```
B:\GIS Documents\Welcome\Alex's Notes\Process in order to run a CAUV Calc.docx
```

*Note: I updated Alex's instructions since the land use layer's structure was changed slightly. You can read more about that [here](./06_Land_Use.md)*
