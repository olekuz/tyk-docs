---
date: 2020-03-17T19:13:22Z
Title: Task 5 - Add your first API
menu:
  main:
    parent: "Getting Started with Tyk-Cloud"
weight: 5
aliases:
    - /tyk-cloud/first-api/
---

You'll now setup a very basic API to demonstrate how they are managed within Tyk-Cloud.

## Prerequisites

From the **Edge Gateways** section of the Deployments screen, make a note of the Tag "edge" assigned to your Edge Gateway. You'll add this tag when creating your API.

## Step One - Access the Dashboard

From the Deployments Overview screen Click **Access Dashboard**. You'll be redirected to the Tyk Dashboard for your [Control Plane](/docs/tyk-cloud/glossary/glossary/#control-plane).

## Step Two - Add a New API

Click the APIs menu item and then click **Add New API**.

## Step Three - Core Settings

1. Give Your API a name - We'll use "my app" for the rest of this Getting Started journey
2. Scroll down to the **Target URL** setting and change the URL to http://tyk.io
3. Then scroll down to the Authentication section and select **Open(Keyless)** to keep things simple for this demo

## Step Four - Advanced Options

1. Click the **Advanced Options** tab of the API Designer.
2. Scroll down to the **Segment Tags (Node Segmentation)** setting and add the tag (edge) you saw in the Linked Stacks settings. 

## Step Five - Save Your API

Click **Save** from the API Designer. Your API will now be added to the APIs list.

Next you'll access your API from the Gateway Ingress.