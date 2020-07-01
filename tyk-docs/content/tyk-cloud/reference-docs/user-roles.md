---
title: "Tyk-Cloud User Roles"
date: 2020-04-06
menu:
  main:
    parent: "Reference Docs"
weight: 1
url: "/tyk-cloud/reference-docs/user-roles"
---

## User Roles within Tyk-Cloud

We have the following user roles defined in Tyk-Cloud for your team members

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
| Apply multiple roles to a single user             |               | X         | X          |              |

