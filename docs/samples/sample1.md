---
layout: default
title: Samples
nav_order: 8
has_children: true
permalink: /docs/samples/sample1.html
---
## Relation Sample
Between 2 models, Damascus generates one to many relations. The sample is as below. 

There are the ```Employee``` model and ```Position``` model. In the ```Employee``` model, position fields are where pointing the ```Position``` model. All fields of validation object are mandatory. The target model (In this case, ```Position```) need to have at least the primary key field (long) and String field to display the string in a pull-down list in Employee edit page.

```json
{
  "projectName": "Employee",
  "packageName": "com.liferay.sb.employee",
  "liferayVersion": "7.1",
  "applications": [{
      "model": "Employee",
      "title": "Employee Test",
      "web": "true",
      "asset": {
        "assetTitleFieldName": "employeeTitleName",
        "assetSummaryFieldName": "employeeSummaryName",
        "categories": "true",
        "discussion": "true",
        "ratings": "true",
        "tags": "true",
        "relatedAssets": "true",
        "fullContentFieldName": "employeefullContent",
        "workflow": "true",
        "generateActivity": "true",
        "trash": "true",
        "advancedSearch": "true",
        "exportExcel": "true"
      },
      "fieldsName": "Employees",
      "fields": [{
          "type": "com.liferay.damascus.cli.json.fields.Long",
          "primary": true,
          "name": "employeeId",
          "title": "Employee Id",
          "showFieldInView": "false",
          "required": "true"
        },
        {
          "type": "com.liferay.damascus.cli.json.fields.Varchar",
          "name": "name",
          "title": "Name",
          "length": "80",
          "showFieldInView": "true",
          "required": "true"
        },
        {
          "type": "com.liferay.damascus.cli.json.fields.Long",
          "name": "position",
          "title": "Position",
          "showFieldInView": "false",
          "required": "true",
          "validation": {
            "className": "Position",
            "fieldName": "positionId",
            "orderByField": "title"
          }
        }
      ],
      "customValue": {
        "your_own_id": "your_custom_value_for_template_here"
      }
    },
    {
      "model": "Position",
      "title": "Position Test",
      "web": "true",
      "asset": {
        "assetTitleFieldName": "positionTitleName",
        "assetSummaryFieldName": "positionSummaryName",
        "categories": "true",
        "discussion": "true",
        "ratings": "true",
        "tags": "true",
        "relatedAssets": "true",
        "fullContentFieldName": "positionfullContent",
        "workflow": "true",
        "generateActivity": "true",
        "trash": "true",
        "advancedSearch": "true",
        "exportExcel": "true"
      },
      "fieldsName": "Positions",
      "fields": [{
          "type": "com.liferay.damascus.cli.json.fields.Long",
          "primary": true,
          "name": "positionId",
          "title": "Position Id",
          "showFieldInView": "false",
          "required": "true"
        },
        {
          "type": "com.liferay.damascus.cli.json.fields.Varchar",
          "name": "title",
          "title": "Title",
          "length": "80",
          "showFieldInView": "true",
          "required": "true"
        }
      ],
      "customValue": {
        "your_own_id": "your_custom_value_for_template_here"
      }
    }
  ]
}
```