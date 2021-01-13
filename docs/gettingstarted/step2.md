---
layout: default
title: Generate Service
nav_order: 1
parent: Getting Started
permalink: /docs/gettingstarted/step2.html
---
# Generate Service

Let's navigate to the modules directory.
```bash
cd ./lrworkspace/modules
```

## Generate base.json
Run Damascus as follows

```bash
damascus init -c Todo -p com.liferay.sb.test -v 7.3
```

Under the ```todo``` folder, ```base.json``` will be generated.

## Generate Services

Basic configrations are already configured in ```base.json``` , so let's create a service with the default configrations.

Go to ```todo``` directory and run commands as follows.

```bash
damascus create
```

This command will create a service and a portlet as follows.

```bash
.
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
│                               │   ├── TodoConstants.java
│                               │   └── TodoPortletKeys.java
│                               ├── exception
│                               │   ├── NoSuchTodoException.java
│                               │   └── TodoValidateException.java
│                               ├── model
│                               │   ├── Todo.java
│                               │   ├── TodoModel.java
│                               │   ├── TodoSoap.java
│                               │   └── TodoWrapper.java
│                               └── service
│                                   ├── TodoLocalService.java
│                                   ├── TodoLocalServiceUtil.java
│                                   ├── TodoLocalServiceWrapper.java
│                                   ├── TodoService.java
│                                   ├── TodoServiceUtil.java
│                                   ├── TodoServiceWrapper.java
│                                   └── persistence
│                                       ├── TodoPersistence.java
│                                       └── TodoUtil.java
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
│           │                   ├── internal
│           │                   │   ├── search
│           │                   │   │   ├── TodoSearchRegistrar.java
│           │                   │   │   ├── TodoSearcher.java
│           │                   │   │   ├── index
│           │                   │   │   │   └── contributor
│           │                   │   │   │       ├── TodoModelDocumentContributor.java
│           │                   │   │   │       └── TodoModelIndexerWriterContributor.java
│           │                   │   │   ├── query
│           │                   │   │   │   └── contributor
│           │                   │   │   │       ├── TodoKeywordQueryContributor.java
│           │                   │   │   │       └── TodoModelPreFilterContributor.java
│           │                   │   │   └── result
│           │                   │   │       └── contributor
│           │                   │   │           ├── TodoModelSummaryContributor.java
│           │                   │   │           └── TodoModelVisibilityContributor.java
│           │                   │   ├── security
│           │                   │   │   └── permission
│           │                   │   │       └── resource
│           │                   │   │           ├── TodoModelResourcePermissionRegistrar.java
│           │                   │   │           └── TodoPortletResourcePermissionRegistrar.java
│           │                   │   └── trash
│           │                   │       └── TodoTrashHandler.java
│           │                   ├── model
│           │                   │   └── impl
│           │                   │       ├── TodoBaseImpl.java
│           │                   │       ├── TodoCacheModel.java
│           │                   │       ├── TodoImpl.java
│           │                   │       └── TodoModelImpl.java
│           │                   └── service
│           │                       ├── base
│           │                       │   ├── TodoLocalServiceBaseImpl.java
│           │                       │   └── TodoServiceBaseImpl.java
│           │                       ├── http
│           │                       │   ├── TodoServiceHttp.java
│           │                       │   └── TodoServiceSoap.java
│           │                       ├── impl
│           │                       │   ├── TodoLocalServiceImpl.java
│           │                       │   └── TodoServiceImpl.java
│           │                       ├── persistence
│           │                       │   └── impl
│           │                       │       ├── TodoPersistenceImpl.java
│           │                       │       └── constants
│           │                       │           └── TodoPersistenceConstants.java
│           │                       ├── util
│           │                       │   └── TodoValidator.java
│           │                       └── workflow
│           │                           ├── TodoWorkflowHandler.java
│           │                           └── TodoWorkflowManager.java
│           └── resources
│               ├── META-INF
│               │   ├── module-hbm.xml
│               │   ├── portlet-model-hints.xml
│               │   ├── resource-actions
│               │   │   └── default.xml
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
            │                       ├── info
            │                       │   └── display
            │                       │       └── contributor
            │                       │           └── TodoAssetInfoDisplayContributor.java
            │                       ├── internal
            │                       │   ├── display
            │                       │   │   └── context
            │                       │   │       ├── TodoDisplayContext.java
            │                       │   │       └── TodoManagementToolbarDisplayContext.java
            │                       │   └── security
            │                       │       └── permission
            │                       │           └── resource
            │                       │               ├── TodoEntryPermission.java
            │                       │               └── TodoPermission.java
            │                       ├── portlet
            │                       │   ├── TodoAdminPortlet.java
            │                       │   ├── TodoAdminPortletProvider.java
            │                       │   ├── TodoLayoutFinder.java
            │                       │   ├── TodoPanelApp.java
            │                       │   ├── TodoPortlet.java
            │                       │   ├── TodoPortletProvider.java
            │                       │   ├── action
            │                       │   │   ├── TodoAdminCrudMVCActionCommand.java
            │                       │   │   ├── TodoAdminCrudMVCRenderCommand.java
            │                       │   │   ├── TodoAdminViewMVCRenderCommand.java
            │                       │   │   ├── TodoConfiguration.java
            │                       │   │   ├── TodoConfigurationAction.java
            │                       │   │   ├── TodoCrudMVCActionCommand.java
            │                       │   │   ├── TodoCrudMVCRenderCommand.java
            │                       │   │   ├── TodoExportMVCResourceCommand.java
            │                       │   │   ├── TodoPortletLayoutFinder.java
            │                       │   │   └── TodoViewMVCRenderCommand.java
            │                       │   └── route
            │                       │       └── TodoFriendlyURLMapper.java
            │                       ├── upload
            │                       │   └── TodoItemSelectorHelper.java
            │                       └── util
            │                           └── TodoViewHelper.java
            └── resources
                ├── META-INF
                │   ├── friendly-url-routes
                │   │   └── routes.xml
                │   └── resources
                │       ├── todo
                │       │   ├── asset
                │       │   │   ├── abstract.jsp
                │       │   │   ├── full_content.jsp
                │       │   │   └── preview.jsp
                │       │   ├── configuration.jsp
                │       │   ├── css
                │       │   │   └── main.css
                │       │   ├── edit.jsp
                │       │   ├── edit_actions.jsp
                │       │   ├── init.jsp
                │       │   ├── view.jsp
                │       │   └── view_record.jsp
                │       └── todo_admin
                │           ├── asset
                │           │   ├── abstract.jsp
                │           │   └── full_content.jsp
                │           ├── css
                │           │   └── main.css
                │           ├── edit.jsp
                │           ├── edit_actions.jsp
                │           ├── init.jsp
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