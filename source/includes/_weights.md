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