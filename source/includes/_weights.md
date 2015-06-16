# Weighted products

## Show product

Returns full information about the registered product

```coffee
$.ajax
  dataType: "json"
  type: "get"
  url: "/api/weights/5"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON structured like this:

```json
{
"id":5,
"name":"Test",
"description":"Sth",
"hs_mapping":{
    "id":2,
    "hs8":"00000031",
    "hs8_text":"Proviant",
    "hs6_text":"Levende dyr og animalske produkter"
    },
"ean":"1234567891233",
"product_code":"1234",
"trademark":"Coke",
"weight_source_type":{
    "id":1,
    "type":"Own weighing",
    "description":"Representatives of the PRO performed the weighing.",
    "data_quality":"Very good"
    },
"weight_source_company_id":1,
"weight_source_company":{
    "id":1,
    "org_no":"984170661",
    "name":"Aveiro AS",
    "description":"Test",
    "country":"Norway",
    "pro":{
        "id":1,
        "name":"Grønt Punkt Norge",
        "description":null
        }
    },
"data_reliability":1,
"product_importance":"0.0",
"is_gross":true,
"approved":false,
"created_date":"2015-04-10T00:04:46.000+02:00",
"updated_date":"2015-04-10T00:04:46.000+02:00",
"created_by_user":"Greg",
"updated_by_user":"Prakriti",
"weight_data":[
    {
    "id":1,
    "weight":"2.0",
    "packaging_type":{
        "id":8,
        "name":"Bølgepapp",
        "description":"Bølgepapp og massivpapp",
        "presentation_order":70,
        "material":{
            "id":5,
            "name":"Bølgepapp og massivpapp",
            "descrption":"Bølgepapp og massivpapp",
            "presentation_order":50
            }
        }
    }
]
}

```




### HTTP Response Codes

Response | Meaning
--------- | -------
200 | ok.
422 | Unprocessable entity

### HTTP Request

`GET api/weights/:ID`

## Packaging factors

Returns the list of packaging codes and respective packaging factors for given country and hs8 code.

```coffee
$.ajax
  dataType: "json"
  type: "get"
  data:
    hs8: "01011919"
    lang: "NO"
  url: "/api/weights/packaging_factors"
  success: (data, status, jqXHR) ->
    redirectSomewhere(status)
```

> The above command returns JSON array structured like this:

```json
[ 
  { "code" : "T122",
    "last_updated_at" : "2015-04-11",
    "material" : { "id" : 1,
        "name" : "Plastemballasje"
      },
    "packaging_factor" : 0.13077523498238144,
    "type" : { "id" : 1,
        "kind" : "T",
        "name" : "Folie"
      }
  },
  { "code" : "T422",
    "last_updated_at" : "2015-06-05",
    "material" : { "id" : 5,
        "name" : "Bølgepapp og massivpapp"
      },
    "packaging_factor" : 0.5392959336048203,
    "type" : { "id" : 8,
        "kind" : "T",
        "name" : "Bølgepapp"
      }
  },
  { "code" : "T0",
    "last_updated_at" : "2015-05-11",
    "material" : { "id" : 12,
        "name" : "unknown"
      },
    "packaging_factor" : 0.1410425117764894,
    "type" : { "id" : 27,
        "kind" : "T",
        "name" : "Transportpallet"
      }
  },
  { "code" : "H124",
    "last_updated_at" : "2015-03-14",
    "material" : { "id" : 1,
        "name" : "Plastemballasje"
      },
    "packaging_factor" : 0.8907183597528011,
    "type" : { "id" : 2,
        "kind" : "H",
        "name" : "Flasker/kanner/..."
      }
  },
  { "code" : "H422",
    "last_updated_at" : "2015-03-30",
    "material" : { "id" : 5,
        "name" : "Bølgepapp og massivpapp"
      },
    "packaging_factor" : 0.9506501728182712,
    "type" : { "id" : 8,
        "kind" : "H",
        "name" : "Bølgepapp"
      }
  }
]
```




### Parmeters

Param | Format | Description
--------- | ------- | ------- 
country_code | 2 capital letters | iso2 country code
hs8 | 8 digits | customs code valid in country given in country_code

> Parameters validation errors will be reported in 422 response JSON like:

```json
{
    errors: {
        hs8: [
            "can't be blank"
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

`GET api/weights/packaging_factors`