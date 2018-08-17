# Enterprise Dimensions

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.post("localhost:4545/api/enterprise/v1/dimensions");
```
### Dimensions

``location, 
  jobTitle, 
  grade, 
  department``

### Params

param | type
----- | ----
filter| [] array

### For single dimension 
Example: Single dimension filter for location dimension with year

/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"year":"YYYY"}]

>The above command returns JSON structured like this:

```json
{
   "dimensions":[
      {
         "name":"jobTitle",
         "displayName":"Job Title",
         "values":[
            {
               "count":253,
               "key":"Engineer"
            },
            {
               "count":125,
               "key":"Manager"
            }
         ]
      },
      {
         "name":"grade",
         "displayName":"Grade",
         "values":[
            {
               "count":170,
               "key":"P1"
            },
            {
               "count":163,
               "key":"U2"
            },
            {
               "count":116,
               "key":"U4"
            }
         ]
      },
      {
         "name":"department",
         "displayName":"Department",
         "values":[
            {
               "count":121,
               "key":"ENGINEERING"
            },
            {
               "count":119,
               "key":"BUSINESS DEVELOPMENT"
            },
            {
               "count":2,
               "key":"MARKETING"
            }
         ]
      }
   ]
}
```
### For Multiple Dimensions
Example: multiple dimension filter for location and jobTitle

/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"jobTitle":"TITLE"}]

>The above command returns JSON structured like this:

```json
{
   "dimensions":[
      {
         "name":"grade",
         "displayName":"Grade",
         "values":[
            {
               "count":162,
               "key":"U2"
            },
            {
               "count":74,
               "key":"U3"
            },
            {
               "count":17,
               "key":"U1"
            }
         ]
      },
      {
         "name":"department",
         "displayName":"Department",
         "values":[
            {
               "count":68,
               "key":"CORPORATE SERVICES"
            },
            {
               "count":57,
               "key":"ENGINEERING"
            },
            {
               "count":49,
               "key":"BUSINESS DEVELOPMENT"
            },
            {
               "count":12,
               "key":"IT"
            }
         ]
      }
   ]
}

```

### For Multiple Dimensions With Multiple Matches

Example: multiple dimensions with multiple matches for location and jobTitle.

/api/enterprise/v1/dimensions?filter=[{"location":{"or":["COUNTRY", "COUNTRY"]}},{"jobTitle":"TITLE"}]

>The above command returns JSON structured like this:

```json
{
   "dimensions":[
      {
         "name":"grade",
         "displayName":"Grade",
         "values":[
            {
               "count":294,
               "key":"U2"
            },
            {
               "count":145,
               "key":"U3"
            },
            {
               "count":39,
               "key":"U1"
            }
         ]
      },
      {
         "name":"department",
         "displayName":"Department",
         "values":[
            {
               "count":75,
               "key":"BUSINESS DEVELOPMENT"
            },
            {
               "count":74,
               "key":"ENGINEERING"
            },
            {
               "count":17,
               "key":"IT"
            }
         ]
      }
   ]
}
```
