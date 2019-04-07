---
layout: default
title: Workflow
parent: Customize
nav_order: 5
permalink: /docs/customize/workflow.html
---
## Workflow 

The workflow is initiated at creating entity. Also they are removed at deletion of entities. Most of code are found in ```*LocalServiceImpl.java```.

Also for Asian markets, quick workflow approvement functionality is pre-implemented.

## General workflow process
Workflow starts from ```WorkflowHandlerRegistryUtil.startWorkflowInstance```, inside of ```*LocalServiceImpl#startWorkflowInstance``` method.

 This method is placed in ```*LocalServiceImpl#addEntry``` , ```*LocalServiceImpl#updateEntry```

```java
WorkflowHandlerRegistryUtil.startWorkflowInstance(
    entry.getCompanyId(), entry.getGroupId(), userId,
    SampleSB.class.getName(), entry.getPrimaryKey(), entry,
    serviceContext, workflowContext);
```

When the entity is deleted, the workflow must be removed at the same time. The method is found in ```*LocalServiceImpl#deleteEntry```.

```java
workflowInstanceLinkLocalService.deleteWorkflowInstanceLink(
    entry.getCompanyId(), entry.getGroupId(),
    SampleSB.class.getName(), entry.getPrimaryKey());
```

## Quick workflow approver
In Asian markets, a user sometimes wants to approve right away, without assigning yourself first and approve. At each transition phase, pass the name of task to a method.

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *WorkflowManager | **completeWorkflowTaskAtOnce** | Entry point of assigning and processing workflow at once
| *WorkflowManager | isWorkflowEnable | Check if workflow is enabled
| *WorkflowManager | getTransitionNames | Fetching a list of transition task names
| *WorkflowManager | getWorkflowTask | Fetching a workflow task from the entity's classPK.
| *WorkflowManager | isWorkflowExist | Checking if the workflow task exists.

## What's next?
Let's learn more [details of comments]({{ site.baseurl }}{% link docs/customize/comments.md %}).
