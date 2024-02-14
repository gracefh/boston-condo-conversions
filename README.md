# boston-condo-conversions

This repository contains code to find the condo conversions that took place in Boston from 2015 to 2024. In order to do so, we used [property assessment data](https://data.boston.gov/dataset/property-assessment) from Analyze Boston. 

As a note, because this data uses property assessment data spanning across a large set of years and the data formats changed across years, there will be columns that contain some null values, which can/should be filtered out for cetain kinds of analysis.

## Code

All of the cleaning code can be found in `data_cleaning.ipynb`, which also contains comments to help substantiate some of the code. We counted condo conversions as addresses that only had 1 entry in a given year but multiple entries in the next year, with addresses being a combination of street number, name, and suffix. 

For each condo conversion, we kept 1 data entry and augmented it with the number of condo units (`num_condo_units`) and the year just prior to the conversion (`prior_year`) and the next year, after the conversion occurred (`post_year`). Data fields with the suffix `_prior` indicate data from `prior_year`, and data fields with the suffix `_post` indicate data from `post_year`.

## Data fields

### Conversion Fields
* `ADDRESS`: The merged street number, name, and suffix
* `num_condo_units`: The number of condo units after conversion
* `prior_year`: The year just prior to the conversion, as described above (indicates the year that `_prior` data comes from)
* `post_year`: The year after `prior_year` (indicates the year that `_post` data comes from)

### Spatial fields
From [Analyze Boston's 2022 Parcel data](https://data.boston.gov/dataset/parcels-2022/resource/1b2cd4a0-c23a-4c11-b880-1255bb4d8734)
* `OBJECTID`
* `LOC_ID`
* `POLY_TYPE`
* `MAP_NO`
* `SOURCE`
* `PLAN_ID`
* `LAST_EDIT`
* `BND_CHK`
* `NO_MATCH`
* `TOWN_ID`
* `Shape_STArea__`	
* `Shape_STLength__`
* `ShapeSTArea`
* `ShapeSTLength`

### General Fields
The following data fields correspond to either the `prior_year` or the `post_year`'s data fields; more information about them can be found on Analyze Boston's [website](https://data.boston.gov/dataset/property-assessment) (if a year doesn't have a data key, that means its data comes from the most recent prior data key PDF).

* `BDRM_COND` - Bedroom condition
* `BED_RMS` - Total number of bedrooms in structure
* `BLDG_SEQ` - Building numbers of parcel
* `BLDG_TYPE` - Building type and style
* `BLDG_VALUE` - Total assessed building value
* `CD_FLOOR` - Number of floors of condominium unit
* `CITY` - City or Town of parcel
* `CM_ID` - 10-digit parcel number of Condo Main, which houses all related condo units
* `COM_UNITS` - Number of Commercial units
* `EXT_COND` - Exterior condition of parcel
* `FULL_BTH` - Total number of full baths in the structure
* `GIS_ID` - GIS id
* `GROSS_AREA` - Gross floor area
* `GROSS_TAX` - Tax bill amount based on total assessed value multiplied by the tax rateper thousand
* * `HEAT_TYP` - Structure heating type
* `HEAT_TYPE` - Structure heating type
* `HALF_BTH` - Total number of half baths in the structure
* `HLF_BTH` - Total number of half baths in the structure
* `INT_COND` - Interior Condition of parcel
* `LAND_SF` - Parcel's land area in square feet (legal area)
* `LAND_VALUE` - Total assessed land value
* `LIVING_AREA` - Living area square footage of the property
* `LU` - type of property (Land use)
* `LU_DESC` - Land use description
* `LUC` - Land use code
* `NUM_BLDGS` - Total buildings of parcel
* `NUM_FLOORS` - Number of floors
* `NUM_PARKING` - Number of parking spaces
* `OVERALL_COND` - Overall condition of parcel
* `PID` - Process ID (unique 10 digit number)
* `PTYPE` - State class code
* `R_EXT_CND` - Residential exterior condition (in older data)
* `R_INT_CND` - Residential Interior condition (in older data)
* `R_OVRALL_CND` - Residential overall condition (in older data)
* `RC_UNITS` - Number of Residential/Commercial Units in a condominium building
* `RES_FLOOR` - Number of floors (for residential units)
* `RES_UNITS` - Number of Residential units
* `S_EXT_CND` - Condo main exterior condition
* `S_NUM_BLDG` - Number of buildings in condo main    
* `ST_NAME` - Street name
* `ST_NAME_SUF` - Street name suffix
* `ST_NUM` - Street number
* `STRUCTURE_CLASS` - Structural classification of building
* `TOTAL_VALUE` - Total assessed value for property
* `TT_RMS` - Total number of rooms in the structure
* `UNIT_NUM` - Specific unit number within a housing complex
* `YR_BUILT` - Year property was built
* `YR_REMODEL` - Year property was last remodeled
* `ZIPCODE` - Zip code

