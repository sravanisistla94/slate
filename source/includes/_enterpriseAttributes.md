# Enterprise Attributes
Result contains array of attributes which are present in `defaultSchema.history.predictions` in configuration file.
This result can be changes by altering the config file.

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.post("localhost:4545/api/enterprise/v1/attributes");
```

>The above command returns JSON structured like this:

```json
[
   {
      "displayName":"Attrition",
      "name":"attrition",
      "isIncreaseGood":false,
      "value":[
         {
            "displayName":"Predicted Attrition (Avg.)",
            "column_name":"predicted_attrition"
         }
      ]
   },
   {
      "displayName":"Retention",
      "name":"loyalty",
      "isIncreaseGood":true,
      "value":[
         {
            "displayName":"Predicted Retention (Avg.)",
            "column_name":"loyalty_predicted"
         }
      ]
   },
   {
      "displayName":"Performance",
      "name":"performance",
      "isIncreaseGood":true,
      "value":[
         {
            "displayName":"Predicted Performance (Avg.)",
            "column_name":"performance_predicted"
         }
      ]
   }
]

```