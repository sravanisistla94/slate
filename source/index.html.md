---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
   - shell
  # - ruby
  # - python
  #- javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  # - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

Please contact live.xopa.com to get the access token.

> To authorize, use the access_token value in the parameter.

```shell
access_token = <ACCESS TOKEN>
```

#Roboroy API

## Create New Job

Creates a new job and after creating a new job it checks the skillsmusthave,
skillsgoodtohave, skillsdesired. if these skills exists 
it creates the new entry in the job skill table.
if not it creates the these skills and then it creates 
the new entry in the job skill table.

### Http Request
      
 `CREATE live.x0pa.com/api/api/Jobs/createJob`

```shell
curl -X POST 'https://live.x0pa.com/api/api/Jobs/createJob?access_token=<ACCESS TOKEN>' -H 'Content-Type:application/json' -d '{
  "companyId": 5143,
  "officeId": 4,
  "divisionId": 0,
  "title": "newTitle",
  "internalCode": "1990",
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
'
```

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
this endpoint returns a new Job with complete job details.

## Find All Users Job Applicants

gets the entire list of applicants

### Http Request
      
 `GET live.x0pa.com/api/api/Applications/findAllUserJobApplicants`

```shell
curl https://live.x0pa.com/api/api/Applications/findAllUserJobApplicants?access_token=<ACCESS TOKEN>&jobId=1&filter[limit]=10&filter[skip]=0&searchKey=abs&status=true

```
### Parameters

params     | type  | descrption
---------- | ----- | ------
shortlisted | boolean | applicants application status.
jobId       |  integer | After creating a job it generates a unique id i.e(job id).
applicationId | integer | Applicants unique id after applying for a job. 
searchKey   | string   | key for searching a particular applicant from the results.
filter[limit/skip]| number | it limits/skips the values.
status      | string   | status of a particular applicant.
> The above command returns JSON structured like this:

```json
{
    "applications": [
        {
            "appId": 1,
            "profileId": 2,
            "jobId": 5,
            "appDate": "2018-04-08T18:30:00.000Z",
            "coverLetter": null,
            "coverLetterName": null,
            "appStatusId": 4,
            "fromTalentPool": false,
            "review": null,
            "loyalty": "36.0",
            "skillMatch": "25.0327",
            "twoWayMatch": null,
            "shortlisted": null,
            "performance": null,
            "fromApplicant": false,
            "invitesent": null,
            "inviteaccept": null,
            "teamId": 14,
            "updateDate": null,
            "roboroyShortlist": null,
            "skillMatchCustom": null,
            "stage": "Screening",
            "location": "Hyderabad",
            "profile": {
                "profileId": 2,
                "summary": "summary details",
                "genderId": null,
                "firstName": "xxx",
                "middleName": null,
                "lastName": "xxx",
                "preferName": null,
                "birthDate": "1988-06-17T18:30:00.000Z",
                "marriageId": 2,
                "email": "xxx@yahoo.co.in",
                "addressId": "29",
                "nationalityId": 15,
                "totalExp": "3.5833333333333335",
                "managementExp": null,
                "courtCharge": null,
                "bankruptcy": null,
                "crime": null,
                "linkedin": null,
                "facebook": null,
                "salary": null,
                "currencyId": null,
                "entryUserId": "3",
                "createDate": "2018-04-08T18:30:00.000Z",
                "updateDate": "2018-04-08T18:30:00.000Z",
                "profileIndex": "182",
                "teamId": null,
                "ethnicityId": null,
                "globalTalent": null,
                "address": {
                    "addressId": 2,
                    "addressLine1": "Srilaxmi nagar colony",
                    "addressLine2": null,
                    "locationId": "499",
                    "zipcode": "500058",
                    "location": {
                        "locationId": 49469,
                        "locationName": "Hyderabad",
                        "stateId": 10,
                        "countryId": 1,
                        "country": {
                            "countryId": 1,
                            "countryShort": "IN",
                            "countryFull": "India",
                            "countryCode": "+91"
                        },
                        "state": {
                            "stateId": 10,
                            "stateShort": "AP",
                            "stateFull": "Andhra Pradesh",
                            "countryId": 1
                        }
                    }
                },
                "country": {
                    "countryId": 1,
                    "countryShort": "IN",
                    "countryFull": "India",
                    "countryCode": "+91"
                }
            },
            "job": {
                "jobId": 5,
                "companyId": "3",
                "officeId": "1",
                "divisionId": "0",
                "nameId": "2",
                "internalCode": null,
                "functionId": 1,
                "seniorityId": 2,
                "qualTypeId": 10,
                "requiredExp": "5",
                "jobDesc": "Description about the Job",
                "benefit": "",
                "minSalary": "5000",
                "maxSalary": "6000",
                "currencyId": 125,
                "openDate": "2018-02-25T00:00:00.000Z",
                "closeDate": null,
                "vacancy": 2,
                "termId": 1,
                "hourTypeId": 1,
                "teamId": "37",
                "status": true,
                "fromResume": false,
                "jobIndex": "90",
                "parsedFileLocation": "",
                "rawFileLocation": "",
                "draft": false,
                "department": null,
                "region": null,
                "countryId": null,
                "jobname": {
                    "nameId": 52,
                    "nameName": "Administrator",
                    "linkedinJobnameId": null,
                    "companyId": null
                },
                "jobfunction": {
                    "functionId": 61,
                    "functionName": "Accounting"
                },
                "jobseniority": {
                    "seniorityId": 92,
                    "seniorityName": "1 ~ 5 years"
                },
                "currency": {
                    "currencyId": 19,
                    "currencyShort": "SGD",
                    "currencyFull": "Singapore Dollar",
                    "countryId": 200
                },
                "hourtype": {
                    "typeId": 1,
                    "typeName": "Full-Time"
                },
                "term": {
                    "termId": 1,
                    "termName": "Permanent"
                },
                "qualificationtype": {
                    "typeId": 1,
                    "typeName": "Bachelor's Degree"
                },
                "company": {
                    "companyId": 300,
                    "companyName": "1st Colonial Bancorp Inc.",
                    "description": null,
                    "website": null,
                    "linkedinCompanyId": null
                },
                "office": {
                    "officeId": 1,
                    "officeName": "Google Inc.",
                    "companyId": "3",
                    "addressId": "4",
                    "officeWebsite": "https://www.google.com/",
                    "address": {
                        "addressId": 4,
                        "addressLine1": "",
                        "addressLine2": null,
                        "locationId": "5",
                        "zipcode": "48105",
                        "location": {
                            "locationId": 5,
                            "locationName": "Ann Arbor",
                            "stateId": 7,
                            "countryId": 23,
                            "country": {
                                "countryId": 9,
                                "countryShort": "US",
                                "countryFull": "United States",
                                "countryCode": "+1"
                            },
                            "state": {
                                "stateId": 7,
                                "stateShort": "MI",
                                "stateFull": "Michigan",
                                "countryId": 23
                            }
                        }
                    }
                }
            },
            "status": {
                "statusId": 4,
                "statusName": "Reviewing"
            }
        }
    ]

```
this endpoint returns list of applications.


