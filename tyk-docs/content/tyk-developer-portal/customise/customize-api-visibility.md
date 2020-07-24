---
date: 2020-07-24
title: Customizing API Visibility
linktitle: Customizing API Visibility
menu:
  main:
    parent: "Customise"
---

By default, any user who accesses your developer Portal will be able to view all of the published API's in the catalog.  This behavior may not be desired and you may want to have more control of what API's developers see in the catalog when access the portal.  A common use case for this is if you have internal API's that you want to publish but only want your internal developers to be able to see these in the catalog.

We'll walk through how you can use custom Page Templates to control the visibility of an internal API so it can only be seen by your internal developers.

## Prerequisites
1. You have An API created in your Dashboard.   See Create an API for more details.
2. You have a Policy created in your Dashboard that has access rights to this API
3. You have a Portal Catalog entry for this API with the name of "Internal API"
4. You have a developer account that can access your Developer Portal.


## Add a custom field to the developer profile

For this example, we'll add a custom field to the developer profile called "internal".  This flag when set to 1 indicates the developer is an internal developer, when set to 0 indicates the developer is an external developer.
Go to the Portal Management > Developers screen

![dev_profile_custom_field](/docs/img/dashboard/portal-management/dev_profile_custom_field.jpg)


This flag can also be [set programatically](https://tyk.io/docs/tyk-developer-portal/customise/custom-developer-portal/#updating-a-developer-example-adding-custom-fields).


## Modify the Portal Catalogue Template to add Show/Hide Logic

The developer portal is fully customizable via templates.  We'll add custom logic to the portal catalog template (catalogue.html) to show/hide the "Internal API" catalogbased on the value of the "internal" flag for the developer.  

Please see the customized catalogue template ​​here​: https://gist.github.com/nerdydread/1c4f2c909e33591d7c63f805e8e3698d  

We're now going to overwrite the default catalogue.html template in the 'portal/templates' directory on the Tyk Dashboard instance with the custom one.

**NOTE**: After replacing or updating a template, the Dashboard must be restarted to lead the changes.

Now the visibility of the "Internal API" is driven by the internal flag on the developer profile.


#### Developer Logged In, internal flag set to 1 (Internal API is visible)
![dev_logged_in_internal](/docs/img/dashboard/portal-management/dev_logged_in_internal.jpg)

#### Developer Logged In, internal flag set to 0 (Internal API not visible)
![dev_logged_in_external](/docs/img/dashboard/portal-management/dev_logged_in_external.jpg)

#### No User Logged In (Internal API not visible)
![no_user_logged_in](/docs/img/dashboard/portal-management/no_user_logged_in.jpg)