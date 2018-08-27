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

Roboroy API main functionality of is to parse the resume successfully. When a recruiter prepares his desired job description details by creating a job and uploads a resume to that job, then the roboroy scripts will parse the resume, compares the requirements present in the job description with the details present in the resume. It identifies whether he is a right candidate to this job or not by calculating scores (like cv relevance, benchmark, loyalty, performance).based on the stats, recruiter will decide whether to shortlist this candidate for further proceedings or not.Once he shortlists the candidate, an email will be sent to candidate, upon accepting the email by the candidate, recruiter starts the workflow, (video interview, phone interview,...) and finally recruiter accepts or rejects his candidature. Talent pool and gloabl talent pool are nothing but storage of resumes. (kind of...). If recruiter interested in the candidate and wants to store resume internally into his application, he will add those resumes to talent pool. So that when he creates a job, he can upload the resume directly from talent pool search.

Enterprise API gets stats of employees based on dimensions (job title, grade, location, department) of an organization. 

# Authentication

Please contact x0pa engineering team to get the access token.

> To authorize, use the access_token value in the parameter.

```shell
access_token = <ACCESS TOKEN>
```

#Roboroy API

## Meta Information 
Meta information is needed while creating a new job.

### Http Request

`GET /api/api/Jobs/metaInformation`

```shell
curl https://live.x0pa.com/api/api/Jobs/metaInformation?access_token=<ACCESS TOKEN>
```
> The above command returns JSON structured like this:

 ```json
{
    "meta":{
        "jobFunctions":[
            {
                "functionId":1,
                "functionName":"Accounting"
            }
        ],
        "jobSeniorities":[
            {
                "seniorityId":1,
                "seniorityName":"0 year"
            }
        ],
        "qualificationTypes":[
            {
                "typeId":1,
                "typeName":"Early Childhood Education"
            },
            {
                "typeId":2,
                "typeName":"Primary Education"
            }
        ],
        "currencies":[
            {
                "currencyId":1,
                "currencyShort":"AED",
                "currencyFull":"United Arab Emirates Dirham",
                "countryId":237
            },
            {
                "currencyId":2,
                "currencyShort":"AFN",
                "currencyFull":"Afghanistan Afghani",
                "countryId":1
            }
        ],
        "terms":[
            {
                "termId":1,
                "termName":"Permanent"
            },
            {
                "termId":2,
                "termName":"Contract"
            },
            {
                "termId":3,
                "termName":"Temporary"
            }
        ],
        "hourTypes":[
            {
                "typeId":1,
                "typeName":"Full-Time"
            },
            {
                "typeId":2,
                "typeName":"Part-Time"
            },
            {
                "typeId":3,
                "typeName":"PRN"
            }
        ],
        "jobName":[
            {
                "nameId":1,
                "nameName":"Able Seaman",
                "linkedinJobnameId":null,
                "companyId":null
            }
        ],
        "skilltypes":[
            {
                "typeId":1,
                "typeName":"Technical (Hard) Skills"
            },
            {
                "typeId":2,
                "typeName":"Transferable (Soft) Skills"
            },
            {
                "typeId":3,
                "typeName":"Languages"
            },
            {
                "typeId":4,
                "typeName":"General Skills"
            }
        ],
        "countries":[
            {
                "countryId":1,
                "countryShort":"AF",
                "countryFull":"Afghanistan",
                "countryCode":"+93"
            },
            {
                "countryId":2,
                "countryShort":"AX",
                "countryFull":"Åland Islands",
                "countryCode":"+358"
            },
            {
                "countryId":105,
                "countryShort":"IN",
                "countryFull":"India",
                "countryCode":"+91"
            }
        ],
        "officeId":"4",
        "company":{
            "companyId":5143,
            "companyName":"X0PA Ai Pte. Ltd.",
            "description":"X0PA is a people management Enterprise system that uses data analytics, machine learning and proprietary algorithms to produce data-driven, evidenced-based predictions for business leaders, managers, employees and candidates.",
            "website":"https://www.x0pa.com/",
            "linkedinCompanyId":null
        }
    }
}

```
this endpoint returns the meta information for creating a new job.

