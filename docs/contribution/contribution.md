---
layout: default
title: Contribution
nav_order: 9
has_children: true
permalink: /docs/contribution.html
---
## How can I compile Damascus on my own?
Clone [this repository](https://github.com/yasuflatland-lf/damascus) to your local. Please make sure you've already installed Gradle 3.0 or above and jpm.

At the root directory, run 

```bash
gradle assemble
```

then ```damascus.jar``` will be created under ```/build/libs/``` directory.

If you've already installed damascus, uninstall it first with 

```bash
jpm remove damascus
```

Then install it with 

```bash
jpm install ./damascus.jar
```

---

## How can I customize Lexer and Parser of template generation?
Damascus template generator uses ANTLR4 for the DSL. This document explains how to develop Lexer / Parser for Damascus with ANTLR4.

### Install ANTLR4

### For Mac

```bash
brew install antlr
```

### How to compile ANTLR file

```bash
gradle clean
gradle generateGrammarSource
```

It will generate the new lexer and parser from ```*.g4``` file.

### How to test if the grammar is correctly conformed?

```bash
gradle clean test
```

### How to build language

You need to repeat try and error through the process. Here is a tip of how to iterate the process

Navigate to a directory where ```*.g4``` is placed and compile it with 

```bash
antlr4 DmscSrcLexer.g4 ; antlr4 DmscSrcParser.g4 ; javac Dms*.java
```

Listeners and Visitors will be generated at the same directory.

Create the target file to be compiled, say ```test.txt```. Save including DSL tags. Say 

```xml
<dmsc:root id="test" />
```

 or 
 
 ```xml
 <dmsc:sync id="test"> any texts here </dmsc:sync>
 ```

Confirm the lexer / parser correctly compile the target file with the following command, 

```bash
grun DmscSrc document -tokens test.txt
```

The ``` file``` should be the root element in the ```*.g4```. So please replace it appropriately to your environment if you want to change the grammar for your requirements.

---

## How to debug Lexer / Parser

Eclipse's ANTLR plugin works great. Here is the how to use ANTLR plugin with Eclipse Oxygen (the latest version of Eclipse as of now). With the plugin, check Parser / Lexer process the target files correctly, then you may want to create unit tests against the generated lexer and parser later for your efficiency of debugging.

### Install ANTLR plugin

1. On the Eclipse, navigate to Help -> Eclipse Market place and search "Antlr". Install **ANTLR 4 IDE 0.3.6** (choose the latest version when you install them)
2. It'll take a while and restart Eclipse.
3. Navigate to **Window -> Show view -> others -> ANTLR 4**
4. Select both **Parse Tree** and **Syntax Diagram**
5. Open **Parse Tree**
6. Open your parser file, **DmscSrcParser.g4**
7. Double click **file** rule, then paste text to be parsed in the left pane, **DmscSrcParser::file**. The parsed block diagram will be displayed on the right pane

### When you modify Lexer
When you modify Lexer, sometimes ANTLR plugin doesn't recognize the change correctly. Then please try steps below.

Run 
```bash
gradle generateGrammarSource
gradle eclipse
```
to regenerate parser and lexer, then regenerate eclipse project file.

If it still doesn't solve the issue, run 
```bash
antlr4 DmscSrcLexer.g4 ; antlr4 DmscSrcParser.g4 ; javac Dms*.java
```
at ```*.g4``` directory (```damascus/src/main/antlr```) 

Copy generated ```*.tokens``` and ```*.interp``` files into the ```/damascus/src/main/java/com/liferay/damascus/antlr/template``` directory.

Then run 
```bash
gradle eclipse
```

then click ```file``` rule in the ```DmscSrcParser.g4``` to see if the plugin reload the file. **You may want to restart Eclipse too.**

---

## IDE settings

Damascus is including lombok library, so you need to configure annotations of lombok to be properly working and compiled on IDEs. Here are how to apply lombok to Eclipse / IntelliJ

### Eclipse

1. Download [lombok](https://projectlombok.org/download)
2. double click ```lombok.jar``` and select the directory where ```eclipse.exe``` exist
3. Run ```gradle eclipse``` at the project directory and restart IDE, and right click on the project and display context menu, and choose **gradle > Refresh gradle project**
4. Java files will be displayed properly without errors.

### IntelliJ
1. **Preferences - Plugins** and search Lombok. Install the Lombok plugin.
2. **Preferences - Build, Execution, Deployment - Compiler - Annotation Processors** and check **Enable annotation processing**

---

## Bug reports / Enhancement requests

In terms of bugs, please post Github issues or send me a PR. In terms of a Enhancement request, please post a issue. Contribution is always welcome!

