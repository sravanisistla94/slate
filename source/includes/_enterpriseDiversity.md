# Enterprise Diversity
 
Diversity groups the data based on the first filter field (if filter provided), else it groups the data based on the ethnicity (which is the default grouping field in configs)
Diversity gives the total male and female percentage for the filtered data set in addition to the male and female percentage for the each filtered group.


```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.post("localhost:4545/api/enterprise/v1/diversity");
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


### For Multiple Dimensions
Example: multiple dimension filter for location and jobTitle

/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"jobTitle":"TITLE"}]

### For Multiple Dimensions With Multiple Matches

Example: multiple dimensions with multiple matches for location and jobTitle.

/api/enterprise/v1/dimensions?filter=[{"location":{"or":["COUNTRY", "COUNTRY"]}},{"jobTitle":"TITLE"}]

>The above command returns JSON structured like this:

```json
{
   "aggregations":{
      "metrics":[
         {
            "name":"INDIA",
            "value":253,
            "type":"location",
            "displayType":"Location",
            "malePercent":52.96442687747036,
            "femalePercent":47.03557312252965
         },
         {
            "name":"AUSTRALIA",
            "value":225,
            "type":"location",
            "displayType":"Location",
            "malePercent":50.66666666666667,
            "femalePercent":49.333333333333336
         }
      ]
   },
   "totalMalePercent":51.88284518828452,
   "totalFemalePercent":48.11715481171548
}

```
