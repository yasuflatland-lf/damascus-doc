---
layout: default
title: Generate Service
nav_order: 1
parent: Getting Started
permalink: /docs/gettingstarted/step2.html
---
# Generate Service

## Generate base.json
Run Damascus as follows

```bash
damascus -init Todo -p com.liferay.sb.test -v 7.1
```

Under the ```todo``` folder, ```base.json``` will be generated.

## Generate Services

Basic configrations are already configured in ```base.json``` , so let's create a service with the default configrations.

Go to ```todo``` directory and run commands as follows.

```bash
damascus -create
```

This command will create a service and a portlet as follows.

```bash
./
├── README.md
├── base.json
├── todo-api
│   ├── bnd.bnd
│   ├── build.gradle
│   └── src
│       └── main
│           └── java
│               └── com
│                   └── liferay
│                       └── sb
│                           └── test
│                               ├── constants
│                               │   └── TodoPortletKeys.java
│                               ├── exception
│                               │   ├── NoSuchTodoException.java
│                               │   ├── TodoValidateException.java
│                               │   └── TodoValidateExceptionException.java
│                               ├── model
│                               │   ├── Todo.java
│                               │   ├── TodoModel.java
│                               │   ├── TodoSoap.java
│                               │   └── TodoWrapper.java
│                               ├── service
│                               │   ├── TodoLocalService.java
│                               │   ├── TodoLocalServiceUtil.java
│                               │   ├── TodoLocalServiceWrapper.java
│                               │   └── persistence
│                               │       ├── TodoPersistence.java
│                               │       └── TodoUtil.java
│                               └── social
│                                   └── TodoActivityKeys.java
├── todo-service
│   ├── bnd.bnd
│   ├── build.gradle
│   ├── service.xml
│   └── src
│       └── main
│           ├── java
│           │   └── com
│           │       └── liferay
│           │           └── sb
│           │               └── test
│           │                   ├── model
│           │                   │   └── impl
│           │                   │       ├── TodoBaseImpl.java
│           │                   │       ├── TodoCacheModel.java
│           │                   │       ├── TodoImpl.java
│           │                   │       └── TodoModelImpl.java
│           │                   ├── service
│           │                   │   ├── base
│           │                   │   │   └── TodoLocalServiceBaseImpl.java
│           │                   │   ├── impl
│           │                   │   │   └── TodoLocalServiceImpl.java
│           │                   │   ├── permission
│           │                   │   │   ├── TodoPermissionChecker.java
│           │                   │   │   └── TodoResourcePermissionChecker.java
│           │                   │   ├── persistence
│           │                   │   │   └── impl
│           │                   │   │       └── TodoPersistenceImpl.java
│           │                   │   ├── util
│           │                   │   │   ├── ServiceProps.java
│           │                   │   │   ├── TodoIndexer.java
│           │                   │   │   └── TodoValidator.java
│           │                   │   └── workflow
│           │                   │       ├── TodoWorkflowHandler.java
│           │                   │       └── TodoWorkflowManager.java
│           │                   └── trash
│           │                       └── TodoTrashHandler.java
│           └── resources
│               ├── META-INF
│               │   ├── module-hbm.xml
│               │   ├── portlet-model-hints.xml
│               │   ├── resource-actions
│               │   │   └── default.xml
│               │   ├── spring
│               │   │   └── module-spring.xml
│               │   └── sql
│               │       ├── indexes.sql
│               │       ├── sequences.sql
│               │       └── tables.sql
│               ├── portlet.properties
│               └── service.properties
└── todo-web
    ├── bnd.bnd
    ├── build.gradle
    └── src
        └── main
            ├── java
            │   └── com
            │       └── liferay
            │           └── sb
            │               └── test
            │                   └── web
            │                       ├── asset
            │                       │   ├── TodoAssetRenderer.java
            │                       │   └── TodoAssetRendererFactory.java
            │                       ├── constants
            │                       │   └── TodoWebKeys.java
            │                       ├── portlet
            │                       │   ├── TodoAdminPortlet.java
            │                       │   ├── TodoPanelApp.java
            │                       │   ├── TodoPortletLayoutFinder.java
            │                       │   ├── TodoWebPortlet.java
            │                       │   └── action
            │                       │       ├── TodoConfiguration.java
            │                       │       ├── TodoConfigurationAction.java
            │                       │       ├── TodoCrudMVCActionCommand.java
            │                       │       ├── TodoCrudMVCRenderCommand.java
            │                       │       ├── TodoFindEntryAction.java
            │                       │       ├── TodoFindEntryHelper.java
            │                       │       └── TodoViewMVCRenderCommand.java
            │                       ├── social
            │                       │   └── TodoActivityInterpreter.java
            │                       ├── upload
            │                       │   └── TodoItemSelectorHelper.java
            │                       └── util
            │                           └── TodoViewHelper.java
            └── resources
                ├── META-INF
                │   └── resources
                │       └── todo
                │           ├── asset
                │           │   ├── abstract.jsp
                │           │   └── full_content.jsp
                │           ├── configuration.jsp
                │           ├── edit.jsp
                │           ├── edit_actions.jsp
                │           ├── init.jsp
                │           ├── search_results.jspf
                │           ├── view.jsp
                │           └── view_record.jsp
                ├── content
                │   └── Language.properties
                ├── portlet.properties
                └── resource-actions
                    └── default.xml
```

## What's next?
[Let's deploy to Liferay!]({{ site.baseurl }}{% link docs/gettingstarted/step3.md %}){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }