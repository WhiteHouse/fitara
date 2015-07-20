---
published: true
layout: default
title: FITARA Metadata Schema 
permalink: /schema/
filename: schema.md
---

#### JSON File Format

JSON is a lightweight data-exchange format that is very easy to read, parse and generate. Based on a subset of the JavaScript programming language, JSON is a text format that is optimized for data interchange. JSON is built on two structures: (1) a collection of name/value pairs and (2) an ordered list of values.

Where optional fields are included in a catalog file but are unpopulated, they may be represented by a `null` value. They should not be represented by an empty string (`""`).

The JSON schemas listed on this page are case sensitive. The schemas uses a camel case convention where the first letter of some words within a field are capitalized (usually all words but the first one). While it may seem subtle which characters are uppercase and lowercase, it is necessary to follow the exact same casing as defined in the schema documented here. For example: 

> Correct: `firstName`  
> Incorrect: `FirstName`  
> Incorrect: `firstname`  
> incorrect: `FIRSTNAME`  

Bureau IT Leadership Directory 
---------------------------------------
Each agency is expected to post a JSON file for their Bureau IT Leadership Directory to the following URL path: [agency.gov]/digitalstrategy/bureaudirectory.json

Each dataset should include one record for each agency employee with the title of “chief information officer” or who performs the duties and responsibilities of a CIO but does not necessarily have the title of “CIO.”

{: .table .table-striped}
Field Name                            | Data Type                       | Required? | Notes
--------------                        | --------------                  | ----------| --------------
**bureauCode**                        | Int (2)                         | Yes       |
**firstName**                         | String (50)                     | Yes       |
**lastName**                          | String (50)                     | Yes       |
**employmentType**                    | Select: GS, SES, SL, ST, Other  | Yes       | 
**employmentTypeOther**               | String (500)                    | No        | If employmentType "Other" is used, describe the employment type.
**typeOfAppointment**                 | Select: career, policitical     | Yes       |
**otherResponsibilities**             | String (500)                    | No        |
**evaluationRatingOfficialTitle**     | String (500)                    | Yes       |
**evaluationReviewingOfficialTitle**  | String (500)                    | No        | If a "reviewing official" is used, describe their title. 
**keyBureauCIO**                      | Select: Yes, No                 | Yes       | Indicate whether this position is designated by the agency CIO as a “key bureau CIO.” Agency CIOs must provide key bureau CIOs’ rating officials input into the agency-wide critical element(s) described in N1 of the FITARA Common Baseline.

#### Bureau IT Leadership Directory JSON Syntax Example

~~~json
{
    "leaders" : [
        {
            "bureauCode" : "12",
            "firstName" : "Jane",
            "lastName" : "Smith",
            "employmentType" : "GS",
            "typeOfAppointment" : "career",
            "otherResponsibilities": "Optional description of other responsibilities here.  Max length is 500 characters.",
            "evaluationRatingOfficialTitle" : "CIO",
            "evaluationReviewingOfficialTitle" : "Optional Reviewing Official Title here.  Max 500 characters",
            "keyBureauCIO" : "Yes"
        },
        {
            "bureauCode": "33",
            "firstName": "John",
            "lastName": "Doe",
            "employmentType": "SES",
            "typeOfAppointment": "political",
            "evaluationRatingOfficialTitle": "CFO",
            "keyBureauCIO": "No"            
        }
    ]
    
}
~~~

*[Extended Bureau IT Leadership Directory JSON Example](https://management.cio.gov/schemaexamples/bureauITLeadershipSchema.json)*

CIO Governance Board Membership List  
---------------------------------------
Each agency is expected to post a JSON file for their Bureau IT Leadership Directory to the following URL path: [agency.gov]/digitalstrategy/governanceboards.json

Include all governance boards the CIO is a member of. Agencies shall keep this list up to date at least annually beginning in April 2016.

{: .table .table-striped}
Field Name                            | Data Type                       | Required? | Notes
--------------                        | --------------                  | ----------| --------------
**governanceBoardName**               | String (100)                    | Yes       | Name of governnance board
**programCodeFPI**                    | String (7)                      | No        | Code of Program that board is related to (Federal Program Inventory), if available
**bureauCode**                        | Int (2)                         | Yes       | Bureau that board is a part of, if at bureau-level or within-bureau board. Otherwise indicate “00”
**cioInvolvementDescription**         | String (500)                    | No        | Brief description of CIO involvement

#### CIO Governance Board Membership List JSON Syntax Example 

~~~json
{
    "boards" : [
        {
            "governanceBoardName" : "Committee for Naming Oversight",
            "programCodeFPI" : "005-001",
            "bureauCode" : "12",
            "cioInvolvementDescription" : "Optional Reviewing Official Title here.  Max 500 characters",
        },
        {
            "governanceBoardName" : "Board of Boring Names",
            "bureauCode" : "10",
        }
    ]
    
}
~~~

*[Extended CIO Governance Board Membership List JSON Example](https://management.cio.gov/schemaexamples/governanceBoardSchema.json)*
