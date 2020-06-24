---
title: "Teams & Users Admin"
date: 2020-04-21
menu:
  main:
    parent: "Tasks"
weight: 2
aliases:
    - /tyk-cloud/administration/tasks/teams-and-user-admin/"
---

## Teams Admin

### Editing an Existing Team

#### Prerequisites

The following [user roles](/docs/tyk-cloud/reference-docs/user-roles/) can perform existing Team Admin tasks:

* Org Admin - Can manage all teams in the organisation they are a member of
* Team Admin - Can only manage the team they are a member of

For an existing team, you can:

* Change the team name
* Delete the team
* Invite users to add to the team
  
#### Change the team name

1. From the Admin > Teams screen, select the team name.
2. Click **Edit**.
3. Change the existing name for the team.
4. Click **Save**.

#### Delete a team

1. From the Admin > Teams screen, select the team name
2. Click **Edit**.
3. Click **Delete Team**.
4. You'll be asked to confirm the deletion. Click **Delete Team** from the dialog box to confirm, or click **Cancel**.

#### Create a new Team

You need to be a Org Admin to create a new team.

1. From the Admin > Teams screen, click **Add Team**.
2. Enter a name for the new team that will be added to the organisation.
3. Click **Create**.

You can now invite users to your new team.

## User Admin

The following [user roles](/docs/tyk-cloud/reference-docs/user-roles/) can perform existing User Admin tasks:

* Org Admin - Can manage all users in the organisation they are a member of
* Team Admin - Can only manage the users of the team they are a member of

### Invite a new user to your team

1. From the Admin > Teams screen, select the team name.
2. Click **Invite User**.
3. Complete the form for the new user.

### Editing Existing Users

1. Select the team with the user you want to edit
2. Click the user name from the team user list
3. You can change the following details
   * Change the team they are a member of
   * Update personal details (First and Last name, Email address)
   * Change the user role assigned to them
   * Change Password
4. Click Save to update the user info

### Delete a User

1. Select the team with the user you want to edit
2. Click the user name from the team user list
3. Click **Delete**
4. You'll be asked to confirm the deletion. Click **Delete User** from the pop-up box to confirm, or click **Cancel**.