## Create New Job

Creates a new job and after creating a new job it checks the skillsmusthave,
skillsgoodtohave, skillsdesired. if these skills exists 
it creates the new entry in the job skill table.
if not it creates the these skills and then it creates 
the new entry in the job skill table.

### Http Request
      
 `CREATE /api/api/Jobs/createJob`

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
      
 `GET /api/api/Applications/findAllUserJobApplicants`

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
loyalty     | numeric  | This metric signifies the probability of a candidate to be working                             at the same position for the next one year without intention to                                change.
performance |  numeric | This metric signifies the probability for the candidate to deserve                             an earlier than average promotion.
twoWayMatch |  numeric |  This score signifies how similar is the candidate's profile when                               compared to employees at similar position in an organization.
skillMatchCustom | numeric | This score signifies how close the candidate's resume matches                                  with job description.

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

## Resume Upload
Uploads a resume 

```shell

curl -X POST \
  'https://live.x0pa.com/api/roboroy/resume_parse?access_token=<ACCESS TOKEN>' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F 'file=@/home/xxxxx/xxxxxx/xxxx.pdf' \
  -F job_Id=1 \
  -F client=fastjobs
```
### Http Request

`POST /api/roboroy/resume_parse`

### Inputs

Key | Value
---- | ----
file | resume file(s) 
jobId | After creating a job it generates a unique id i.e(job id).
client | constant value equal to fastjobs
 
 > The above command returns JSON structured like this:

 ```json
{
   "file_path_list":[
      "roboroy/resume/raw/xxxx_320_20180821051653901461.pdf"
   ],
   "inconvertible_list":[

   ],
   "raw_name_list":[
      "xxxx.pdf"
   ],
   "task_id":"8fc662a4-9a59-4f0f-bce0-b6e660a911c9_320_20180821051653902906",
   "wrong_file_list":[

   ]
}

```
this endpoint uploads a resume for a particular job.


#Enterprise API

## Get Dimensions
It returns the dimensions key count bases on the applied filter.
NOTE: The result will not contains the fields which are applied in filter

```shell
 curl https://live.x0pa.com/api/enterprise/v1/dimensions?access_token=<ACCESS TOKEN>

```
### Http Request
      
 `GET /api/enterprise/v1/dimensions`

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
      
 `GET /api/enterprise/v1/diversity`

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
      
 `GET /api/enterprise/v1/attributes`

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

## Get DashboardAttributes
It gives the analysis on the attributes(attrition retention performance gender)
and gets the highest and lowest values of attributes based on each dimensions(job title, grade, location, department). In addition to this it will do the analysis on the predicted and current values and returns whether the isIncreaseGood is good or not.

### Http Request

`GET /api/enterprise/v1/dashboardattributes`

```shell
curl http://live.x0pa.com/api/enterprise/v1/dashboardattributes?access_token=<ACCESS TOKEN>
```

### List Of Attributes

attribute  |  description
-----------| ------------
Attrition(HEADCOUNT) | No of employees at risk of leaving the organisation in next the 12                          months
Retention(Loyalty) | The probability of the employees leaving the organisation in the next                       12 months
Performance        | Predicted performance of employees over the next 12 months
Gender proportion  | The breakdown of gender gaps between existing employe


> The above command returns JSON structured like this:

