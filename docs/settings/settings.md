---
layout: default
title: Settings
nav_order: 7
has_children: true
permalink: /docs/settings.html
---
## Proxy settings
For Windows users, after you installed jpm and damascus, ```damascus.ini``` and ```jpm.ini``` are supposed to be created at the following directory.
```bash
C:\\JPM4J\\bin
```

In both ```damascus.ini``` and ```jpm.ini```, you need to write configurations according to your proxy as follows. The damascus.ini's example is as follows.

```bash
main.class=com.liferay.damascus.cli.Damascus
log.level=error
classpath.1=C:\JPM4J\repo\D846C5DB6132E1D155AA01666EA8D7DC0265E076
vmarg.1=-Dhttps.proxyHost=XXXX.proxy.co.jp <http://XXXX.proxy.co.jp>
vmarg.2=-Dhttps.proxyPort=XXXX
vmarg.3=-Dhttp.proxyHost=XXXX.proxyj.co.jp <http://XXXX.proxyj.co.jp>
vmarg.4=-Dhttp.proxyPort=XXXX
```