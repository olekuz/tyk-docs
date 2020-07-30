---
date: 2020-03-17T19:13:22Z
Title: Task 4 - Create an Environment
menu:
  main:
    parent: "Getting Started with Tyk Cloud"
weight: 4
aliases:
    - /tyk-cloud/create-environment/
---

## Introduction

You can use Tyk Cloud to manage your APIs effectively and with minimal effort. To do so, you will need to create an environment that allows you to group deployments with specific purposes, which is what this page shows you how to do. 

## Step One - Name your Environment

Give your [Environment](/docs/tyk-cloud/glossary/glossary/#environment) a name. You may find it useful to reflect the names used within your organisation.

## Step Two - Name your Control Plane

Give your [Control Plane](/docs/tyk-cloud/glossary/glossary/#control-plane) a name. Again, this is up to you and you may already have an infrastructure you want to re-create in Tyk Cloud.

{{< note success >}}
**Note**
  
For this release of Tyk Cloud, you can only have one Control Plane per Environment.
{{< /note >}}

## Step Three - Configure your first Edge Gateway

1. Select the region you want to locate your [Edge Gateway](/docs/tyk-cloud/glossary/glossary/#edge) in from the drop-down list.
2. Give your Edge a name

## Step Five

Click [Deploy Control Plane and Creat an Edge Gateway](/docs/tyk-cloud/glossary/glossary/#deploy). You can watch your deployment being created. You will then be taken to the Deployments overview screen within Tyk Cloud.

Next you'll set up your first API from the Tyk Dashboard.