# csfloat-api-query-map
## A query map showing how to combine weapon-skin parameters to request specific weapons and skins via the API.

The official csfloat documentation (https://docs.csfloat.com/#introduction) is focused mainly
on the parameters and you have to do your own digging. With this repo i wish to
save you some time.

## How it works
### CSFloat listings can be filtered using query parameters:

def_index — identifies the weapon
paint_index — identifies the skin (optional)
limit — number of listings per request (maximum: 50)
cursor — used for pagination

### Weapon + skin request example

To request listings for AK-47 | Redline:
def_index=7 (AK-47)
paint_index=282 (Redline)
https://csfloat.com/api/v1/listings?limit=50&def_index=7&paint_index=282

### Weapon-only request example

To request listings for a weapon regardless of skin, omit paint_index:
https://csfloat.com/api/v1/listings?limit=50&def_index=7

### Pagination

Each API response includes a cursor value at the bottom of the response payload.
To retrieve the next page of results, include this cursor in the subsequent request:
https://csfloat.com/api/v1/listings?limit=50&def_index=50&cursor=<cursor_value>
