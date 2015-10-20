# Packaging factors

## factors by country

Returns the list of packaging codes and respective packaging factors for given country. 
Both BigML calculated and invariant factors are returned.

```coffee
$.ajax
  dataType: "json"
  type: "get"
  data:
    country_code: "NO"
  url: "/api/packaging_factors/by_country"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON array structured like this:

```json
[ 
  { "hs8" : "12345678",
    "code" : "T122",
    "last_updated_at" : "2015-04-11",
    "material" : { 
        "id" : 1,
        "name" : "Plastemballasje"
      },
    "packaging_factor" : 0.134077523498238144,
    "type" : { 
        "id" : 1,
        "kind" : "T",
        "name" : "Folie"
      },
    "invariant": false
  },
  { "hs8" : "12345678",
    "code" : "T422",
    "last_updated_at" : "2015-06-05",
    "material" : { 
        "id" : 5,
        "name" : "Bølgepapp og massivpapp"
      },
    "packaging_factor" : 0.5392959336048203,
    "type" : { 
        "id" : 8,
        "kind" : "T",
        "name" : "Bølgepapp"
      },
    "invariant": true
  },
  { "hs8" : "12345678",
    "code" : "T0",
    "last_updated_at" : "2015-05-11",
    "material" : { 
        "id" : 12,
        "name" : "unknown"
      },
    "packaging_factor" : 0.1410425117764894,
    "type" : { 
        "id" : 27,
        "kind" : "T",
        "name" : "Transportpallet"
      },
    "invariant": false
  },
  { "hs8" : "12345678",
    "code" : "H124",
    "last_updated_at" : "2015-03-14",
    "material" : { 
        "id" : 1,
        "name" : "Plastemballasje"
      },
    "packaging_factor" : 0.8907183597528011,
    "type" : { 
        "id" : 2,
        "kind" : "H",
        "name" : "Flasker/kanner/..."
      },
    "invariant": false
  },
  { "hs8" : "12345678",
    "code" : "H422",
    "last_updated_at" : "2015-03-30",
    "material" : { 
        "id" : 5,
        "name" : "Bølgepapp og massivpapp"
      },
    "packaging_factor" : 0.9506501728182712,
    "type" : { 
        "id" : 8,
        "kind" : "H",
        "name" : "Bølgepapp"
      },
    "invariant": false
  }
]
```


### Parmeters

Param | Format | Description
--------- | ------- | ------- 
country_code | 2 capital letters | iso2 country code

> Parameters validation errors will be reported in 422 response JSON like:

```json
{
    errors: {
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
200 | ok.
422 | Unprocessable entity

### HTTP Request

`GET api/packaging_factors/by_country`


## factors by vendor

Returns the list of products with packaging codes and respective packaging factors for given vendor. 
The vendor is identified by organization number.

```coffee
$.ajax
  dataType: "json"
  type: "get"
  data:
    country_code: "NO",
    org_nr: 123456789
  url: "/api/packaging_factors/by_vendor"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON array structured like this:

```json
[
  {
    "product_code": "601202",
    "name": "84186101_Wilfa_601202_2800.0_3509.91",
    "ean": "7044876012029",
    "last_updated_at": "2015-09-22T14:50:11.000+02:00",
    "packagings": [
      {
        "code": "H122",
        "packaging_factor": "0.002344792503819736078902444",
        "type": {
          "id": 1,
          "name": "Folie",
          "kind": "H"
        },
        "material": {
          "id": 1,
          "name": "Plastemballasje"
        }
      },
      {
        "code": "H422",
        "packaging_factor": "0.198617885563530086596022",
        "type": {
          "id": 8,
          "name": "Bølgepapp",
          "kind": "H"
        },
        "material": {
          "id": 5,
          "name": "Bølgepapp og massivpapp"
        }
      },
      {
        "code": "T122",
        "packaging_factor": "0.001295036307466578184511241",
        "type": {
          "id": 1,
          "name": "Folie",
          "kind": "T"
        },
        "material": {
          "id": 1,
          "name": "Plastemballasje"
        }
      }
    ]
  },
  {
    "product_code": "602153",
    "name": "85167100_Wilfa_602153_3740.0_4814.23",
    "ean": "7044876021533",
    "last_updated_at": "2015-09-22T14:50:11.000+02:00",
    "packagings": [
      {
        "code": "H122",
        "packaging_factor": "0.005982269218318049751270675",
        "type": {
          "id": 1,
          "name": "Folie",
          "kind": "H"
        },
        "material": {
          "id": 1,
          "name": "Plastemballasje"
        }
      },
      {
        "code": "H422",
        "packaging_factor": "0.216288112717564322361392462",
        "type": {
          "id": 8,
          "name": "Bølgepapp",
          "kind": "H"
        },
        "material": {
          "id": 5,
          "name": "Bølgepapp og massivpapp"
        }
      },
      {
        "code": "T122",
        "packaging_factor": "0.000865490407537556020936727",
        "type": {
          "id": 1,
          "name": "Folie",
          "kind": "T"
        },
        "material": {
          "id": 1,
          "name": "Plastemballasje"
        }
      }
    ]
  }
]
```


### Parmeters

Param | Format | Description
--------- | ------- | ------- 
country_code | 2 capital letters | iso2 country code
org_nr | 9 digits | organization number (currently only in Norwegian org_nr format)

> Parameters validation errors will be reported in 422 response JSON like:

```json
{
    errors: {
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
200 | ok.
422 | Unprocessable entity

### HTTP Request

`GET api/packaging_factors/by_vendor`

## Factors last updated 

Returns the datetime (iso8601) of the last uploaded file with packaging factors.

```coffee
$.ajax
  dataType: "json"
  type: "get"
  data:
    country_code: "NO"
  url: "/api/packaging_factors/last_updated"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON array structured like this:

```json
{
  "last_updated": "2015-10-16T15:19:15.000+02:00"
}
```


### Parmeters

Param | Format | Description
--------- | ------- | ------- 
country_code | 2 capital letters | iso2 country code

> Parameters validation errors will be reported in 422 response JSON like:

```json
{
    errors: {
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
200 | ok.
422 | Unprocessable entity

### HTTP Request

`GET api/packaging_factors/last_updated`