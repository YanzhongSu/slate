---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Copofi API documentation! This page introduces Copofi API endpoints for FHL calculator.

# Authentication

Copofi uses API keys to allow access to the API endpoints. You will be given an API key upon request.

# FHL Calculator
Return calculated long-term and short-term let gross of a given property.

### URL

`https://zuto2vut94.execute-api.us-east-1.amazonaws.com/beta`

### Method

`POST`

### Query Parameters

Parameter | Type | Value | Description
--------- | ---- | ----- | -----------
postcode* | Text Categorical  | 2'200 potential values  | property postcode
ppt_size* | Numerical Categorical  |  [1,2,3,4,5] | property size
ppt_value* | Numerical  |   | property value
loan_to_value* | Numerical  | (0, ppt_value*0.75] | loan to value
interest_rate* | Numerical  | (0, 0.1] | mortgage interest rate
ppt_lng_gross | Numerical  |   | long-term let monthly rent * 12 months
ppt_lng_exps_perc | Numerical | (0, 1) | long-term let expense percentage
ppt_sht_gross | Numerical  |   | short-term let monthly rent * 12 months
ppt_sht_exps_perc | Numerical | (0, 1) | short-term let expense percentage
income_tax_bra* | Numerical Categorical  | [0.2, 0.4, 0.45] | individual income tax bracket
user_name* | Text |   | user name
user_email* | Text  | E-mail format | user email
ppt_lender | Text Categorical | [Majors lenders in the UK] | property mortgage lender
time_to_refin | Datetime |   | time to refinance
ppt_mor_type | Text Categorical | [Interest only, Repayment] | property mortgage type
ppt_tenor_period | Numerical Categorical  | [2, 3, 5] | property tenor of fixed period
more | Text |    | Extra information


> This endpoint returns a JSON structured object. :

```json
{
  "ppt_value": 340000,
  "user_data": {
    "income_tax_sht": 6460,
    "ltv": 0.7,
    "total_income_lng": {
      "2017": 5406,
      "2018": 4989.5,
      "2019": 4573,
      "2020": 4156.5,
      "2021": 3740
    },
    "income_tax_lng": 6936,
    "income_tax_rlf": {
      "2017": 3332,
      "2018": 2915.5,
      "2019": 2499,
      "2020": 2082.5,
      "2021": 1666
    },
    "net_rev_sht": 24480,
    "shtVslng": 0,
    "net_rev_lng": 17340,
    "total_income_sht": {
      "2017": 9690,
      "2018": 9690,
      "2019": 9690,
      "2020": 9690,
      "2021": 9690
    }
  },
  "interest_cost": 8330
}
```

<aside class="success">
Note: parameters marked with * denotes those that are required.
</aside>

# Rent evaluation
This endpoint is to get the estimated long-term monthly rent and short-term monthly rent based on the postcode and property size(number of bedrooms)

### URL

`https://zuto2vut94.execute-api.us-east-1.amazonaws.com/beta/rentevaluation`

### Method

`GET`

### Query Parameters

Parameter | Type | Value | Description
--------- | ---- | ----- | -----------
postcode* | Text Categorical  | 2'200 potential values  | property postcode
ppt_size* | Numerical Categorical  |  [1,2,3,4,5] | property size

### URL Parameters

`None`

### This endpoint returns a JSON structured object:

```json
{
  "ppt_sht_rent": 3039,
  "ppt_lng_rent": 2435
}```

# Postcode
This endpoint retrieves all the available postcodes.

### URL

`https://zuto2vut94.execute-api.us-east-1.amazonaws.com/beta`

### Method

`GET`

### Query Parameters

`None`

### URL Parameters

`None`

> This endpoint returns a JSON structured object:

```json
{
  "postcode":
    [ "SW15",
      "CA23",
      "EX24",
      "LE17",
      ...
    ]
}```