# openform-specs (DRAFT 0.1)

A description langage for forms that can be extended for specific forms (like administrative form)

## Example 
```
---
version: 0.1-draft
title: My Awesome Service Survey
description: I want your feeling about my service
langage: en
items: 
  - id: A1
    title: Did you like my service ?
    description: Every anwsers except no is accepted !
    type: boolean
    required: true
  - id: A2
    title: How much did you liked my service ?
    type: rating      
  - id: A3
    title: What's the best choice to describe my service ?
    type: multiple-choices
    attributes:
       choices:
         - id: A3-AWESOME
           label: It's awesome
         - id: A3-MORE
           label: It's more than awesome
         - id: A3-NO-WORD
           label: They is no word to describe it
       allow-other-choice: true
  - id: A4
    title: When did you tried my service ?
    type: date
  - id: A5
    title: Feel free to describe the awesomeness of my service !
    type: text
    required: true
  - id: A6
    type: page
    title: Complementary questions
    description: 
  - id: B1
    type: file
    title: Can you send my a cat picture for my collection ?
    required: true
  - id: B2 
    type: rating
    title: Can you confirm how much you like my service ?
    description: 10 out of 10 stars is the only acceptable answer
    attributes:
      steps: 10
  - id: B3
    type: text
    title: What's your company french registration number ?
    extention-admin:
       type: siret
    
```

## Available types
- boolean
  - attributes:
      true-label: text # default : "Yes" in the user langage
      false-label: test # Default : "No" in the user langage
- text
  - attributes:
      multiple-lines-allowed: boolean # default : false
- date
  - attributes:
      ask-time: boolean # default : false
- multiple-choices
  - attributes : 
      allow-multiple-selection: boolean # default : false
      allow-other-choice: boolean # default : false
- file
- email
- number
  - attributes : 
      min-value: number # default: 0
      max-value: number # default: 9 999 999 
- phone-number 
- rating
   - attributes: 
       steps: number # default : 5
- grid
   - attributes: 
       rows
       colums

## Questions
- How to manage select, checkbox and radio button ? (Should we simplify)
- We can base our description) on https://json-schema.org/ (as a superset)

## Tools that can be useful to develop
- Transform a openform description to a beautiful html form
- Transform Google Form,Typeform description to openform description (for export/import feature)
- Backend that store data from an openform generated html form in a table in a SQL database
- Generate the https://json-schema.org/ associated

## Already existing formats

- HTML Form : https://www.w3.org/TR/html401/interact/forms.html
- Extensible Forms Description Language (XFDL) 4.0
 https://www.w3.org/TR/1998/NOTE-XFDL-19980902
- Typeform https://developer.typeform.com/create/reference/retrieve-form/
- Google Form : https://developers.google.com/apps-script/reference/forms/
- Zof typecheck  https://github.com/colinhacks/zod
