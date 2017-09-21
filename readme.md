jq-bls
---
The U.S. Bureau of Labor Statistics publishes all sorts of 
time series data about the economy accessible as JSON.

Jq is functional, stream based JSON manipulator using 
query strings by Stephen Dolan and is amazing.

Oveview
---
Observe: you will need to have curl and jq installed.
Orientate: get to BLS Data finder page
Decide: pick a series
Act: pipe curl into jq and play around with jq filter strings

Example: Testing the pipes
---
Lets say we want the series named :All items in U.S. city average, 
all urban consumers, not seasonally adjusted.  We need the 
series ID: CUUR0000SA0

curl https://api.bls.gov/publicAPI/v2/timeseries/data/CUUR0000SA0 \
 | jq .

Example: Grabing JSON for later (bcz of bls.gov data limits)
---
curl https://api.bls.gov/publicAPI/v2/timeseries/data/CUUR0000SA0 > \
CUUR000000SAO.json


Example: using JSON file just like a curl stream 
---
cat CUUR000000SAO.json | jq .

Example: Filter data for x/y graph 
---
cat CUUR0000SA0.json | jq '.Results.series[].data[] | {year, period, value}'


Links
---
[Data Tools Entry Point at BLS](https://www.bls.gov/data/)
[Stephen Dolan](http://stedolan.net/)
[CPI Overview](https://www.bls.gov/cpi/overview.htm)
