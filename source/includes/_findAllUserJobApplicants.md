# Find All Users Job Applicants

gets the entire list of applicants

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get("localhost:4545/api/api/Applications/findAllUserJobApplicants");
```
### Parameters

Parameters | Type 
---------- | -----
shortlisted | boolean
jobId       |  integer
applicationId | integer
searchKey   | string
status      | string
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

returns Entire list of Job applicants