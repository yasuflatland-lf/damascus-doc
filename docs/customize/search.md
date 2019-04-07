---
layout: default
title: Search
parent: Customize
nav_order: 3
permalink: /docs/customize/search.html
---

## How can I customize Search?

All search related functionalities are located in ```*Indexer.java``` according to the best practice. This document explains the key methods to tune Search for your requirements.

### Key classes and methods

| Class |  Method name | details |
| :---- | :----------- | :------ |
| *Indexer | *Indexer(Constructor) | Configuring default permissions to the entity.
| *Indexer | hasPermission | Checking permissions for the search results. 
| *Indexer | isVisible | Checking workflow status for the search results. 
| *Indexer | **doGetDocument** | Mapping indexed text / keyword to search.
| *Indexer | doGetSummary | Configuring summary to be displayed in search portlet.
| *Indexer | doReindex | Called at reindexing.
| *Indexer | reindexEntries | Configuring how to be indexed.

For more details, please see [the official document](https://dev.liferay.com/ja/develop/tutorials/-/knowledge_base/7-0/creating-a-guestbook-indexer).

## What's next?
Let's learn more [details of permission]({{ site.baseurl }}{% link docs/customize/permission.md %}).
