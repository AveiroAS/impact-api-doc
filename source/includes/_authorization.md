# Authorization

Authorization is performed using Devise (server side) and ng-token-auth (client side) and is token based. User authenticates using email and password.

## Login

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