#Enterprise API

## Get Dimensions
It returns the dimensions key count bases on the applied filter.
NOTE: The result will not contains the fields which are applied in filter

```shell
 curl https://live.x0pa.com/api/enterprise/v1/dimensions?access_token=<ACCESS TOKEN>

```
### Http Request
      
 `GET live.x0pa.com/api/enterprise/v1/dimensions`

### List Of Dimensions

dimension | description
----------| -----------
 location | location of a particular employee.
 jobTitle | jobtitle of a particular employee.
 grade    | grade of a employee
 department| department of a employee.
 gender   | gender of a employee.

### Params

   param      | type | descrption             
--------------| ---- | ----------
filter[{dimension:value}] | []array  | filters based on the dimension and value.
 dimension                |  string  | dimension can be from the above mentioned list.
 value                    |  string  | value of dimension.
         
                                              
### Sample End Points

### For single dimension 
Example: Single dimension filter for location dimension with year

`/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"year":"YYYY"}]`

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

`/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"jobTitle":"TITLE"}]`

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

`/api/enterprise/v1/dimensions?filter=[{"location":{"or":["COUNTRY", "COUNTRY"]}},{"jobTitle":"TITLE"}]`

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
this endpoint returns list of dimensions key count based on the applied filter.

## Get Diversity
 
Diversity groups the data based on the first filter field (if filter provided), else it groups the data based on the ethnicity (which is the default grouping field in configs)
Diversity gives the total male and female percentage for the filtered data set in addition to the male and female percentage for the each filtered group.

### Http Request
      
 `GET live.x0pa.com/api/enterprise/v1/diversity`

```shell
curl https://live.x0pa.com/api/enterprise/v1/diversity?access_token=<ACCESS TOKEN>
```
### List Of Dimensions

dimension | description
----------| -----------
 location | location of a particular employee.
 jobTitle | jobtitle of a particular employee.
 grade    | grade of a employee
 department| department of a employee.

### Params

   param      | type | descrption             
--------------| ---- | ----------
filter[{dimension:value}] | []array  | filters based on the dimension and value.
 dimension                |  string  | dimension can be from the above mentioned list.
 value                    |  string  | value of dimension.

### Sample End Points

### For single dimension 
Example: Single dimension filter for location dimension with year

`/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"year":"YYYY"}]`


### For Multiple Dimensions
Example: multiple dimension filter for location and jobTitle

`/api/enterprise/v1/dimensions?filter=[{"location":"COUNTRY"},{"jobTitle":"TITLE"}]`

### For Multiple Dimensions With Multiple Matches

Example: multiple dimensions with multiple matches for location and jobTitle.

`/api/enterprise/v1/dimensions?filter=[{"location":{"or":["COUNTRY", "COUNTRY"]}},{"jobTitle":"TITLE"}]`

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
this endpoint returns the metrics of male and female percentage of each filtered object. In addition to the the total gender diversity.

## Get Attributes

Result contains array of attributes which are present in `defaultSchema.history.predictions` in configuration file.
This result can be changes by altering the config file.

### Http Request
      
 `GET live.x0pa.com/api/enterprise/v1/attributes`

```shell
curl https://live.x0pa.com/api/enterprise/v1/attributes?access_token=<ACCESS TOKEN>
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
this endpoint returns the dimension attributes.

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>
