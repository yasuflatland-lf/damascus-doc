---
layout: default
title: Deploy to Liferay
nav_order: 2
parent: Getting Started
permalink: /docs/gettingstarted/step3.html
---
# Deploy to Liferay

## Set up Liferay
[Download Liferay 7 / DXP](https://www.liferay.com/ja/downloads) and setup [according to this document.](https://dev.liferay.com/ja/discover/deployment/-/knowledge_base/7-0/installing-liferay-on-tomcat-8)

## Start up Liferay
Assuming you've set up Liferay under ```liferay``` folder. But the default heap settings out of box is kind of small, so you may want to assign larger size in ```setenv.sh / setenv.bat``` as follows.

Mac
{: .label .label-green}

```bash
# liferay/${tomcat_dir}/bin/setenv.sh
CATALINA_OPTS="$CATALINA_OPTS -Dfile.encoding=UTF8 -Djava.net.preferIPv4Stack=true  -Dorg.apache.catalina.loader.WebappClassLoader.ENABLE_CLEAR_REFERENCES=false -Duser.timezone=GMT -Xmx4096m -XX:MaxPermSize=512m"
```

Windows
{: .label .label-blue}

```bash
# liferay/${tomcat_dir}/bin/setenv.bat
if exist "%CATALINA_HOME%/jre1.6.0_20/win" (
	if not "%JAVA_HOME%" == "" (
		set JAVA_HOME=
	)

	set "JRE_HOME=%CATALINA_HOME%/jre1.6.0_20/win"
)

set "CATALINA_OPTS=%CATALINA_OPTS% -Dfile.encoding=UTF8 -Djava.net.preferIPv4Stack=true  -Dorg.apache.catalina.loader.WebappClassLoader.ENABLE_CLEAR_REFERENCES=false -Duser.timezone=GMT -Xmx4096m -XX:MaxPermSize=512m"
```

Then, you can start up liferay as follows.

Mac
{: .label .label-green}

```bash
./catalina.sh run
```

Windows
{: .label .label-blue}

```bash
./catalina.bat run
```

## Deploy using Blade CLI
Let's go back to your project folder under Liferay Wokespace.(Assuming ```lrworkspace/modules/todo```)

And run

```bash
blade deploy
```

On the console where you started up Lifeary, the message as follows will be displayed.

```bash
2018-06-20 06:18:23.471 INFO  [Thread-42][BundleStartStopLogger:35] STARTED com.liferay.sb.test.service_1.0.0 [579]
2018-06-20 06:18:23.604 INFO  [Thread-42][BundleStartStopLogger:35] STARTED com.liferay.sb.test.web_1.0.0 [580]
2018-06-20 06:18:24.319 INFO  [Thread-42][BundleStartStopLogger:35] STARTED com.liferay.sb.test.api_1.0.0 [581]
```

All bundles are successfully deployed now! Let's see the portlet on GUI!