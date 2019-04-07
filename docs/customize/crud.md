---
layout: default
title: Crud
parent: Customize
nav_order: 2
permalink: /docs/customize/crud.html
---

## How can I modify CRUD implementation?

Here is the key touch points to customize CRUD implementation. 

### Controller

```*CrudMVCActionCommand.java``` are controllers of MVC pattern. All requests goes into these classes first and call ```*LocalService``` to store data into database.

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *CrudMVCActionCommand | doProcessAction | Entry point of HTTP requests at server side |

### Service

According to Liferay best practices, all methods related to model manipulation are found in ```*LocalServiceImpl.java```. In most cases, you manipulate data via Models in these services and don't directly touch the database.  

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *LocalServiceImpl | addEntryResources | Adding permissions to the entity |
| *LocalServiceImpl | addEntry | Creating a new entity and store the record into database |
| *LocalServiceImpl | deleteEntry | Deleting a entry and remove the record into database |
| *LocalServiceImpl | updateEntry | Updating a entry and update the record in database |
| *LocalServiceImpl | moveEntryToTrash | Move an entity into trash |
| *LocalServiceImpl | restoreEntryFromTrash | Restore an entity from trash |
| *LocalServiceImpl | completeWorkflowTaskAtOnce | Complete workflow at once, whereas general workflow is separated as assignment, complete actions. |

Please see ```*LocalServiceImpl.java``` for more details. If you modify the signature of methods or add new methods, you will need to run ```gradle buildService``` to regenerate interfaces.

## How can I add pages?
Basically, once the bundles are generated, you can add pages as you want according to the basic Liferay portlet mechanism.
```*ViewMVCRenderCommand.java``` is for rendering ```view.jsp```. This is called when a portlet is displayed. 

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *ViewMVCRenderCommand | render | Rendering view.jsp |

```*CrudMVCActionCommand.java``` is called at __view / delete / update / create__ a record and ```*CrudMVCRenderCommand.java``` are for rendering after the each action. ```edit.jsp``` and ```view.jsp``` will be rendered according to the actions.

### *CrudMVCActionCommand#doProcessAction

```java
if (cmd.equals(Constants.ADD)) {
    addEntry(request, response);

} else if (cmd.equals(Constants.UPDATE)) {
    updateEntry(request, response);

} else if (cmd.equals(Constants.DELETE)) {
    deleteEntry(request, response, false);

} else if (cmd.equals(Constants.MOVE_TO_TRASH)) {
    deleteEntry(request, response, true);
}
```

## How can I implement validations?
All validations are found in ```*Validator.java``` The Validations need to be implemented manually because the requirements for validations are different depending on customers. Only basic validations are generated, so please customize them according to your requirements.

### *Validator#validateTitle

```java

    protected void validateTitle(String field) {
        //TODO : This validation needs to be implemented. Add error message key into _errors when an error occurs.
        if (!StringUtils.isNotEmpty(field)) {
            _errors.add("samplesb-title-required");
        }
    }
```


## What's next?
Let's learn more [details of search]({{ site.baseurl }}{% link docs/customize/search.md %}).
