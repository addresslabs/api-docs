# POST /parsed-address

    /parsed-address

Parse provided address into separate components and format it. This endpoint is provided in case you prefer not to pass address data through a query string using GET method - instead you can POST unparsed address as JSON.

## Request

    {
        "address": "1600 pennsylvania ave north-west washington dc 20500"
    }

## Example

```shell
curl -H 'Content-Type: application/json' \
  -d '{ "address": "1600 pennsylvania ave north-west washington dc 20500" }' \
  http://api.addresslabs.com/v1/parsed-address
```
The above request would return following response:

    {
        "number": "1600",
        "street": "Pennsylvania",
        "street_suffix": "Ave",
        "street_post_direction": "NW",
        "city": "Washington",
        "state": "DC",
        "state_fips": "11",
        "zip": "20500",
        "intersection": false,
        "delivery": {
            "address_line": "1600 Pennsylvania Ave NW",
            "last_line": "Washington DC  20500"
        },
        "input": "1600 pennsylvania ave north-west washington dc 20500"
    }


## Response JSON

Property                  | Description
:-------------------------|:--------------------------------------
`number`                  | Street number
`street`                  | Street name
`street_suffix`           | Street suffix, for example "St", "Rt", "Ave", etc.
`unit`                    | Unit
`unit_designator`         | Unit designator, for example "Apt", "Ste", "Ut", etc.
`street_pre_direction`    | Directional designator appearing before street name, eg. "N" in "1 N Main St"
`street_post_direction`   | Directional designator appearing after street name, eg. "NW" in "1600 Pennsylvania Ave NW"
`street2`                 | 2nd street name, if address an intersection of 2 streets
`street2_suffix`          | Suffix of 2nd street
`street2_pre_direction`   | Directional designator appearing before 2nd street name
`street2_post_direction`  | Directional designator appearing after 2nd street name
`city`                    | City
`state`                   | State abbreviation
`state_fips`              | [State FIPS code](http://en.wikipedia.org/wiki/Federal_Information_Processing_Standard_state_code)
`zip`                     | 5 digit ZIP code
`zip4`                    | Plus-four ZIP digits
`intersection`            | Boolean, indicating whether the address is an intersection or not. `true` or `false`
`delivery.address_line`   | 1st line of the address formatted following USPS guidelines
`delivery.last_line`      | 2nd line of the address formatted following USPS guidelines
`input`                   | Input address string