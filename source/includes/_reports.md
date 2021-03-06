# Reports

## Customs code info

Returns the info for given customs code mapping for given country. If no hs8 parameter is given, all hs8 codes valid for given country are returned.

```coffee
$.ajax
  dataType: "json"
  type: "get"
  data:
    hs8: "01011919"
    lang: "NO"
  url: "/api/reports/customs_code_info"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON array structured like this:

```json
{
  "hs8": "01011919",
  "hs6_text": "Levende dyr og animalske produkter",
  "hs8_text": "Hester, over 1/2 år, levende, ikke vallaker, ikke til avl",
  "year": null
}
```




### Parmeters

Param | Format | Description
--------- | ------- | ------- 
country_code | 2 capital letters | iso2 country code
hs8 | 8 digits | (optional) customs code valid in country given in country_code

> Parameters validation errors will be reported in 422 response JSON like:

```json
{
    errors: {
        hs8: [
            "is the wrong length (should be 8 characters)"
            "is not a number"
        ]
        country_code: [
           "can't be blank"
           "is the wrong length (should be 2 characters)"
           " is not a valid country code"
        ]
    }
}
```

### HTTP Response Codes

Response | Meaning
--------- | -------
200 | ok
422 | Unprocessable entity

### HTTP Request

`GET api/reports/customs_code_info`

## Hs6

Returns the list of all hs6 codes with description.

```coffee
$.ajax
  dataType: "json"
  type: "get"
  url: "/api/reports/hs6"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON array structured like this:

```json
[
  {
    "hs6": "000000",
    "hs6_text": "Levende dyr og animalske produkter"
  },
  {
    "hs6": "010110",
    "hs6_text": "Levende dyr og animalske produkter"
  },
  {
    "hs6": "010111",
    "hs6_text": "Levende dyr og animalske produkter"
  },
  (...)
]
```

### HTTP Request

`GET api/reports/hs6`