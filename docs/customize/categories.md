---
layout: default
title: Categories / Tags / Stars
parent: Customize
nav_order: 7
permalink: /docs/customize/categories.html
---

## Categories, Tags and Stars.

Categories, Tags and Stars are functionalities of Asset Framework. You need to look at both server side and frontend side for the implementation.

To disable Categories, Tags and Stars, remove method calls below. But be careful, server side implementation is taking care of all assets, so you need to leave it unless removing all Asset Framework functionalities.

## Server side

At updating Categories, Tags and Stars. In ```*LocalServiceImpl＃updateStatus```

```java
assetEntryLocalService.updateEntry(SampleSB.class.getName(),
                                    entryId, entry.getModifiedDate(), null, true, true);

```

At updating Categories, Tags and Stars to hide because the workflow status is other than approval. In ```*LocalServiceImpl＃updateStatus```

```java
assetEntryLocalService.updateVisible(SampleSB.class.getName(),
                                        entryId, false);

```

At deleting the entity into trash. In ```*LocalServiceImpl＃updateStatus```

```java
assetEntryLocalService.deleteEntry(SampleSB.class.getName(),
                                    entry.getPrimaryKey());
```

At updating assets. In ```*LocalServiceImpl＃updateAsset```.

 You may want to remove ```*LocalServiceImpl＃updateAsset``` itself from ```*LocalServiceImpl＃addEntry``` and ```*LocalServiceImpl＃updateEntry```

```java
public void updateAsset(
    long userId, SampleSB entry, long[] assetCategoryIds,
    String[] assetTagNames, long[] assetLinkEntryIds, Double priority)
    throws PortalException {

    boolean visible = false;

    if (entry.isApproved()) {
        visible = true;
    }

    String summary = HtmlUtil.extractText(
        StringUtil.shorten(entry.getSamplesbSummaryName(), 500));

    AssetEntry assetEntry = assetEntryLocalService.updateEntry(
        userId,
        entry.getGroupId(), entry.getCreateDate(), entry.getModifiedDate(),
        SampleSB.class.getName(), entry.getPrimaryKey(), entry.getUuid(), 0,
        assetCategoryIds, assetTagNames, true, visible, null, null, null,
        null, ContentTypes.TEXT_HTML, entry.getSamplesbTitleName(), null,
        summary, null, null, 0, 0, priority);

    assetLinkLocalService.updateLinks(
        userId, assetEntry.getEntryId(),
        assetLinkEntryIds, AssetLinkConstants.TYPE_RELATED);
}
```

## JSP (Frontend)
Categories, Tags and Stars are enabled to place taglibs as below in ```edit.jsp```
If you don't use them, remove the lines below along with methods in server side.

### Categories
```html
 <aui:input name="categories" type="assetCategories" />
```

### Tags
```html
<aui:input name="tags" type="assetTags" />
```

### Stars
```html
<liferay-ui:ratings className="<%=SampleSB.class.getName()%>"
			classPK="<%=sampleSB.getPrimaryKey()%>" type="stars" />
```
