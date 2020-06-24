---
date: 2020-03-17T19:13:22Z
Title: Task 7 - Add Another Edge Gateway
menu:
  main:
    parent: "Getting Started with Tyk-Cloud"
weight: 7
aliases:
    - /tyk-cloud/new-edge-gateway/
---

You'll now create a new Edge Gateway.


## Step One - Add a New Edge

From the Edge Gateway section of the Tyk-Cloud Deployments screen, click Add Edge.

## Step Two - Complete the Deployment details

You need to configure your new deployment with the following information:

* Give your deployment a **Name**
* Select a **Location** for your Edge Gateway to be located in
* Select the **Type** of deployment (for this task, select Edge)
* Select the **Team** you want to manage the deployment
* Select the **Environment** you want to add the Edge to. Select the The Environment you added in [Task 4](/docs/tyk-cloud/getting-started-tyk-cloud/setup-environment/#step-one---name-your-environment).
* Select the Control Plane you want to add the Edge to. Select the Control Plane name you added in [Task 4](/docs/tyk-cloud/getting-started-tyk-cloud/setup-environment/#step-two---name-your-control-plane).
* Select the **Bundle Channel** you want to use. Select **Stable** for this demo.
* Select the **Bundle Version** you want to use. You can select a Tyk Gateway version from the drop-down list. Select the latest version.

## Step Three - Deploy your new Deployment

Click **Create and Deploy**. You will taken to the Deployments screen.

## Step Four - View your new Deployment

From your new deployment, click the **Actions** drop-down and select **View Deployment**. You will be re-directed to the URL for your new Edge Gateway.

## Step Five - Test your API from the new Edge Gateway

 Add `/my-app/` to the end of the URL. You should be taken to https://tyk.io as in [Task 6](/docs/tyk-cloud/getting-started-tyk-cloud/test-api/#step-two---append-the-url-with-your-api)

Next you will view the analytics for your API in the Dashboard.