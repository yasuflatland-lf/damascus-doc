---
layout: default
title: Getting Started
nav_order: 3
has_children: true
permalink: /docs/gettingstarted.html
---

# Setup the enviroment

## Creating Liferay Workspace

Create a folder, ```lrworkspace``` and go to the directory. Open up a console and generate Liferay Workspace as follows.
```bash
mkdir lrworkspace
cd lrworkspace
blade init -v 7.1
```

It will generate a Liferay workspace under the directory. Then go to the modules directory.
```bash
cd ./lrworkspace/modules
```
## What's next?
[Let's generate a service!]({{ site.baseurl }}{% link docs/gettingstarted/step2.md %}){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }