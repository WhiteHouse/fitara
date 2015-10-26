---
published: true
layout: default
title: FITARA Common Baseline Publishing Schema 
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

## Bureau IT Leadership Directory 
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

*[Bureau IT Leadership Directory JSON Schema](https://management.cio.gov/schemaexamples/bureauITLeadershipSchema.json)*

## CIO Governance Board Membership List  

Each agency is expected to post a JSON file for their CIO Governance Board Membership List to the following URL path: [agency.gov]/digitalstrategy/governanceboards.json

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
            "cioInvolvementDescription" : "Optional Reviewing Official Title here.  Max 500 characters"
        },
        {
            "governanceBoardName" : "Committee of Planning",
            "bureauCode" : "10"
        }
    ]
    
}
~~~

*[CIO Governance Board Membership JSON Schema](https://management.cio.gov/schemaexamples/governanceBoardSchema.json)*

### IDC Cost Savings and Avoidance

On October 23, 2015 agency points of contact were sent their ITOR strategies already converted to JSON format. 

OMB asks agency submitters to: 

1. Check the information in the file for accuracy;  
2. Update it with any new savings strategies;  
3. Fill-out any missing information in the required “strategyId” and “ombInitiatives” fields;  
4. Fill-out the “netOrGross” field for all savings amounts, indicating whether each year’s amount is “Net” of costs (equal to gross cost savings/avoidance achieved minus implementation costs required to achieve the savings) or “Gross” (meaning, ignoring any costs of implementation); and  
5. Post your finished file on your agency’s [agency.gov]/digitalstrategy/costsavings.json  

Before the close of the IDC quarter, identifying the JSON dataset as “[Agency] IT Reform Cost Savings/Avoidance” in your Enterprise Data Inventory and Public Data Listings. Your agency should update this data on a rolling basis as savings are realized, and must ensure that the file is updated with all savings realized in a given quarter during the week prior to the IDC collection deadline.

The following resources contain helpful tools for working with JSON data format:

* [Tabular to JSON Converter](http://www.csvjson.com/csv2json): to add a new strategy to your agency’s JSON file, first ensure that all of the columns have the correct field names and are arranged in the correct order. In Microsoft Excel: highlight and copy the new cost savings and avoidance data you wish to add to your JSON file, making sure to include the column headings, and paste that data into the box on the left side of the page and click the button saying “Convert”. The right side window will show your data in a basic JSON structure. In order to conform with the schema, adjust the “amount”, “netOrGross”, and “relatedUIIs” fields as necessary to mimic the spacing, indentation, brackets, colons, and quotation markings in the sample. 

* [JSON Validator](http://jsonlint.com/): Copy and paste the contents of your updated JSON file into the window and click the “Validate” button. The tool will check whether the data is written correctly. If any brackets, quotation marks, colons, or other markings are missing from your file, these issues will be shown to you in error messages beneath the window.

* [JSON Schema Validator](http://jsonschemalint.com/draft4/): Using the link to the schema provided on this page, copy and paste the schema text into the window on the left side of the page. Then, copy and paste your valid JSON file in the window on the right. Any errors or missing information will be shown immediately in the space below your JSON file.

{: .table .table-striped}
Field Name                            | Data Type                                                                 | Required? | Notes
--------------                        | --------------                                                            | ----------| --------------
| **strategyID**                      | Int (3)                                                                   | Yes       | The unique identifier for the strategy 
| **strategyTitle**                   | String (100)                                                              | Yes       | The title of the strategy  
| **decisionDate**                    | Date (MM/DD/YYYY)                                                         | Yes       | The date the agency decided to use this strategy 
| **ombinitiative**                   | Select: Data Center, Digital Services, Commodity IT, PortfolioStat, Other | Yes       | The primary OMB initiative that categorizes this strategy
| **relatedUIIs**                     | String (200)                                                              | No        | Related investments to the strategy, identified as their Unique Investment Identifiers (UIIs) 
| **useOfSavingsAvoidance**           | String (500)                                                              | No        | Explain what the resultant savings will be used for, or how it will be repurposed 
| **amountType**                      | Select: Cost-savings, Cost-avoidance, Both                                | Yes       | Indicate whether the amounts given for each strategy are cost-savings, cost-avoidance, or both as defined in [OMB Circular A-131](https://www.whitehouse.gov/omb/circulars_a131). 
| **fy2012**                          |                                                                           |           |                                                                                 
|   *amount*                          | Numeric, 1-1000                                                           | Yes       | _Realized_ total savings for each strategy for FY12, **in MILLIONS of dollars** 
|   *netOrGross*                      | Select: Net, Gross                                                        | Yes       | Indicate whether the FY 12 amount is net of costs, or gross 
| **fy2013**                          |                                                                           |           |                                                                                 
|   *amount*                          | Numeric, 1-1000                                                           | Yes       | _Realized_ total savings for each strategy for FY13, **in MILLIONS of dollars** 
|   *netOrGross*                      | Select: Net, Gross                                                        | Yes       | Indicate whether the FY 13 amount is net of costs, or gross 
| **fy2014**                          |                                                                           |           |                                                                                 
|   *amount*                          | Numeric, 1-1000                                                           | Yes       | _Realized_ total savings for each strategy for FY14, **in MILLIONS of dollars** 
|   *netOrGross*                      | Select: Net, Gross                                                        | Yes       | Indicate whether the FY 14 amount is net of costs, or gross 
| **fy2015**                          |                                                                           |           |                                                                                 
|   *amount*                          | Numeric, 1-1000                                                           | Yes       | _Realized_ total savings for each strategy for FY15, **in MILLIONS of dollars** 
|   *netOrGross*                      | Select: Net, Gross                                                        | Yes       | Indicate whether the FY 15 amount is net of costs, or gross

#### IDC Cost Savings and Avoidance JSON Syntax Example 

~~~json
{
    "strategies": [
        {
            "strategyId": 5,
            "strategyTitle": "Blanket Purchase Agreement",
            "decisionDate": "04/12/2011",
            "ombInitiative": "PortfolioStat",
            "useOfSavingsAvoidance": "These savings will be reinvested in existing major investments, as determined by business needs.",
            "amountType": "Cost-Avoidance",
            "relatedUIIs": [
                "099-000002345",
		"099-000000123"
            ],
            "fy2012": {
                "amount": 4,
                "netOrGross": "Net"
            },
            "fy2013": {
                "amount": 2.17,
                "netOrGross": "Net"
            },
            "fy2014": {
                "amount": 5,
                "netOrGross": "Gross"
            },
            "fy2015": {
                "amount": 0.25,
                "netOrGross": "Net"
            }
        },
        {
            "strategyId": 6,
            "strategyTitle": "Document Management System (DMS)",
            "decisionDate": "12/01/2012",
            "ombInitiative": "Commodity IT",
            "amountType": "Cost-Savings",
            "fy2012": {
                "amount": 0,
                "netOrGross": "Net"
            },
            "fy2013": {
                "amount": 0.79,
                "netOrGross": "Net"
            },
            "fy2014": {
                "amount": 0.699,
                "netOrGross": "Net"
            },
            "fy2015": {
                "amount": 0.667,
                "netOrGross": "Gross"
            }
        },
        {
            "strategyId": 3,
            "strategyTitle": "Legacy System Upgrade",
            "decisionDate": "12/01/2012",
            "ombInitiative": "Digital Services",
            "useOfSavingsAvoidance": "To be determined in forthcoming review board meeting.",
            "amountType": "Cost-Avoidance",
            "relatedUIIs": [
                "099-000003000"
            ],
            "fy2012": {
                "amount": 1.2,
                "netOrGross": "Net"
            },
            "fy2013": {
                "amount": 1.2,
                "netOrGross": "Net"
            },
            "fy2014": {
                "amount": 1.2,
                "netOrGross": "Net"
            },
            "fy2015": {
                "amount": 0,
                "netOrGross": "Net"
            }
        }
    ]
}
~~~

*[IDC Cost Savings and Avoidance JSON Schema](https://management.cio.gov/schemaexamples/costSavingsAvoidanceSchema.json)*
