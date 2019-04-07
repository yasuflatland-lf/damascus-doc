---
layout: default
title: Comments
parent: Customize
nav_order: 6
permalink: /docs/customize/comments.html
---
## Comments 

Comments is one of functionalities of Asset Framework. You need to look at both server side and frontend side for the implementation.

To disable comments, remove method calls below.

## Server side
At deleting a comment. In ```*LocalServiceImpl＃deleteEntry```

```java
protected void deleteDiscussion(SampleSB entry) throws PortalException {
    CommentManagerUtil.deleteDiscussion(SampleSB.class.getName(),
                                        entry.getPrimaryKey());
}

```

At moving the entity into trash. In ```*LocalServiceImpl＃updateStatus```

```java
CommentManagerUtil
    .moveDiscussionToTrash(SampleSB.class.getName(), entryId);
trashEntryLocalService.addTrashEntry(userId, entry.getGroupId(),
                                        SampleSB.class.getName(), entry.getPrimaryKey(),
                                        entry.getUuid(), null, oldStatus, null, null);
```

At restoring the entity from trash In ```*LocalServiceImpl＃updateStatus```

```java
CommentManagerUtil.restoreDiscussionFromTrash(
    SampleSB.class.getName(), entryId);
```

At restoring the entity from trash.

```java
CommentManagerUtil.restoreDiscussionFromTrash(
    SampleSB.class.getName(), entryId);
```

## JSP (Frontend)
Comment is enabled to place taglibs as below in ```edit.jsp```. 

```htmlmixed
<portlet:actionURL name="invokeTaglibDiscussion" var="discussionURL" />

<liferay-ui:discussion className="<%=SampleSB.class.getName()%>"
    classPK="<%=sampleSB.getPrimaryKey()%>" formName="fm2"
    ratingsEnabled="<%=true%>" redirect="<%=currentURL%>"
    userId="<%=sampleSB.getUserId()%>" />
```

## What's next?
Let's learn more [details of categories]({{ site.baseurl }}{% link docs/customize/categories.md %}).
