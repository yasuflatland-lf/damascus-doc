---
layout: default
title: Template Generation
nav_order: 6
has_children: true
permalink: /docs/template_generation.html
---

# Template Generation
In a project, there are cases where you want to use your custom templates for portlets and services. This chapter explains how to generate templates and streamline the process.

## Getting Started

### Create base.json
Assuming you already have a project that you want to convert to templates. The first thing to do is creating `base.json` for the project. Please create a new folder somewhere and run `init` command as follows due to `Damascus` doesn't override an existing folder. 

```
damascus init -c [Class Name of your target project] -p [Target project's package root] -v [Target project Liferay version]
```

For example, it should be 
```
damascus init -c SampleSB -p com.liferay.sb.test -v 7.2
```

Please copy the generated `base.json` into the target project root directory. 

### Place The base.json In The Target Project
Grab the generated `base.json` and place it in the root directory of the target project. Should be as follows:

```
└── sample-sb
    ├── base.json
    ├── sample-sb-api
    ├── sample-sb-service
    └── sample-sb-web
```

Please make sure the convert rules are appropriate for your project. The sample rules are as follows:

```
"replacements" : {
  "/damacsus/ws/modules/sample-sb/sample-sb-api" : "${apiModulePath}",
  "/damacsus/ws/modules/sample-sb/sample-sb-service" : "${serviceModulePath}",
  "/damacsus/ws/modules/sample-sb/sample-sb-web" : "${webModulePath}",
  "SamplesbTitleName" : "${application.asset.assetTitleFieldName?cap_first}",
  "SamplesbSummaryName" : "${application.asset.assetSummaryFieldName?cap_first}",
  "com/liferay/sb/test" : "${packagePath}",
  "com.liferay.sb.test" : "${packageName}",
  "SampleSB" : "${capFirstModel}",
  "sampleSB" : "${uncapFirstModel}",
  "samplesb" : "${lowercaseModel}",
  "SAMPLESB" : "${uppercaseModel}",
  "sample_sb" : "${snakecaseModel}",
  "sample-sb" : "${dashcaseProjectName}",
  "Yasuyuki Takeo" : "${damascus_author}"
}
```

The left side values are strings to replace, and the right values are replacements. For the details of right side values, please refer to [valuables.ftl](https://github.com/yasuflatland-lf/damascus/blob/master/src/main/resources/templates/7.2/valuables.ftl), `Damascus` source code.

### Quick Usage of dmsc Tags

In case where you want to convert `SampleSBAssetRenderer.java`, At the top of the file, it would look like as below:

```
// <dmsc:root templateName="Portlet_XXXXWEB_AssetRenderer.java.ftl" pickup="true" />
// <dmsc:sync id="head-common" > //
// <#include "./valuables.ftl">
// <#assign createPath = "DMSC_INSERT_FULLPATH_TAG">
// </dmsc:sync> //
```

#### Overview
`Damascus` picks up files to convert if a `<dmsc:root />` tags are included. Also, another tag, `<dmsc:sync>` preserves the code inside of the bracketed area as it is both in the template file and the original file, to reduce the tedious tasks to replace and update the same area of code between templates and originals. For more detailed usage, please look at `Damascus` 's template files.

However, those `Damascus Custom Tag`s are going to cause errors as it is. Therefore, all `Damascus Custom Tag`s need to be commented out by comment blocks of the original file's language. Single line comment is preferred rather than multiple line comment block if it's available for the original file language.

Also, please add a single comment block at the end of the line. The way preserves the line breaks in the template files.

#### Root Tag
Please place `<dmsc:root>` tag at the top of the target file and **comment out by the target file's language** as above. **One root tag is required for the original file**. 

`templateName` attribute defines the template file name to be generated. `pickup` attribute defines if this file should be converted into a template file.

#### Sync Tag
`<dmsc:sync>` tag is used to preserve code inside of the tags as it is. While working on a template generation task, you frequently need to generate a template and apply the change or fix the original accordingly. For a common use-case, you might replace model fields value operation to a loop in a template. Once you convert an original file into a template, you need to maintain the discrepancy. This tag makes the process easier to keep the discrepancy in a template, and meanwhile, the original file compilable.

`id` attribute has to be unique in a template file. Multiple `<dmsc:sync>` tags can be used.

### Generate Template For The First Time
At the directory where `base.json` is placed, run command below.

```
damascus generate -model SampleSB -templatedir "[Target directory fullpath]" -insertpathtag DMSC_INSERT_FULLPATH_TAG
```

`-insertpathtag` defines a tag to be replaced for a full path of the original file is located. It could reduce the effort to populate the path for the templates manually.

In case you run `damascus generate` in the different directory where `base.json` is placed, you can specify the source root directory as below.
```
damascus generate -model SampleSB -sourcerootdir "[Source directory fullpath]" -templatedir "[Target directory fullpath]" -insertpathtag DMSC_INSERT_FULLPATH_TAG
```

After template files are generated, remove comments inside of `head-common` id dmsc tag as below:

```
// <dmsc:root templateName="Portlet_XXXXWEB_AssetRenderer.java.ftl" pickup="true" />
// <dmsc:sync id="head-common" > //
<#include "./valuables.ftl">
<#assign createPath = "DMSC_INSERT_FULLPATH_TAG">
// </dmsc:sync> //
```

Once you generate templates, you can call `generate` as follows:

```
damascus generate -model SampleSB -templatedir "[Target directory fullpath]"
```

As you see, the code where bracketed by `<dmsc:sync>` tags is preserved as it is if the template file already exists.

## Tips for Custom Template Generation

### Template building process
At the beginning of building templates, the code build may fail. It's tedious to test it manually until the code is fixed. By using the test, this experience can be improved. You may be able to add a temporal test to copy one of the tests in `CreateCommandTest.groovy,` and run
```
gradle test --tests "*CreateCommandTest.<your test name>" --info
```

### Be aware of handling XML files
An XML file does not allow a blank for the first line. It could be a cause of failing `gradle buildService` process. The typical error would be as follows:
```
org.dom4j.DocumentException: Error on line 2 of document  : "[xX][mM][lL]" is not allowed.
```

### Do not forget to have `settings.gradle`
Dependencies should be included in `settings.gradle` to avoid error during the generation process. Also in `build.gradle` of both `*-service` and `*-api`, you need to point project as `(:<project-name>-api)`

### Please do not change `service.xml` filename to other
`Damascus` treats `service.xml` 's template name as it is. So please **DO NOT CHANGE THE NAME** from `service.xml` in a template folder.