# boston-condo-conversions


This repository contains code to find the condo conversions that took place in Boston from 2015 to 2024. In order to do so, we used [property assessment data](https://data.boston.gov/dataset/property-assessment) from Analyze Boston. 

## Code

All of the cleaning code can be found in `data_cleaning.ipynb`, which also contains comments to help substantiate some of the code. We counted condo conversions as addresses that only had 1 entry in a given year but multiple entries in the next year, with addresses being a combination of street number, name, and suffix. 

For each condo conversion, we kept 1 data entry and augmented it with the number of condo units (`num_condo_units`) and the year just prior to the conversion (`prior_year`) and the next year, after the conversion occurred (`post_year`). Data fields with the suffix `_prior` indicate data from `prior_year`, and data fields with the suffix `_post` indicate data from `post_year`.

## Data fields

There are some computed data fields:
* `ADDRESS`: The merged street number, name, and suffix
* `num_condo_units`: The number of condo units after conversion
* `prior_year`: The year just prior to the conversion, as described above (indicates the year that `_prior` data comes from)
* `post_year`: The year after `prior_year` (indicates the year that `_post` data comes from)

And some special cases:
* `YR_REMODEL`: For years in which the year remodeled column was named `YR_REMOD`, we renamed all of them to `YR_REMODEL` for greater consistency
* [REMOVED] `full_address`: This column was only present in 2015 and overlaps with the calculated `ADDRESS` column, so we removed it.

The other data fields correspond to either the `prior_year` or the `post_year`'s data fields; more information about them can be found on Analyze Boston's [website](https://data.boston.gov/dataset/property-assessment) (if a year doesn't have a data key, that means its data comes from the most recent prior data key PDF).
