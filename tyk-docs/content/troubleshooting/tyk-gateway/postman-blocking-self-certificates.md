---
title: Postman Blocks Self-Signed SSL Certificates
menu:
  main:
    parent: "Tyk Gateway"
weight: 8
url: "/troubleshooting/tyk-gateway/postman-self-signed-ssl-cert"
---

### Description

If using a self-signed SSL certificate, Postman can block API calls.


### Cause

You may not have Postman configured correctly.

### Solution

From the **Postman > Preferences > Settings > General** tab, make sure that the **SSL certificate verification** option is turned **off**

![Postman SSL Setting][1]


[1]: /docs/img/dashboard/system-management/postman_ssl_cert_setting.png