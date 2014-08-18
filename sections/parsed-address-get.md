# GET /parsed-address

    /parsed-address

Parse provided address into separate components and format it.


## Paramaters

Parameter | Description
:---------|:------------------------
address   | Unparsed address string


## Example

```shell
curl -H 'Content-Type: application/json' \
  http://api.addresslabs.com/v1/parsed-address?address=1+main+st+ste+6+boston+ma+02111
```
The above request would return following response:

    {
        "number": "1",
        "street": "Main",
        "street_suffix": "St",
        "unit": "6",
        "unit_designator": "Ste",
        "city": "Boston",
        "state": "MA",
        "state_fips": "25",
        "zip": "02111",
        "intersection": false,
        "delivery": {
            "address_line": "1 Main St Ste 6",
            "last_line": "Boston MA  02111"
        },
        "input": "1 main st ste 6 boston ma 02111"
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
