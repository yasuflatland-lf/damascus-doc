---
layout: default
title: Permission
parent: Customize
nav_order: 4
permalink: /docs/customize/permission.html
---
## Permission implementations 

Permissions checking is implimented in these 2 classes, ```*PermissionChecker``` for model layer permission checking and ```*ResourcePermissionChecker``` for portlet layer permission checking.

The combinations of permissions assigned to roles are defined in ```default.xml```
This file is located at,

```bash
*-service/src/main/resources/META-INF/resource-actions/default.xml
```

Please see [the official document](https://dev.liferay.com/ja/develop/tutorials/-/knowledge_base/7-0/configuring-your-permissions-scheme) for more details.

## PermissionChecker
PermissionChecker is responsible to check permissions at model layer.

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *PermissionChecker | check | Entry point of checking permissions. Call these methods in other code
| *PermissionChecker | contains | Methods where actually check the permissions.

## ResourcePermissionChecker
ResourcePermissionChecker is responsible to check permissions at portlet level.

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *ResourcePermissionChecker | check | Entry point of checking permissions. Call these methods in other code
| *ResourcePermissionChecker | checkResource | Entry point of checking permissions. Call these methods in other code
| *PermissionChecker | contains | Methods where actually check the permissions.

## Usage in jsp files
The permission checkers are used as follows

```html
<c:if test="<%= SampleSBResourcePermissionChecker.contains(permissionChecker, themeDisplay.getScopeGroupId(), ActionKeys.ADD_ENTRY) %>">
```

## Usage in java files
The permission checkers are used as follows

```java
@Override
public boolean hasPermission(
    PermissionChecker permissionChecker, String entryClassName,
    long entryClassPK, String actionId) throws Exception {

    return SampleSBPermissionChecker.contains(
        permissionChecker, entryClassPK, actionId);
}
```

## What's next?
Let's learn more [details of workflow]({{ site.baseurl }}{% link docs/customize/workflow.md %}).
