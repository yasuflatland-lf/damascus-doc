---
layout: default
title: Getting Started
nav_order: 3
has_children: true
permalink: /docs/gettingstarted.html
---

# Setup the Environment

## Creating Liferay Workspace

Create a folder, ```lrworkspace``` and go to the directory. Open up a console and generate Liferay Workspace as follows.
```bash
mkdir lrworkspace
cd lrworkspace
blade init -v 7.3
```

## Configure the `gradle-local.properties`
Navigate to the created directory.
```bash
cd ./lrworkspace
```
Then create `gradle-local.properties`. Assuming you are using Liferay 7.3 GA6, set as below. Also replace `/your/bundle/root/path/here!` for `liferay.workspace.home.dir` property. 

```bash
liferay.workspace.target.platform.version=7.3.5
liferay.workspace.home.dir=/your/bundle/root/path/here!
target.platform.index.sources=true
```

Liferay now leverages Target Platform to resolve dependencies of libraries in `build.gradle`. For more details, please see links below:

- [Managing the Target Platform](https://help.liferay.com/hc/en-us/articles/360028834252-Managing-the-Target-Platform)
- [Liferay CE's BOMs](https://repository.liferay.com/nexus/index.html#nexus-search;quick~release.portal.bom)
- [Liferay DXP's BOMs](https://repository.liferay.com/nexus/index.html#nexus-search;quick~release.dxp.bom)

## What's next?
[Let's generate a service!]({{ site.baseurl }}{% link docs/gettingstarted/step2.md %}){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }