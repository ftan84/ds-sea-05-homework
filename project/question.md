Given the following features:
  - City and State
  - Zestimate (Zillow proprietary score on property value)
  - Last updated
  - 30-day change (in $)
  - Valuation range (high) (in $)
  - Valuation range (low) (in $)
  - Percentile (Valuation percentile)
  - FIPS county code (factor variable)
    - The FIPS county code is a five-digit Federal Information Processing Standard (FIPS)
      code (FIPS 6-4) which uniquely identifies counties and county equivalents in the
      United States, certain U.S. possessions, and certain freely associated states.
      The first two digits are the FIPS state code and the last three are the county code within the state or possession.
  - Usecode (factor variable)
    - Unknown
    - SingleFamily
    - Duplex
    - Triplex
    - Quadruplex
    - Condominium
    - Cooperative
    - Mobile
    - MultiFamily2To4
    - MultiFamily5Plus
    - Timeshare
    - Miscellaneous
    - VacantResidentialLand
  - Tax assessment year
  - Tax assessment ($)
  - Year built
  - Lot Size (sq ft)
  - Square footage
  - # of bathrooms
  - # of bedrooms
  - Last sold date (likely convert to epoch time for numerical value)
and the "Last Sold Price" as a response variable, I will try to predict a sales price.

Data was collected through Zillow's public API (http://www.zillow.com/howto/api/APIOverview.htm) over a span of
one week due to a rate limit of 1000 calls per day. This project utilizes two endpoints: GetDeepComps and GetDeepSearchResults.
Using these two endpoints, the application collects data in two steps:
  1. Collect list of comps given a property
    - The API is able to return a list of zpid's (Zillow property ID. Max 25 per call). We must first start with a
      "seed" property address. Once we have a seed, the application will "recursively" collect comps (not true recursion
      in consideration of memory expense).
  2. Collect property details
    - Once zpid's are known, make calls on collected zpid's to collect property details as described above.
    
I have close to 7000 zpid's collected with about 2000 populated with property details thus far. Considering the API rate limit,
I think 2000 observations will suffice for the purposes of this project. The data is currently stored in the form of a SQLite file.
