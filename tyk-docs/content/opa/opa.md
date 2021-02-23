---
title: "Open Policy Agent (OPA)"
date: 2021-02-23
tags: ["OPA", "Open Policy Agent"]
menu: "main"
description: "Open Policy Agent (OPA)"
weight: 80
url: "/opa"
---

Tyk support [Open Policy Agent](https://www.openpolicyagent.org/) (OPA) standard.

### Added new config fields:
| Key                             | Type       | Description                                                                                              | Example                 |
| ------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------- | ----------------------- |
| security.enable_openpolicy      | boolean    | Toggle support for OpenPolicy                                                                            | true                    |
| security.openpolicy_debug       | boolean    | Enable debugging mode, prints a lot of information to the console                                        | true                    |
| security.additional_permissions | string map | Add custom user/user_group permissions. You can use them in your rules, and they will be displayed on UI | `{"key": "human name"}` |


When Opa turned on, the majority of the security rules will be dynamically evaluate based on these rules.
Additionally, on-prem users can modify this file and define their own rules.
Moreover, using these rules you can also modify request content 🚀

To give you some inspiration here are some ideas of the rules you can implement now:

Enforce HTTP proxy option for all APIs which target URL does not point to the internal domain
Control access for individual fields. For example, do not allow change API "active" status (e.g. deploy), unless you have a specific permission set (and make new permission be available to the UI/API).
Have a user(or group) which has read access to one APIs and write to another
OpenPolicy rule engine put on top of Dashboard API, which means you can control the behavior of all APIs (except public developer portal).


### Language intro
OPA is purpose built for reasoning about information represented in structured documents. The data that your service and its users publish can be inspected and transformed using OPA’s native query language Rego.

### What is Rego?
Rego was inspired by Datalog, which is a well understood, decades old query language. Rego extends Datalog to support structured document models such as JSON.

Rego queries are assertions on data stored in OPA. These queries can be used to define policies that enumerate instances of data that violate the expected state of the system.

### Why use Rego?
Use Rego for defining policy that is easy to read and write.

Rego focuses on providing powerful support for referencing nested documents and ensuring that queries are correct and unambiguous.

Rego is declarative so policy authors can focus on what queries should return rather than how queries should be executed. These queries are simpler and more concise than the equivalent in an imperative language.

Like other applications which support declarative query languages, OPA is able to optimize queries to improve performance.

Rego supports a variety of statements and functions. And you can even use things like HTTP calls, to build a policies that depends on third-party APIs.
See more about the language itself https://www.openpolicyagent.org/docs/latest/policy-language/.


### Tyk policy primitives
The main building block which is required for controlling access is a "deny" rule, which should return a detailed error, in case of rejection. You can specify multiple deny rules, and they all will be evaluated. If none of the rules was matched, user will be allowed to access the resource.

Simple deny rule with static error message can look like:

```
deny["User is not active"] {
  not input.user.active
}
```

You can also specify a dynamic error message:

```
# None of the permissions was matched based on path
deny[x] {
  count(request_permission) == 0
  x := sprintf("Unknown action '%v'", [input.request.path])
}
```
In addition, to `deny` rules, you can also modify the requests using `patch_request`.
You should respond with a JSON merge patch format https://tools.ietf.org/html/rfc7396
For example:
```
# Example: Enforce http proxy configuration for an APIs with category #external.
patch_request[x] {
  request_permission[_] == "apis"
  request_intent == "write"
  contains(input.request.body.api_definition.name, "#external")

  x := {"api_definition": {"proxy": {"transport": {"proxy_url": "http://company-proxy:8080"}}}}
}
```


### Getting Tyk Objects
In some of the cases, you may want to write a rule, which is based on existing Tyk Object.
For example, you can write a rule for a policy API, which depends on the metadata of the API inside it.
Policy engine has access to TykAPIGet function, which essentially just does a GET call to Dashboard API.
Example:

```
api := TykAPIGet("/apis/api/12345")
contains(api.target_url, "external.com")
```

Getting changeset of current request
For requests which modify the content, you can get a changeset (e.g. difference) using `TykDiff` function, combined with `TykAPIGet` call to get original object. See example:

```
# Example of the complex rule which forbids user to change API status, if he has some custom permission
deny["You are not allowed to change API status"] {
	input.user.user_permissions["test_disable_deploy"]

	# Intent is to to update API
	request_permission[_] == "apis"
	request_intent == "write"

	# Lets get original API object, before update
	# TykAPIGet accepts API url as argument, e.g. to receive API object call: TykAPIGet("/api/apis/<api-id>")
	api := TykAPIGet(input.request.path)

	# TykDiff performs Object diff and returns JSON Merge Patch document https://tools.ietf.org/html/rfc7396
	# For example if only state has changed diff may look like: {"api_definition":{"state": "active"}}
	diff := TykDiff(api, input.request.body)

	# API state has changed
	not is_null(diff.api_definition.active)
}
```

### Developer guide
Since Opa rules are declarative, in order to test them, in the majority of the cases you can test your rules without using the dashboard, and using this pre-build Rego playground https://play.openpolicyagent.org/p/x3ila2Q8Gb
When it comes `TykAPIGet` and `TykDiff` functions, you can mock them in your tests.

In order to understand how Dashboard evaluates the rules, you can enable debugging mode by setting `security.openpolicy_debug` option, and in dashboard logs, you will see the detailed output with input and output of the rule engine. It can be useful to copy-paste dashboard log output to the Rego playground, fix issue, and validate it on the dashboard.

When you modify `dashboard.opa` file, you need to restart dashboard.
