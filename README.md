## Purpose of this repository

Recently I was looking for county-by-county results of the 2012 presidential
election, but was unable to find this data freely available in a usable format.
Although the data is available for free in several places on the Internet, it's
generally not provided in a consistent format, and cannot be used for mapping
or data analysis without a lot of tedious cleanup. Obtaining the data in a
consistent tabular format requires payment or institutional access.

Since others are presumably interested in this data as well, I decided to clean
up the 2012 data, along with the 2016 data as it is published, and make it
publicly available.

## Contents of this repository

### Election results

The original basis for this dataset is the [2012 election results table](https://www.theguardian.com/news/datablog/2012/nov/07/us-2012-election-county-results-download) provided by the *Guardian*. I reformatted the table so that every row uses the same
column order, and later replaced unofficial early returns with official results.
Since the table provides FIPS codes, you can load this spreadsheet into a GIS
application and join it to county shapefiles right away.

I've also been adding official results for the 2016 presidential election as
they become available. It always takes weeks after the election for counting to
be completed, and sometimes this leads people to draw erroneous conclusions –
you may remember, for example, that much of the commentary immediately after the
2016 election was premised on a large drop in turnout, which, as we now know,
did not happen. For this reason, I initially did not add unofficial results to
the table. At this point in time, most states that haven't certified have a very
small number of votes outstanding, so I've added those states as well, and noted
their unofficial status. These results will be updated as the final states'
certify.

State certification status is listed in `state_results_status.csv`

Results for Alaska have not been compiled, as I do not have access to borough-level
results.

The `maps` directory contains some SVG maps created in QGIS, which I will also
update.

### Population and turnout

I obtained voting-age population (VAP) figures for 2012 from the US Census
[Population Estimates Program (PEP)](https://www.census.gov/popest/index.html).
The 2016 PEP reports will not be released until sometime in 2017, so I
extrapolated 2016 VAP based on 2015 VAP and the 2014-2015 growth rate. In
counties with very small populations, this may greatly overstate changes in
population.

I have not been able to obtain year-by-year county-level data on the proportion
of noncitizens and disenfranchised felons. This is why I haven't included any
maps of absolute turnout levels; there are definitely enough people in those
groups to distort the results in some places. The turnout change maps are based
on the assumption that the proportion of voting-ineligible adults in each county
remained roughly constant from 2012 to 2016. This may not be true.

## Limitations of this data

* Vote totals for individual third-party and independent candidates are not
listed. Since each state had different third-party candidates on the ballot,
and tabulated the results differently, tracking them individually would have
taken additional time that I chose not to invest. However, the vote totals do
include all candidates.
* I had to enter some of this information manually or using ad hoc scripts. I
ran some basic sanity checks and corrected the errors I found, but I can't
guarantee that the data is completely free of mistakes.
* The *Guardian* data does not list individual boroughs in Alaska. Alaska
officially reports vote totals by state house district, not borough. I do not
yet know where to find vote totals by borough.

## Miscellaneous notes
* These FIPS codes are formatted without leading zeroes. US Census Department
shapefiles do use leading zeroes. Watch out for this when making maps.
* At least two counties changed in some way between 2012 and 2016. Shannon
County, SD changed its name to Oglala Lakota County in 2015, and its FIPS code
also changed. Bedford City, VA gave up its independent city status in 2013 and
became part of Bedford County. You may need to fix these manually if you're
using data from 2012.
* 2016 Nevada vote totals do not include "none of these candidates." I have not
yet checked to see whether the 2012 totals include these votes.
* 2016 NH totals do not include write-ins, as these have not been reported yet,
although the numbers are probably negligible anyway.
* Results for New England are officially reported by town, not county.

## Acknowledgements

Thanks to [Dave Wasserman](https://twitter.com/Redistrict) at the Cook Political
Report for [tracking up-to-date popular vote totals](https://docs.google.com/spreadsheets/d/133Eb4qQmOxNvtesw2hdVns073R68EZx4SfCnP4IGQf8/htmlview?sle=true) and state certifications. I also filled in some gaps in the
data using [Dave Leip's election atlas](http://uselectionatlas.org/).
