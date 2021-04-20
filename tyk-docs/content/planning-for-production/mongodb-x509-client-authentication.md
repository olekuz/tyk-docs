---
title: MongoDB X509 Client Authentication
tags: ["MongoDB", "x509"]
description: "Setting up MongoDB with X509 Client Authentication between Tyk Components"
menu:
  main:
    parent: "Redis and MongoDB"
weight: 3
url: /tyk-stack/dependencies/mongodb/x509-client-auth
---


You can use the MongoDB X509 Certificate flow to authenticate the Tyk Dashboard, Tyk Pump, and Tyk MDCB with your MongoDB install.  This is similar yet slightly different to [AWS DocumentDB setup instructions](/docs/frequently-asked-questions/how-to-connect-to-documentdb/).

## Setting Up

Before we get into the configuration, we need to understand the 2 key components

### 1. Connection Strings


A) You are required to specify a username (and password if needed) in the connection string.  [Why do you need a username at all?](https://docs.mongodb.com/manual/tutorial/configure-x509-client-authentication/)

B) We need to specify the following parameters: `?authSource=$external&authMechanism=MONGODB-X509"`

**An example of a connection string would be:**

```bash
"mongodb://CN=tyk-mongo-client,OU=TykTest@<host>:<port>/<db>?authSource=$external&authMechanism=MONGODB-X509"
```

##### Passwords
If you have to include a password, you can do it after the username via basic auth format:

```bash
"mongodb://CN=tyk-mongo-client,OU=TykTest,O=TykTest:mypassword@<host>:<port>/<db>?authSource=$external&authMechanism=MONGODB-X509"
```

##### URL Encoding Protected Characters
You have to url encode the `:` character into `%40`.   So replace any `:` in the username field into the URL encoded version.

### 2. Certificates

We have to provide two certificates to complete the X509 Client Authentication.


**CA Cert**, Should contain just the public key of the CA.

**Client Cert,** Should contain both the public and private key of the client.

# Configuration

Here's what it looks like all put together:

## Tyk Dashboard
Your tyk_analytics.conf should include these fields at the root level:

```json
{
  ...
  "storage": {
    "main": {
      "type": "mongo",
      "connection_string": "mongodb://<username>@<host>:<port>/<db>?authSource=$external&authMechanism=MONGODB-X509",
      "mongo": {
        "ssl": {
          "enabled": true,
          "ca_file": "ca.pem",
          "key_file": "client.pem",
        }
      }
    }
  }
}
```
* old configuration of MongoDB was inside root element of tyk_analytics.conf file, recently it has moved to be like this


| Config File           | Environment Variable | Type   | Examples
| ---                   | --                   | ----   | ---- |
| "connection_string"                       | TYK_DB_STORAGE_MAIN_CONNECTIONSTRING      | string | "mongodb://{username}@{host}:{port}/{db}?authSource=$external&authMechanism=MONGODB-X509" |
| "ssl"                   | TYK_DB_STORAGE_MAIN_MONGO_SSL_ENABLED      | bool | true, false |
| "ca_file"               | TYK_DB_STORAGE_MAIN_MONGO_SSL_CAFile      | string | "certificates/ca.pem" |
| "pem_keyfile"           | TYK_DB_STORAGE_MAIN_MONGO_SSL_PEMKEYFILE      | string | "certificates/key.pem" |
| "insecure_skip_verify"  | TYK_DB_STORAGE_MAIN_MONGO_SSL_INSECURESKIPVERIFY      | bool | true, false |
| "allow_invalid_hostnames" | TYK_DB_STORAGE_MAIN_MONGO_SSL_ALLOWINVALIDHOSTNAMES      | bool | true, false |
| "session_consistency"       | TYK_DB_STORAGE_MAIN_MONGO_SSL_SESSIONCONSISTENCY      | string | "strong", "eventual", or "monotonic". default is "strong" |
| "batch_size"                | TYK_DB_STORAGE_MAIN_MONGO_SSL_BATCHSIZE      | int | Default "2000", min "100" |


## Tyk Pump
There are 3 mongo pumps, `mongo`, `mongo_aggregate`, and `mongo_selective`.

In order to setup X509 certificate authentication with MongoDB, you can add the following tags to the `meta` section to each of these 3 pumps, ie:

```json
{
  ...
  "pumps": {
    "mongo": {
      "type": "mongo",
      "meta": {
        "collection_name": "tyk_analytics",
        "mongo_url": "mongodb://CN=tyk-mongo-client,OU=TykTest@<host>:<port>/<db>?authSource=$external&authMechanism=MONGODB-X509",
        "mongo_use_ssl": true,
        "mongo_ssl_ca_file": "ca.pem",
        "mongo_ssl_pem_keyfile": "client.pem"
      }
    }
  }
}
```

In addition to the other configs, these are the ones related to MongoDB:

| Config File           | Type  | Examples
| -- | -- | --
"mongo_url" | string     | "mongodb://{username}@{host}:{port}/{db}?authSource=$external&authMechanism=MONGODB-X509" |
"mongo_use_ssl" | bool | true, false |
"mongo_ssl_ca_file" | string      | "certificates/ca.pem" |
“mongo_ssl_pem_keyfile" | string     | "certificates/key.pem" |
"mongo_ssl_insecure_skip_verify" | bool     | true, false |
"mongo_ssl_allow_invalid_hostnames" | bool         | true, false |

## Tyk Sink

As of v1.8.0, you can also secure Tyk MDCB/Sink with MongoDB using X509 Certificate Authentication flow.

The config settings are exactly the same as the Tyk Dashboard steps, just nested one level deeper:

**Example Config:**
```json
{
  ...
  "analytics": {
    "mongo_url": "mongodb://CN=tyk-mongo-client,OU=TykTest@<host>:<port>/<db>?authSource=$external&authMechanism=MONGODB-X509",
    "mongo_use_ssl": true,
    "mongo_ssl_ca_file": "ca.pem",
      "mongo_ssl_pem_keyfile": "client.pem"
  }
}
```
| Config File           | Environment Variable | Type   | Examples
| ---                   | --                   | ----   | ---- |
"analytics.mongo_url" | TYK_MDCB_ANALYTICS_MongoURL | string   |  "mongodb://{username}@{host}:{port}/{db}?authSource=$external&authMechanism=MONGODB-X509"
"analytics.mongo_use_ssl" | TYK_MDCB_ANALYTICS_MongoUseSSL | bool | true, false |
"analytics.mongo_ssl_ca_file" | TYK_MDCB_ANALYTICS_MongoSSLCAFile | string |  "certificates/ca.pem" |
"analytics.mongo_ssl_pem_keyfile" | TYK_MDCB_ANALYTICS_MongoSSLPEMKeyfile | string | "certificates/key.pem" |
"analytics.mongo_ssl_insecure_skip_verify" | TYK_MDCB_ANALYTICS_MongoSSLInsecureSkipVerify | bool | true, false |
"analytics.mongo_ssl_allow_invalid_hostnames" | TYK_MDCB_ANALYTICS_MongoSSLAllowInvalidHostnames | bool  | true, false |
"analytics.mongo_session_consistency" | TYK_MDCB_ANALYTICS_MongoSessionConsistency | string |  "strong", "eventual", or "monotonic". default is "strong" |
"analytics.mongo_batch_size" |  TYK_MDCB_ANALYTICS_MongoBatchSize | int |  Default "2000", min "100" |

