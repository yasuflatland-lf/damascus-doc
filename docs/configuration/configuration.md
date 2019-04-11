---
layout: default
title: Configuration
nav_order: 4
has_children: true
permalink: /docs/configuration.html
---
# Configuration
This page explains how to configure ```base.json``` for scaffoldings. When you run ```damascus -init```, damascus creates the template of ```base.json``` file.

Some of the fields have not been enabled because they've not been implemented yet. Invalid fields are tagged *TBI* (To be implemented) in this document.

## Root elements
These values are defined once in ```base.json```.

| value | details |
| :---- | :------ |
| projectName | Project name. Damascus will create a folder based on this name. The name should be CamelCase, "**Todo**",  "**Event**" , e.g. |
| packageName | The package name of this project. |
| liferay Version | This is taken from the field of ```-v``` in ```damascus -init``` command. ```70``` means Liferay 7.0 / DXP. The default as of 2017 June is ```70```. This will be always the latest version in the future when a new version of Liferay is released. |
| applications | This field contains ```1...N``` numbers of application element, which represent each model of ```service.xml``` of Service. For more details of ```service.xml```, please see [SERVICE BUILDER](https://dev.liferay.com/develop/tutorials/-/knowledge_base/7-0/service-builder) |

---

## Application element
As explained in Root element, application element represent a model of ```service.xml```. 

| value | details |
| :---- | :------ |
| model | The model name of this application. It has to be camel case.
| title | The title of this application. This field will be used in bnd.bnd file and ```*-web``` portlet title.
| web (TBI) | When it's true, *-web project (portlet) will be created. For now, *-web is always created.
| Asset element | Assets configurations. 
| fieldsName (TBI) | |
| fields | Details are below. |
| customValue | Customize values by an array that you want to use in templates. |

---

## Fields
Each field in a model.

### Long
Long value field

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.Long``` |
| primary | true if this field is primary key |
| name | This field name. This will be also used as a field name for ```service.xml```  |
| title | Title of this field. This is used as a title for a list in a view. |
| showFieldInView | (TBI) displayed in a view if it's true. For now, this field is ignored and always created. |
| required | Required validation will be created if it's true |
| validation | Relation with a model.

### Validation
Relation with a model. The associated model data will be displayed as a pulldown. If the association is incorrect, Damascus throws an exception.

| value | details |
| :---- | :------ |
| className | The target model class name. |
| fieldName | The target model's field name.  |
| orderByField | The target model's field name to be used for sorting the records. |

### Varchar
This will generate a text field.

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.Varchar```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.
| length | Field length. This value will be stored in ```portlet-model-hints.xml```
| showFieldInView | (TBI) displayed in a view if it's true. For now, this field is ignored and always created.
| required | Required validation will be created if it's true

### Boolean
This will generate a boolean field

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.Boolean```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

### DateTime
This will generate DateTime field

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.DateTime```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

### DocumentLibrary
This will generate a field + button to display Document & Library upload popup. 

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.DocumentLibrary```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

### Double
This will generate a field for Double value. 

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.Double```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

### Integer
This will generate a field for Integer value. 

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.Integer```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

### RichText
This will generate a rich text editor field for text.

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.RichText```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

### Text
This will generate a text area field.

| value | details |
| :---- | :------ |
| type | Field type. ```com.liferay.damascus.cli.json.fields.Text```
| name | This field name. This will be also used as a field name for ```service.xml```
| title | Title of this field. This is used as a title for a list in a view.

---

## Asset element
Elements required for assets. Search, Comments, Rating, Activities, Related assets, and trash are all relying on assets framework.

| value | details |
| :---- | :------ |
| assetTitleFieldName | Title name for the assets.
| assetSummaryFieldName | Summary name for the assets
| categories | This generates category field in the Edit page. The default value is `false`.
| discussion | This generates comment section in the Edit page. The default value is `false`.
| ratings | This generates rating section in the Edit page. The default value is `false`.
| tags | This generates tags section in the Edit page. The default value is `false`.
| relatedAssets | This generates related assets section in the Edit page. The default value is `false`.
| fullContentFieldName  | Full contents field for an assets.
| workflow (TBI) | This field enables workflow. For now, this is always true and workflow is always enabled.
| generateActivity | This field enables activity for the activity portlet. The default value is `false`.
| trash (TBI) | This field enables trash (logical deletion). For now, this is always true and trash is always enabled.
