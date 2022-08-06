---
layout: post
title: Group Based Access Control for Azure Synapse Spark Pools
---

This article describes how to give different groups access to different spark pools within the same workspace.


The basic idea is to have

Group 1 -> Spark Pool 1 Group 2 -> Spark Pool 2

We can make use of scopes in Synapse Access Control to achieve this result.

To begin, go to Manage>Access Control in your Azure Synapse Studio.

Click +Add to add a new role assignment.

![image.png]({{ site.baseurl }}/images/20220806/1.png)

In the new role assignment pane, choose "Workspace item" under Scope. This will force the role assignment to be only limited to a workspace item such as a Spark Pool.

Under Item type, choose "Apache Spark Pool".

At the moment roles can be scoped to Apache Spark Pools, Integration Runtimes, Linked Services, or Credentials.

![image.png]({{ site.baseurl }}/images/20220806/2.png)

Under Item, pick the spark pool you would like to scope this role assignment to.

Under Role, pick Synapse Compute Operator.

Synapse Compute Operator will allow users to attach to and run code against the spark pool. It does not allow the user to manage the spark pool (eg. scale it). If you would like users to also manage the spark pool, choose Synapse Contributor.

![image.png]({{ site.baseurl }}/images/20220806/3.png)

Select the group and click Apply.

![image.png]({{ site.baseurl }}/images/20220806/4.png)

A user that belongs to the Group 1 will be able to attach and run a notebook against sp1. However, sp2 will be greyed out. If the user hovers over sp2, a message saying the user doesn't have enough permissions will pop-out.

![image.png]({{ site.baseurl }}/images/20220806/5.png)

If the user tries to perform any management task to sp1, such as scaling the compute, or disabling auto pause, an the change will fail. Note here that the Azure Synapse UI will not stop the user from trying to apply the change. However, the change will fail with a Failed to apply settings error message.

![image.png]({{ site.baseurl }}/images/20220806/6.png)

The error message can be expanded with more details describing the the user is not authorized to make the requested change.

![image.png]({{ site.baseurl }}/images/20220806/7.png)