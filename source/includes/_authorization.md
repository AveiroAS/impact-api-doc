# Authorization

Authorization is performed using Devise (server side) and ng-token-auth (client side) and is token based. User authenticates using email and password. 
The backend utilizes token rotation for every request to secure API calls.

## Login

### HTTP Request

`POST api/auth/sign_in`

### Parmeters

Param | Format | Description
--------- | ------- | ------- 
email | string | email address of user
password | string | user password

### HTTP Response Headers

Header | Value | Meaning
--------- | ------- | -------
access-token | wwwww | one time access token
token-type   | Bearer
client       | xxxxx | This enables the use of multiple simultaneous sessions on different clients.
expiry       | 12334567 | The date at which the current session will expire. 
uid          | test@user.pl | A unique value that is used to identify the user.

> The successfull login returns user object that is available in $rootScope.currentUser

```json
{  
   "id":5,
   "provider":"email",
   "uid":"greg@aveiro.no",
   "name":"Greg",
   "surname":"Brzezinka",
   "email":"greg@aveiro.no",
   "company_id":1,
   "get_roles":[  
      "admin",
      "weigher"
   ],
   "company":{  
      "id":1,
      "org_no":"984170661",
      "name":"Aveiro AS",
      "description":"Test",
      "pro_id":1,
      "country_id":160,
      "pro":{  
         "id":1,
         "name":"Grønt Punkt Norge",
         "description":null
      },
      "country":{  
         "id":160,
         "name":"Norway",
         "iso2":"NO",
         "iso3":"NOR",
         "locale":"EN"
      }
   },
   "signedIn":true,
   "configName":"default"
}

```

## Requests to API
The API is secured with one time tokens rotating at every request. The token is constructed according to [RFC 6750 Bearer Token specification](http://tools.ietf.org/html/rfc6750)

First, the API client should hit the *login* endpoint to obtain `access-token`, `uid`, `client`and `expiry`. 
Those parameters should be then send together with the API request in the request headers:

Header | Value 
--------- | ------- 
access-token | wwwww 
token-type   | Bearer
client       | xxxxx 
expiry       | 12334567 
uid          | test@user.pl 

On successful authentication, to the API server will add new `access-token` to the response headers. This new `access-token` should be used on next request.

*Remark* The library used to handle token expiration utilizes a 5 s buffer to support batch requests. 
It enables to send multiple requests to the API. Withing this window, the same tokens can be used to make requests.

