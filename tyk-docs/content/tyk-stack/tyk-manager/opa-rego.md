---
title: Dashboard OPA rules
url: "/tyk-dashboard/opa-rules"
---

```
package dashboard_users
default request_intent = "write"
request_intent = "read" { input.request.method == "GET" }
request_intent = "read" { input.request.method == "HEAD" }
request_intent = "delete" { input.request.method == "DELETE" }
# Set of rules to define which permission required for given request intent
# read intent require at least "read" permission
intent_match("read", "read")
intent_match("read", "write")
intent_match("read", "admin")
# write intent require "write" or "admin" permission
intent_match("write", "write")
intent_match("write", "admin")
# delete intent require "write" or "admin" permission
intent_match("delete", "write")
intent_match("delete", "admin")
# Helper to check if user an admin
default is_admin = false
is_admin {
	input.user.user_permissions["IsAdmin"] == "admin"
}
# Check if request path match any of the known permissions
# input.permissions is an object passed from Tyk Dashboard containing mapping between routes (regexp) and user permissions:
#
# Exampe object:
#  "permissions": [
#        {
#            "permission": "analytics",
#            "rx": "\\/api\\/usage"
#        },
#        {
#            "permission": "analytics",
#            "rx": "\\/api\\/uptime"
#        }
#        ....
#  ]
# 
# You can extend this object with own permissions inside this script using array.concat function
#
request_permission[role] {
	perm := input.permissions[_]
	regex.match(perm.rx, input.request.path)
    role := perm.permission
}
# --------- Start "deny" rules -----------
# Deny object contains detailed reason behind rejection
default allow = false
allow { count(deny) == 0 }
deny["User is not active"] {
	not input.user.active
}
# None of the requests was matched
deny[x] {
	count(request_permission) == 0
    x := sprintf("Unknown action '%v'", [input.request.path])
}
deny[x] {
    perm := request_permission[_]
	not is_admin
	not input.user.user_permissions[perm]
    x := sprintf("Not allowed to access '%v'", [input.request.path])
}
# Deny request for non admins if intent not match, or not exists
deny[x] {
	perm := request_permission[_]
	not is_admin
    not intent_match(request_intent, input.user.user_permissions[perm])
    x := sprintf("'%v' operation is not allowed for '%v'", [request_intent, input.request.path])
}
# If "deny" rule found, disallow even for admins
deny[x] {
	perm := request_permission[_]
	is_admin
	input.user.user_permissions[perm] == "deny"
    x := sprintf("'%v' operation is denied for '%v'", [request_intent, input.request.path])
}
# Do not allow reset password on behalf of another user
deny[x] {
	request_permission[_] = "ResetPassword"
	not is_admin
    user_id := split(input.request.path, "/")[3]
    user_id != input.user.id
    x := sprintf("Not allowed to reset password for '%v' user", [user_id])
}
# Even admins can't reset if it not allowed in the global config
deny[x] {
	request_permission[_] == "ResetPassword"
	is_admin
    not input.config.allow_admin_reset_password
    not input.user.user_permissions["ResetPassword"]
    x := "Admin not allowed to reset password without explicit permission"
}
# deny[x] {
#    not input.request.header["Milan"] == ["Test1"]
#	x := "Access not allowed to user without Milan Header"
#}
# --------- End "deny" rules ----------
###############################################################################
# Demo section, to show rule capabilities.                                    #
# Rules below are not executed untill you set special permission to the user  #
###############################################################################
# If you are testing using Opa playground, you can mock Tyk functions like this:
#
# TykAPIGet(path) = {}
# TykDiff(o1,o2) = {}
#
# Use this pre-build playground https://play.openpolicyagent.org/p/T1Rcz5Ugnb
# Example of complex rule which forbirds user to change API status, if he has some custom permission
# This rule will not be executed, unless this custom permission set
deny["You are not allowed to change API status"] {
	# Custom permission which can be enabled with tyk_analytics config: `"custom_permissions":["disable_deploy"]`
	input.user.user_permissions["test_disable_deploy"]
	# Intent is to to update API
	request_permission[_] == "apis"
	request_intent == "write"
	# Lets get original API object, before update
	# TykAPIGet accepts API url as argument, e.g. to receive API object call: TykAPIGet("/api/apis/<api-id>")
	api := TykAPIGet(input.request.path)
	# TykDiff performs Object diff and returns JSON Merge Patch document https://tools.ietf.org/html/rfc7396
	# For example if only state has change diff may look like: {"state": "active"}
	diff := TykDiff(api, input.request.body)
	# API state has changed
	not is_null(diff.api_definition.active)
}
# Using patch_request helper you can modify content of the request
# You should respond with JSON merge patch. 
# See https://tools.ietf.org/html/rfc7396 for more detaills
#
# Example: Enforce http proxy configuration for an APIs with category #external. 
patch_request[x] {
	# make it work only in test environment
	# Remove if you want to enable it for all users
	input.user.user_permissions["test_patch_request"]
	request_permission[_] == "apis"
	request_intent == "write"
	contains(input.request.body.api_definition.name, "#external")
	x := {"api_definition": {"proxy": {"transport": {"proxy_url": "http://company-proxy:8080"}}}}
}
# You also have access not to user group name, so can use it in your rules.
deny["Only admins Group allowed to access this APIs"] {
	# Custom permission which can be enabled with tyk_analytics config: `"custom_permissions":["disable_deploy"]`
	input.user.user_permissions["test_admin_usergroup"]
	# Intent is to to access API
	request_permission[_] == "apis"
	api := TykAPIGet(input.request.path)
	# If this is APIs in special #admin-teamA category
	contains(input.request.body.api_definition.name, "#admin-teamA")
	not input.user.group_name == "TeamA-Admin"
}
```