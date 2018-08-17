# Create New Job

Creates a new job and after creating a new job it checks the skillsmusthave,
skillsgoodtohave, skillsdesired. if these skills exists 
it creates the new entry in the job skill table.
if not it creates the these skills and then it creates 
the new entry in the job skill table.

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.post("localhost:4545/api/api/Jobs/createJob");
```
### payload 
<code>
{
  "companyId": 51,
  "officeId": 4,
  "divisionId": 0,
  "title": "newTitle",
  "internalCode": "19",
  "functionId": 3,
  "seniorityId": 3,
  "qualTypeId": 2,
  "requiredExp": 0,
  "jobDesc": "The job description",
  "jobReq": "The job jobRequirements",
  "benefit": "",
  "minSalary": 0,
  "maxSalary": 188,
  "openDate": "2018-07-26T12:11:38+05:30",
  "closeDate": "2018-08-03T18:30:00.000Z",
  "vacancy": 12,
  "termId": 2,
  "hourTypeId": 2,
  "teamId": 0,
  "status": true,
  "fromResume": false,
  "draft": false,
  "country": 105,
  "region": "TELANGANA",
  "department": "NewDep123",
  "numberVacancies": 0,
  "skillsmusthave": [
    {
      "skill": "java",
      "type": "2"
    },
    {
      "skill": "nodejs",
      "type": "1"
    }
  ],
  "skillsgoodtohave": [
    {
      "skill": "newjs",
      "type": "2"
    },
    {
      "skill": "oldjs",
      "type": "1"
    }
  ],
  "skillsdesired": [
    {
      "skill": "c++",
      "type": "2"
    },
    {
      "skill": "c",
      "type": "1"
    }
  ]
}
</code>
> The above command returns JSON structured like this:

```json
{
    "data": {
        "jobId": "5",
        "companyId": 1,
        "officeId": 4,
        "divisionId": 0,
        "nameId": 7,
        "internalCode": "90",
        "functionId": 3,
        "seniorityId": 3,
        "qualTypeId": 2,
        "requiredExp": 0,
        "jobDesc": "The job description for new job",
        "jobReq": "The job jobRequirements for new job requirement",
        "benefit": "",
        "minSalary": 0,
        "maxSalary": 188,
        "openDate": "2018-07-26T12:11:38+05:30",
        "closeDate": "2018-08-03T18:30:00.000Z",
        "vacancy": 12,
        "termId": 2,
        "hourTypeId": 2,
        "teamId": 4,
        "status": true,
        "fromResume": false,
        "draft": false,
        "department": "NewDep123",
        "region": "TELANGANA",
        "title": "newTitle",
        "numberVacancies": 0,
        "skillsmusthave": [
            {
                "skill": "java",
                "type": "2"
            },
            {
                "skill": "nodejs",
                "type": "1"
            }
        ],
        "skillsgoodtohave": [
            {
                "skill": "newjs",
                "type": "2"
            },
            {
                "skill": "oldjs",
                "type": "1"
            }
        ],
        "skillsdesired": [
            {
                "skill": "c++",
                "type": "2"
            },
            {
                "skill": "c",
                "type": "1"
            }
        ]
    }
}

```