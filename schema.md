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
Each agency is expected to post a JSON file for their IDC Cost Savings and Avoidance to the following URL path: [agency.gov]/digitalstrategy/CostSavingsAndAvoidance.json

**Agencies shall update this on a rolling basis and will be evaluated quarterly.** 

#### IDC Cost Savings and Avoidance JSON Syntax Example 

~~~json
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "version" : 1.0,
    "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance",
    "name": "/",
    "title": "Realized Cost Savings and Avoidance Schema version 1.0",
    "description": "Schema definition for describing the Realized Cost Savings and Avoidance data collection",
    "type": "object",
    "required": [
        "strategies"
    ],
    "properties": {
        "strategies": {
            "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies",
            "name": "strategies",
            "title": "Strategies schema",
            "description": "A list of realized cost savings and avoidance strategies for this agency",
            "type": "array",
            "minItems": 1,
            "additionalItems": false,
            "required": [
                "0"
            ],
            "items": {
                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0",
                "name": "0",
                "title": "initiative 0 schema",
                "description": "Information about a particular initiative",
                "type": "object",
                "required": [
                    "strategyId",
                    "strategyTitle",
                    "decisionDate",
                    "ombInitiative",
                    "amountType",
                    "fy2012",
                    "fy2013",
                    "fy2014",
                    "fy2015"
                ],
                "properties": {
                    "strategyId": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/strategyId",
                        "name": "stratgeyId",
                        "description": "Strategy identifier",
                        "title": "strategyId schema",
                        "type": "number",
                        "minimum": 1,
                        "maximum": 999,
                        "multipleOf": 1
                    },
                    "strategyTitle": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/strategyTitle",
                        "name": "stratgeyTitle",
                        "title": "strategyTitle schema",
                        "description": "Strategy title",
                        "type": "string",
                        "minLength" : 1,
                        "maxLength" : 100
                    },
                    "useOfSavingsAvoidance": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/useOfSavingsAvoidance",
                        "name": "useOfSavingsAvoidance",
                        "title": "useOfSavingsAvoidance schema",
                        "description": "Use of Savings Avoidance",
                        "type": "string",
                        "minLength" : 1,
                        "maxLength" : 500
                    },
                    "decisionDate": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/decisionDate",
                        "name": "regex",
                        "title": "decisionDate schema",
                        "description": "Decision date (MM/DD/YYYY format)",
                        "type": "string",
                        "pattern": "^[0-9]{2}\/[0-9]{2}\/[0-9]{4}$"
                    },
                    "ombInitiative": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/ombInitiative",
                        "name": "ombInitiative",
                        "title": "ombInitiative schema",
                        "description": "OMB Initiative (Data Center, Digital Services, Commodity IT, PortfolioStat or Other)",
                        "type": "string",
                        "enum" : ["Data Center", "Digital Services", "Commodity IT", "PortfolioStat", "Other"]
                    },
                    "amountType": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/properties/amoutType",
                        "name": "amountType",
                        "title": "amountType schema",
                        "description": "Amount Type (Cost-Savings, Cost-Avoidance or Both)",
                        "type": "string",
                        "enum" : ["Cost-Savings", "Cost-Avoidance", "Both"]
                    },
                    "relatedUIIs": {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/relatedUIIs",
                        "name": "relatedUIIs",
                        "title": "relatedUIIs schema",
                        "description": "Related UIIs",
                        "type": "array",
                        "minItems": 1,
                        "additionalItems": false,
                        "required": [
                            "0"
                        ],
                        "items": {
                            "0": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/relatedUIIs/0",
                                "name": "0",
                                "title": "relatedUIIs 0 schema",
                                "description": "Related UII",
                                "type": "string",
                                "pattern": "^[0-9]{3}-[0-9]{9}$"
                            }
                            
                        }
                    },
                    "fy2012" : {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2012",
                        "name": "fy2012",
                        "title": "fy2012 schema",
                        "description": "Fiscal Year 2012",
                        "type": "object",
                        "required": [
                            "amount",
                            "netOrGross"
                        ],
                        "properties": {
                            "amount": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2012/properties/amout",
                                "name": "amount",
                                "title": "fy2012 amount schema",
                                "description": "Fiscal Year 2012 Amount",
                                "type": "number",
                                "minimum": 0,
                                "maximum": 1000
                            },
                            "netOrGross": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2012/netOrGross",
                                "name": "amount",
                                "title": "fy2012 netOrGross schema",
                                "description": "Fiscal Year 2012 Amount Type (Net or Gross)",
                                "type": "string",
                                "enum" : ["Net", "Gross"]                                
                            }
                        }
                    },
                    "fy2013" : {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2013",
                        "name": "fy2013",
                        "title": "fy2013 schema",
                        "description": "Fiscal Year 2013",
                        "type": "object",
                        "required": [
                            "amount",
                            "netOrGross"
                        ],
                        "properties": {
                            "amount": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2013/properties/amout",
                                "name": "amount",
                                "title": "fy2013 amount schema",
                                "description": "Fiscal Year 2013 Amount",
                                "type": "number",
                                "minimum": 0,
                                "maximum": 1000
                            },
                            "netOrGross": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2013/netOrGross",
                                "name": "amount",
                                "title": "fy2013 netOrGross schema",
                                "description": "Fiscal Year 2013 Amount Type (Net or Gross)",
                                "type": "string",
                                "enum" : ["Net", "Gross"]                                
                            }
                        }
                    },
                    "fy2014" : {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2014",
                        "name": "fy2014",
                        "title": "fy2014 schema",
                        "description": "Fiscal Year 2014",
                        "type": "object",
                        "required": [
                            "amount",
                            "netOrGross"
                        ],
                        "properties": {
                            "amount": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2014/properties/amout",
                                "name": "amount",
                                "title": "fy2014 amount schema",
                                "description": "Fiscal Year 2014 Amount",
                                "type": "number",
                                "minimum": 0,
                                "maximum": 1000
                            },
                            "netOrGross": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2014/netOrGross",
                                "name": "amount",
                                "title": "fy2014 netOrGross schema",
                                "description": "Fiscal Year 2014 Amount Type (Net or Gross)",
                                "type": "string",
                                "enum" : ["Net", "Gross"]                                
                            }
                        }
                    },
                    "fy2015" : {
                        "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2015",
                        "name": "fy2015",
                        "title": "fy2015 schema",
                        "description": "Fiscal Year 2015",
                        "type": "object",
                        "required": [
                            "amount",
                            "netOrGross"
                        ],
                        "properties": {
                            "amount": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2015/properties/amout",
                                "name": "amount",
                                "title": "fy2015 amount schema",
                                "description": "Fiscal Year 2015 Amount",
                                "type": "number",
                                "minimum": 0,
                                "maximum": 1000
                            },
                            "netOrGross": {
                                "id": "https://omb.max.gov/schemas/CostSavingsAndAvoidance/strategies/0/fy2015/netOrGross",
                                "name": "amount",
                                "title": "fy2015 netOrGross schema",
                                "description": "Fiscal Year 2015 Amount Type (Net or Gross)",
                                "type": "string",
                                "enum" : ["Net", "Gross"]                                
                            }
                        }
                    }
                }
            }
        }
    }
}


~~~
