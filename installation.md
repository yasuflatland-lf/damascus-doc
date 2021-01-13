---
layout: default
title: Installation
nav_order: 2
permalink: /installation.html
---
## Requirements
- Liferay 7.3 CE GA6 and higher.
- Liferay 7.2 CE GA2 and higher.
- Liferay 7.1 CE GA4 and higher.
- Liferay 7.0 CE GA7 and Liferay DXP SP3 or higher versions.
- Java 1.8 or above
- gradle 3.0 or above need to be installed
- jpm needs to be installed. (instruction to install is as follows)

---

## Installing Blade CLI

Please install [Liferay Workspace Installer](https://sourceforge.net/projects/lportal/files/Liferay%20Workspace) first.

Damascus uses JPM for it's installation and Liferay Workspace that Blade CLI generates. 

You can install Blade CLI using the Liferay Workspace installer. This installs JPM and Blade CLI into your user home folder and optionally initializes a Liferay Workspace folder.

For further steps of installation, please see [INSTALLING BLADE CLI](https://dev.liferay.com/ja/develop/tutorials/-/knowledge_base/7-1/installing-blade-cli) in the official documents.

---

## Installing Damascus

Mac
{: .label .label-green}
Open a terminal and type a command below.

```bash
curl https://raw.githubusercontent.com/yasuflatland-lf/damascus/master/installers/global | sudo sh
```

Windows
{: .label .label-blue}

1. Download [jpm](https://raw.githubusercontent.com/jpm4j/jpm4j.installers/master/dist/jpm-setup.exe) and install.
2. Install ```damascus.jar``` with ```jpm``` as follows. 

```bash
jpm install https://github.com/yasuflatland-lf/damascus/raw/master/latest/damascus.jar
```

---

## How to update Damascus

1. Run ```jpm remove damascus``` to uninstall damascus.

2. Remove all files under ```[user_name]/.damascus``` folder. If you've modified files, please change them accordingly after regenerating configurations and templates.

3. Follow How to install section to install again.

---

## What's next?
[Let's generate services!]({{ site.baseurl }}{% link docs/gettingstarted/gettingstarted.md %}){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