```json
[
    {
        "name":"ATTRITION (HEADCOUNT)",
        "isIncreaseGood":false,
        "predicted":342,
        "current":0,
        "delta":null,
        "highest":{
            "label":"HIGHEST ATTRITION",
            "value":[
                {
                    "label":"Job Title",
                    "value":"Co-ordinator"
                },
                {
                    "label":"Grade",
                    "value":"E1"
                },
                {
                    "label":"Location",
                    "value":"CHINA"
                },
                {
                    "label":"Department",
                    "value":"MARKETING"
                }
            ]
        },
        "lowest":{
            "label":"LOWEST ATTRITION",
            "value":[
                {
                    "label":"Job Title",
                    "value":"Co-ordinator"
                },
                {
                    "label":"Grade",
                    "value":"E1"
                },
                {
                    "label":"Location",
                    "value":"CHINA"
                },
                {
                    "label":"Department",
                    "value":"MARKETING"
                }
            ]
        }
    },
    {
        "name":"RETENTION (AVG. %)",
        "isIncreaseGood":true,
        "predicted":67.23889763779528,
        "current":0,
        "delta":null,
        "highest":{
            "label":"HIGHEST RETENTION",
            "value":[

            ]
        },
        "lowest":{
            "label":"LOWEST RETENTION",
            "value":[

            ]
        }
    },
    {
        "name":"PERFORMANCE (AVG. %)",
        "isIncreaseGood":true,
        "predicted":61.105511811023625,
        "current":0,
        "delta":null,
        "highest":{
            "label":"HIGHEST PERFORMANCE",
            "value":[

            ]
        },
        "lowest":{
            "label":"LOWEST PERFORMANCE",
            "value":[

            ]
        }
    },
    {
        "current":823,
        "predicted":823,
        "isIncreaseGood":true,
        "name":"Gender Proportion (%)",
        "delta":0,
        "highest":{
            "label":"HIGHEST PAYGAP",
            "value":[

            ]
        },
        "lowest":{
            "label":"LOWEST PAYGAP",
            "value":[

            ]
        }
    }
]
```
this endpoint returns the analysis on attributes based on each dimension. 

## Get PayGap
It gets the mean and median paygap based on the gender and ethnicity.
Male and female percentages based on the paybands.
paybands caterogizes as:
paybandA - 0-25%
paybandB - 25-50%
paybandC - 50-75%
paybandD - 75-100%
It also gets mean,median and male female percentages on the paybands based on the dimensions (job title, grade, location, department) provided to filter the data.


### Http Request

`GET /api/enterprise/v1/paygap`

```shell
curl http://live.x0pa.com/api/enterprise/v1/paygap?access_token=<ACCESS TOKEN>
```

### Params

   param      | type | descrption             
--------------| ---- | ----------
filter[{dimension:value}] | []array  | filters based on the dimension and value.
 dimension                |  string  | dimension can be from the above mentioned list.
 value                    |  string  | value of dimension.

### Sample End Points

### For single dimension 
Example: Single dimension filter for location dimension with year

`/api/enterprise/v1/paygap?filter=[{"location":"COUNTRY"},{"year":"YYYY"}]`


### For Multiple Dimensions
Example: multiple dimension filter for location and grade

`/api/enterprise/v1/paygap?filter=[{"grade":"KEY"},{"location":"COUNTRY"}]`

### For Multiple Dimensions With Multiple Matches

Example: multiple dimensions with multiple matches for location and grade.

`/api/enterprise/v1/paygap?filter=[{"grade":{"or":["x","Y"]}},{"location":{"or":["A","B"]}}]`
> The above command returns JSON structured like this:

```json
{
    "aggregations":{
        "metrics":[
            {
                "key":"AUSTRALIA",
                "type":"location",
                "count":432,
                "payBands":[
                    {
                        "malePercent":86.23853211009175,
                        "femalePercent":13.761467889908257,
                        "payBandName":"Pay Band D"
                    },
                    {
                        "malePercent":75.70093457943925,
                        "femalePercent":24.299065420560748,
                        "payBandName":"Pay Band C"
                    },
                    {
                        "malePercent":52.83018867924528,
                        "femalePercent":47.16981132075472,
                        "payBandName":"Pay Band B"
                    },
                    {
                        "malePercent":43.63636363636363,
                        "femalePercent":56.36363636363636,
                        "payBandName":"Pay Band A"
                    }
                ],
                "meanPayGap":16733.106261859582,
                "medianPayGap":13691.8125,
                "ethnicMeanPayGap":null,
                "ethnicMedianPayGap":null
            },
            {
                "key":"SINGAPORE",
                "type":"location",
                "count":51,
                "payBands":[
                    {
                        "malePercent":84.61538461538461,
                        "femalePercent":15.384615384615385,
                        "payBandName":"Pay Band D"
                    },
                    {
                        "malePercent":83.33333333333334,
                        "femalePercent":16.666666666666664,
                        "payBandName":"Pay Band C"
                    },
                    {
                        "malePercent":76.92307692307693,
                        "femalePercent":23.076923076923077,
                        "payBandName":"Pay Band B"
                    },
                    {
                        "malePercent":53.84615384615385,
                        "femalePercent":46.15384615384615,
                        "payBandName":"Pay Band A"
                    }
                ],
                "meanPayGap":4761.283400809716,
                "medianPayGap":2666.5,
                "ethnicMeanPayGap":null,
                "ethnicMedianPayGap":null
            },
            {
                "key":"UK",
                "type":"location",
                "count":5,
                "payBands":[
                    {
                        "malePercent":100,
                        "femalePercent":0,
                        "payBandName":"Pay Band D"
                    },
                    {
                        "malePercent":100,
                        "femalePercent":0,
                        "payBandName":"Pay Band C"
                    },
                    {
                        "malePercent":100,
                        "femalePercent":0,
                        "payBandName":"Pay Band B"
                    },
                    {
                        "malePercent":50,
                        "femalePercent":50,
                        "payBandName":"Pay Band A"
                    }
                ],
                "meanPayGap":23902.125,
                "medianPayGap":27191.5,
                "ethnicMeanPayGap":null,
                "ethnicMedianPayGap":null
            },
        ]
    },
    "meanPayGap":12912.386292707335,
    "medianPayGap":12649.5,
    "ethnicMeanPayGap":null,
    "ethnicMedianPayGap":null,
    "payband":[
        {
            "malePercent":81.28654970760235,
            "femalePercent":18.71345029239766,
            "payBandName":"Pay Band D"
        },
        {
            "malePercent":73.25581395348837,
            "femalePercent":26.744186046511626,
            "payBandName":"Pay Band C"
        },
        {
            "malePercent":56.024096385542165,
            "femalePercent":43.97590361445783,
            "payBandName":"Pay Band B"
        },
        {
            "malePercent":41.24293785310734,
            "femalePercent":58.75706214689266,
            "payBandName":"Pay Band A"
        }
    ]
}

```
this endpoint returns the male and female payband percentages and mean median paygap for gender and ethnicity for global and filtered dimensions.

## Get Measures
It gets all the employee records for a company with company details and default year.
It filters the data based on the dimensions(job title, grade, location, department) provided.
It also gets the details of a particular employee by providing the profileKey.
The configurations object contains the UI mapping variables to that of the result set.
The column name suggests the configuration detail path of a particular field.
The snapshot represent the dashboard mapping of the display names to that of the corresponding result
It gets the stats(avg and sum) of all the employees based on the filtered data.

### Http Request
`GET /api/enterprise/v1/measures`

```shell
curl http://live.x0pa.com/api/enterprise/v1/measures?access_token=<ACCESS TOKEN>
```
### Params

   param      | type | descrption             
--------------| ---- | ----------
filter[{dimension:value}] | []array  | filters based on the dimension and value.
 dimension                |  string  | dimension can be from the above mentioned list.
 value                    |  string  | value of dimension.

### Sample End Points

### For single dimension 
Example: Single dimension filter for location dimension with year

`/api/enterprise/v1/measures?filter=[{"location":"COUNTRY"},{"year":"YYYY"}]`


### For Multiple Dimensions
Example: multiple dimension filter for location and grade

`/api/enterprise/v1/measures?filter=[{"grade":"KEY"},{"location":"COUNTRY"}]`

### For Multiple Dimensions With Multiple Matches

Example: multiple dimensions with multiple matches for location and grade.

`/api/enterprise/v1/measures?filter=[{"grade":{"or":["x","Y"]}},{"location":{"or":["A","B"]}}]`

> The above command returns JSON structured like this:

```json
{
    "aggregations":{
        "metrics":[
            {
                "name":"x0pa",
                "value":1270,
                "type":"company",
                "displayType":"Company",
                "records":[
                    {
                        "profileKey":"9",
                        "gender":"male",
                        "ethnicity":null,
                        "joinDate":"2012-05-25",
                        "age":28,
                        "experience":5.4,
                        "lastWorkingday":null,
                        "maritalStatus":"S",
                        "pastCompany":"",
                        "history":[
                            {
                                "year":"2014",
                                "monthlySalary":32716,
                                "department":"MARKETING",
                                "location":"AUSTRALIA",
                                "jobTitle":"Engineer",
                                "grade":"U2",
                                "company":"x0pa",
                                "actuals":{
                                    "loyalty":{
                                        "name":"Loyalty",
                                        "values":{
                                            "loyalty_actual":{
                                                "name":"loyalty_actual",
                                                "values":null
                                            }
                                        }
                                    },
                                    "performance":{
                                        "name":"Performance",
                                        "values":{
                                            "performance_actual":{
                                                "name":"performance_actual",
                                                "values":null
                                            }
                                        }
                                    },
                                    "attrition":{
                                        "name":"Attrition",
                                        "values":{
                                            "actual_attrition":{
                                                "name":"actualAttrition",
                                                "values":0
                                            }
                                        }
                                    }
                                },
                                "predictions":{
                                    "loyalty":{
                                        "name":"Loyalty",
                                        "values":{
                                            "loyalty_predicted":{
                                                "name":"loyalty_predicted",
                                                "values":null
                                            },
                                            "loyalty_5percent":{
                                                "name":"FivePercentLoyalty",
                                                "values":null
                                            },
                                            "loyalty_10percent":{
                                                "name":"TenPercentLoyalty",
                                                "values":null
                                            },
                                            "loyalty_15percent":{
                                                "name":"FifteenPercentLoyalty",
                                                "values":null
                                            },
                                            "loyalty_imm_promotion":{
                                                "name":"loyalty_imm_promotion",
                                                "values":null
                                            },
                                            "loyalty_no_promotion":{
                                                "name":"loyalty_no_promotion",
                                                "values":null
                                            }
                                        }
                                    },
                                    "performance":{
                                        "name":"Performance",
                                        "values":{
                                            "performance_predicted":{
                                                "name":"performance_predicted",
                                                "values":null
                                            }
                                        }
                                    },
                                    "attrition":{
                                        "name":"Attrition",
                                        "values":{
                                            "predicted_attrition":{
                                                "name":"predictedAttrition",
                                                "values":null
                                            }
                                        }
                                    }
                                }
                            },
                            {
                                "year":"2015",
                                "monthlySalary":38749,
                                "department":"MARKETING",
                                "location":"AUSTRALIA",
                                "jobTitle":"Engineer",
                                "grade":"U2",
                                "company":"x0pa",
                                "actuals":{
                                    "loyalty":{
                                        "name":"Loyalty",
                                        "values":{
                                            "loyalty_actual":{
                                                "name":"loyalty_actual",
                                                "values":null
                                            }
                                        }
                                    },
                                    "performance":{
                                        "name":"Performance",
                                        "values":{
                                            "performance_actual":{
                                                "name":"performance_actual",
                                                "values":null
                                            }
                                        }
                                    },
                                    "attrition":{
                                        "name":"Attrition",
                                        "values":{
                                            "actual_attrition":{
                                                "name":"actualAttrition",
                                                "values":0
                                            }
                                        }
                                    }
                                },
                                "predictions":{
                                    "loyalty":{
                                        "name":"Loyalty",
                                        "values":{
                                            "loyalty_predicted":{
                                                "name":"loyalty_predicted",
                                                "values":null
                                            },
                                            "loyalty_5percent":{
                                                "name":"FivePercentLoyalty",
                                                "values":null
                                            },
                                            "loyalty_10percent":{
                                                "name":"TenPercentLoyalty",
                                                "values":null
                                            },
                                            "loyalty_15percent":{
                                                "name":"FifteenPercentLoyalty",
                                                "values":null
                                            },
                                            "loyalty_imm_promotion":{
                                                "name":"loyalty_imm_promotion",
                                                "values":null
                                            },
                                            "loyalty_no_promotion":{
                                                "name":"loyalty_no_promotion",
                                                "values":null
                                            }
                                        }
                                    },
                                    "performance":{
                                        "name":"Performance",
                                        "values":{
                                            "performance_predicted":{
                                                "name":"performance_predicted",
                                                "values":null
                                            }
                                        }
                                    },
                                    "attrition":{
                                        "name":"Attrition",
                                        "values":{
                                            "predicted_attrition":{
                                                "name":"predictedAttrition",
                                                "values":null
                                            }
                                        }
                                    }
                                }
                            },
                            {
                                "year":"2016",
                                "monthlySalary":43787,
                                "department":"ENGINEERING",
                                "location":"AUSTRALIA",
                                "jobTitle":"Engineer",
                                "grade":"U3",
                                "company":"x0pa",
                                "actuals":{
                                    "loyalty":{
                                        "name":"Loyalty",
                                        "values":{
                                            "loyalty_actual":{
                                                "name":"loyalty_actual",
                                                "values":null
                                            }
                                        }
                                    },
                                    "performance":{
                                        "name":"Performance",
                                        "values":{
                                            "performance_actual":{
                                                "name":"performance_actual",
                                                "values":null
                                            }
                                        }
                                    },
                                    "attrition":{
                                        "name":"Attrition",
                                        "values":{
                                            "actual_attrition":{
                                                "name":"actualAttrition",
                                                "values":0
                                            }
                                        }
                                    }
                                },
                                "predictions":{
                                    "loyalty":{
                                        "name":"Loyalty",
                                        "values":{
                                            "loyalty_predicted":{
                                                "name":"loyalty_predicted",
                                                "values":70.2
                                            },
                                            "loyalty_5percent":{
                                                "name":"FivePercentLoyalty",
                                                "values":0.58
                                            },
                                            "loyalty_10percent":{
                                                "name":"TenPercentLoyalty",
                                                "values":0.564
                                            },
                                            "loyalty_15percent":{
                                                "name":"FifteenPercentLoyalty",
                                                "values":0.55
                                            },
                                            "loyalty_imm_promotion":{
                                                "name":"loyalty_imm_promotion",
                                                "values":0.412
                                            },
                                            "loyalty_no_promotion":{
                                                "name":"loyalty_no_promotion",
                                                "values":0.424
                                            }
                                        }
                                    },
                                    "performance":{
                                        "name":"Performance",
                                        "values":{
                                            "performance_predicted":{
                                                "name":"performance_predicted",
                                                "values":56
                                            }
                                        }
                                    },
                                    "attrition":{
                                        "name":"Attrition",
                                        "values":{
                                            "predicted_attrition":{
                                                "name":"predictedAttrition",
                                                "values":0
                                            }
                                        }
                                    }
                                }
                            }
                        ]
                    },

                ]
            }
        ]
    },
    "defaultYear":2016
},
"configurations":{
    "profile":{
        "name":{
            "columnName":"profileKey"
        },
        "demographic":[
            {
                "displayName":"Designation",
                "columnName":"history.jobTitle"
            },
            {
                "displayName":"Department",
                "columnName":"history.department"
            },
            {
                "displayName":"Grade",
                "columnName":"history.grade"
            },
            {
                "displayName":"Location",
                "columnName":"history.location"
            }
        ],
        "predictions":{
            "loyalty":{
                "displayName":"Retention",
                "isPredicted":true,
                "isIncreaseGood":true,
                "values":[
                    {
                        "displayName":"Employee Score",
                        "columnName":"history.predictions.loyalty.values.loyalty_predicted.values"
                    },
                    {
                        "displayName":"Company Average",
                        "value":67.23889763779528
                    }
                ],
                "min":0.4,
                "max":100
            },
            "performance":{
                "displayName":"Performance",
                "isPredicted":true,
                "isIncreaseGood":true,
                "values":[
                    {
                        "displayName":"Employee Score",
                        "columnName":"history.predictions.performance.values.performance_predicted.values"
                    },
                    {
                        "displayName":"Company Average",
                        "value":61.105511811023625
                    }
                ],
                "min":43,
                "max":93
            }
        },
        "recommendations":{
            "retention":{
                "displayName":"Retention",
                "values":[
                    {
                        "displayName":"SALARY INCREASE 5%",
                        "columnName":"history.predictions.loyalty.values.loyalty_5percent.values"
                    },
                    {
                        "displayName":"SALARY INCREASE 10%",
                        "columnName":"history.predictions.loyalty.values.loyalty_10percent.values"
                    },
                    {
                        "displayName":"SALARY INCREASE 15%",
                        "columnName":"history.predictions.loyalty.values.loyalty_15percent.values"
                    },
                    {
                        "displayName":"PROMOTION - YES",
                        "columnName":"history.predictions.loyalty.values.loyalty_imm_promotion.values"
                    },
                    {
                        "displayName":"PROMOTION - NO",
                        "columnName":"history.predictions.loyalty.values.loyalty_no_promotion.values"
                    }
                ]
            },
            "performance":{
                "displayName":"Performance",
                "values":[

                ]
            }
        }
    },
    "snapshot":[
        {
            "displayName":"Name",
            "columnName":"profileKey",
            "isSearchOn":true
        },
        {
            "displayName":"Retention",
            "columnName":"history.predictions.loyalty.values.loyalty_predicted.values",
            "isPredicted":true,
            "isIncreaseGood":true,
            "min":0.4,
            "max":100
        },
        {
            "displayName":"Performance",
            "columnName":"history.predictions.performance.values.performance_predicted.values",
            "isPredicted":true,
            "isIncreaseGood":true,
            "min":43,
            "max":93
        },
        {
            "displayName":"Exp",
            "columnName":"experience"
        },
        {
            "displayName":"Age",
            "columnName":"age"
        },
        {
            "displayName":"Current Salary",
            "columnName":"history.monthlySalary"
        },
        {
            "displayName":"Designation",
            "columnName":"history.jobTitle",
            "isSearchOn":true
        },
        {
            "displayName":"Department",
            "columnName":"history.department",
            "isSearchOn":true
        },
        {
            "displayName":"Grade",
            "columnName":"history.grade",
            "isSearchOn":true
        },
        {
            "displayName":"Location",
            "columnName":"history.location",
            "isSearchOn":true
        },
        {
            "displayName":"DOJ",
            "columnName":"joinDate"
        },
        {
            "displayName":"Gender",
            "columnName":"gender",
            "isSearchOn":true
        },
        {
            "displayName":"Past Company",
            "columnName":"pastCompany",
            "isSearchOn":true
        }
    ]
    }
}

```
### For stats
Example: multiple dimension filter for location and grade and stats(avg,sum) on the filters applied

`/api/enterprise/v1/measures?filter=[{"grade":"KEY"},{"location":"COUNTRY"}]&stats=[{"avg":"loyalty_15percent"}]`

`/api/enterprise/v1/measures?filter=[{"grade":"KEY"},{"location":"COUNTRY"}]&stats=[{"sum":"loyalty_15percent"}]`

> The above command returns JSON structured like this:
for sum:

```json
{
    "aggregations":{
        "metrics":[
            {
                "name":"x0pa",
                "value":1270,
                "dimensionsList":[
                    {
                        "value":"x0pa",
                        "dimension":"company"
                    }
                ],
                "predictions":{
                    "loyalty":{
                        "loyalty_15percent":{
                            "columnName":"loyalty_15percent",
                            "displayName":"loyalty_15percent",
                            "value":665.4659999999999
                        }
                    }
                }
            }
        ],
        "defaultYear":2016
    }
}

```
> The above command returns JSON structured like this:
for avg:

```json
{
    "aggregations":{
        "metrics":[
            {
                "name":"x0pa",
                "value":1270,
                "dimensionsList":[
                    {
                        "value":"x0pa",
                        "dimension":"company"
                    }
                ],
                "predictions":{
                    "loyalty":{
                        "loyalty_15percent":{
                            "columnName":"loyalty_15percent",
                            "displayName":"loyalty_15percent",
                            "value":0.5239889763779527
                        }
                    }
                }
            }
        ],
        "defaultYear":2016
    }
}

```
this endpoint returns the details of a employees and stats.

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>
