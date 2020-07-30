---
title: "Tyk Cloud User Roles"
date: 2020-04-06
menu:
  main:
    parent: "Reference Docs"
weight: 1
url: "/tyk-cloud/reference-docs/user-roles"
---

## Introduction

This page defines the different user roles within Tyk Cloud, so that you can see at a glance what each role does and manage your account accordingly.

## User Roles within Tyk Cloud

We have the following user roles defined in Tyk Cloud for your team members

* Billing Admin
* Org Admin
* Team Admin
* Team Member

## Use Case Matrix

The following table shows the scope for each user role.


| Use Case                                          | Billing Admin | Org Admin | Team Admin | Team Members |
|---------------------------------------------------|---------------|-----------|------------|--------------|
| Create a new account                              | X             |           |            |              |
| Create a new organisation                         | X             |           |            |              |
| Managing a new account                            | X             |           |            |              |
| Managing an organisation entitlement              | X             |           |            |              |
| Ability to create other billing admins            | X             |           |            |              |
| Editing organisation name                         | X             | X         |            |              |
| Create team / delete                              |               | X         |            |              |
| Future - Edit team entitlements                   |               | X         |            |              |
| Invite, delete, edit org admins and team admins   |               | X         |            |              |
| Invite, delete, edit team members                 |               | X         | X          |              |
| Create new environments                           |               | X         | X          |              |
| Delete / change environments                      |               | X         | X          |              |
| View environments                                 |               | X         | X          | X            |
| Create and delete deployments                     |               | X         | X          |              |
| View deployments                                  |               | X         | X          | X            |
| Deploy, undeploy, redeploy, restart a deployment. |               | X         | X          | X            |
| Create and manage basic SSO                       |               | X         | X          |              |
| Upload plugins to the File Server                          |               | X         | X          | X            |
| Delete plugins from File Server                        |               | X         | X          | X            |
| Viewing Analytics                                 |               | X         | X          | X            |

## Initial Tyk Cloud Account Roles

Your user who signs up for the initial Tyk Cloud account is uniquely assigned to two roles:

1. Org admin of the organisation
2. Billing admin of the account

This is the only occasion where a user can be assigned to 2 roles. So, for example, if you invite a user to be a Team Admin, that is the only role (and team) they can belong to. For a user to be invited as a Billing admin, they can't have an existing Tyk Cloud account.

{{< note success >}}
**Note**
  
This functionality may change in subsequent releases.
{{< /note >}}