---
---

**[hostname](#hostname)**
Environment Variable: **TYK_GW_HOSTNAME**
Type: `string`

Force gateway to work only on a specifc domain name. Can be overriden by API custom domain.


**[listen_address](#listen_address)**
Environment Variable: **TYK_GW_LISTENADDRESS**
Type: `string`

If your machine has mulitple network devices or IPs you can force Gateway to use IP address you need


**[listen_port](#listen_port)**
Environment Variable: **TYK_GW_LISTENPORT**
Type: `int`

Setting this value will change the port that Tyk listens on. Default: 8080.


**[control_api_hostname](#control_api_hostname)**
Environment Variable: **TYK_GW_CONTROLAPIHOSTNAME**
Type: `string`

Custom hostname for the Control API


**[control_api_port](#control_api_port)**
Environment Variable: **TYK_GW_CONTROLAPIPORT**
Type: `int`

Set to run Gateway Control API on separate port, and protect it behind a firewall if needed. Please make sure you follow instructions when setting the control port https://tyk.io/docs/planning-for-production/#change-your-control-port.


**[secret](#secret)**
Environment Variable: **TYK_GW_SECRET**
Type: `string`

This should be changed as soon as Tyk is installed on the system. 
This value is used in every interaction with the Tyk REST API, it should be passed along as the X-Tyk-Authorization header in any requests made.
Tyk assumes that you are sensible enough not to expose the management endpoints to the public and to keep this configuration value to yourself.


**[node_secret](#node_secret)**
Environment Variable: **TYK_GW_NODESECRET**
Type: `string`

The shared secret between the Gateway and the Dashboard to ensure that API Definition downloads, heartbeat and Policy loads are from a valid source.


**[pid_file_location](#pid_file_location)**
Environment Variable: **TYK_GW_PIDFILELOCATION**
Type: `string`

Linux PID file location. Do not change until you know what you are doing. Default: /var/run/tyk/tyk-gateway.pid


**[allow_insecure_configs](#allow_insecure_configs)**
Environment Variable: **TYK_GW_ALLOWINSECURECONFIGS**
Type: `bool`

Can be set to disable Dashboard message signature verification. When set to `true`, `public_key_path` can be ignored.


**[public_key_path](#public_key_path)**
Environment Variable: **TYK_GW_PUBLICKEYPATH**
Type: `string`

While communicating with the Dashboard, by default, all the messages are signed by a private/public key pair. Set path to public key.


**[allow_remote_config](#allow_remote_config)**
Environment Variable: **TYK_GW_ALLOWREMOTECONFIG**
Type: `bool`

Allow Dashboard to remotely set Gateway configuration via Nodes screen. 


**[security](#security)**
Global Certificate configuration


**[security.private_certificate_encoding_secret](#security.private_certificate_encoding_secret)**
Environment Variable: **TYK_GW_SECURITY_PRIVATECERTIFICATEENCODINGSECRET**
Type: `string`

Set AES256 secret which is used to encode certificate private keys when they uploaded via certificate storage


**[security.control_api_use_mutual_tls](#security.control_api_use_mutual_tls)**
Environment Variable: **TYK_GW_SECURITY_CONTROLAPIUSEMUTUALTLS**
Type: `bool`

Enable Gateway Control API to use Mutual TLS. Certificates can be set via `security.certificates.control_api` section


**[security.pinned_public_keys](#security.pinned_public_keys)**
Environment Variable: **TYK_GW_SECURITY_PINNEDPUBLICKEYS**
Type: `map[string]string`

Specify public keys used for Certificate Pinning on global level. 


**[security.certificates.upstream](#security.certificates.upstream)**
Environment Variable: **TYK_GW_SECURITY_CERTIFICATES_UPSTREAM**
Type: `map[string]string`

Specify upstream mutual TLS certificates on global level in the following format: { "<host>": "<cert>" }


**[security.certificates.control_api](#security.certificates.control_api)**
Environment Variable: **TYK_GW_SECURITY_CERTIFICATES_CONTROLAPI**
Type: `[]string`

Certificates used for Control API Mutual TLS


**[security.certificates.dashboard_api](#security.certificates.dashboard_api)**
Environment Variable: **TYK_GW_SECURITY_CERTIFICATES_DASHBOARD**
Type: `[]string`

Used for communicating with the Dashboard if it is configured to use Mutual TLS


**[security.certificates.mdcb_api](#security.certificates.mdcb_api)**
Environment Variable: **TYK_GW_SECURITY_CERTIFICATES_MDCB**
Type: `[]string`

Certificates used for MDCB Mutual TLS 


**[http_server_options](#http_server_options)**
Gateway HTTP server configuration


**[http_server_options.read_timeout](#http_server_options.read_timeout)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_READTIMEOUT**
Type: `int`

User -> Gateway network read timeout


**[http_server_options.write_timeout](#http_server_options.write_timeout)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_WRITETIMEOUT**
Type: `int`

User -> Gateway network write timeout


**[http_server_options.use_ssl](#http_server_options.use_ssl)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_USESSL**
Type: `bool`

Set to true to enable SSL connections


**[http_server_options.use_ssl_le](#http_server_options.use_ssl_le)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_USELE_SSL**
Type: `bool`

Enable lets-encrypt support


**[http_server_options.enable_http2](#http_server_options.enable_http2)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_ENABLEHTTP2**
Type: `bool`

Enable HTTP2 protocol handling


**[http_server_options.ssl_insecure_skip_verify](#http_server_options.ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_SSLINSECURESKIPVERIFY**
Type: `bool`

Disable TLS verification. Required if you are using self-signed certificates.


**[http_server_options.enable_websockets](#http_server_options.enable_websockets)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_ENABLEWEBSOCKETS**
Type: `bool`

Enabled websockets and server side events support


**[http_server_options.certificates](#http_server_options.certificates)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_CERTIFICATES**
Type: `[]CertData`

Deprecated. SSL certificates used by Gateway server. 


**[http_server_options.ssl_certificates](#http_server_options.ssl_certificates)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_SSLCERTIFICATES**
Type: `[]string`

SSL certificates used by Gateway server. List of certificate IDs or path to files.


**[http_server_options.server_name](#http_server_options.server_name)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_SERVERNAME**
Type: `string`

Start Gateway HTTP server on specific server name


**[http_server_options.min_version](#http_server_options.min_version)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_MINVERSION**
Type: `uint16`

Minimum TLS version. Possible values: https://tyk.io/docs/basic-config-and-security/security/tls-and-ssl/#values-for-tls-versions


**[http_server_options.max_version](#http_server_options.max_version)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_MAXVERSION**
Type: `uint16`

Maximum TLS version. 


**[http_server_options.flush_interval](#http_server_options.flush_interval)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_FLUSHINTERVAL**
Type: `int`

Set this to the number of seconds that Tyk should use to flush content from the proxied upstream connection to the open downstream connection. 
This option needed be set streaming protocols like Server Side Events, or gRPC streaming.


**[http_server_options.skip_url_cleaning](#http_server_options.skip_url_cleaning)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_SKIPURLCLEANING**
Type: `bool`

Allow the use of a double slash in url path, and can be useful if you need to pass raw URLs to your API endpoints. 
For example: `http://myapi.com/get/http://example.com`.


**[http_server_options.skip_target_path_escaping](#http_server_options.skip_target_path_escaping)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_SKIPTARGETPATHESCAPING**
Type: `bool`

Disable automatic character escaping, allowing to path original url data to the upstream.


**[http_server_options.ssl_ciphers](#http_server_options.ssl_ciphers)**
Environment Variable: **TYK_GW_HTTPSERVEROPTIONS_CIPHERS**
Type: `[]string`

Custom SSL ciphers. See list of ciphers here https://tyk.io/docs/basic-config-and-security/security/tls-and-ssl/#specify-tls-cipher-suites-for-tyk-gateway--tyk-dashboard


**[version_header](#version_header)**
Environment Variable: **TYK_GW_VERSIONHEADER**
Type: `string`

Expose version header with a given name. Works only for versioned APIs.


**[suppress_redis_signal_reload](#suppress_redis_signal_reload)**
Environment Variable: **TYK_GW_SUPPRESSREDISSIGNALRELOAD**
Type: `bool`

Disable dynamic API and Policcy reloads, e.g. it will load new changes only on procecss start.


**[hash_keys](#hash_keys)**
Environment Variable: **TYK_GW_HASHKEYS**
Type: `bool`

Enable Key hashing


**[hash_key_function](#hash_key_function)**
Environment Variable: **TYK_GW_HASHKEYFUNCTION**
Type: `string`

Specify Key hashing algorithm. Possible values: murmur64, murmur128, sha256


**[hash_key_function_fallback](#hash_key_function_fallback)**
Environment Variable: **TYK_GW_HASHKEYFUNCTIONFALLBACK**
Type: `[]string`

Specify previous key hashing algorithms if you migrated from one algorithm to another.


**[enable_hashed_keys_listing](#enable_hashed_keys_listing)**
Environment Variable: **TYK_GW_ENABLEHASHEDKEYSLISTING**
Type: `bool`

Allow listing hashed API keys


**[min_token_length](#min_token_length)**
Environment Variable: **TYK_GW_MINTOKENLENGTH**
Type: `int`

Minimum API token length


**[template_path](#template_path)**
Environment Variable: **TYK_GW_TEMPLATEPATH**
Type: `string`

Path to error and webhook templates. Defaults to current binary path.


**[policies](#policies)**
The policies section allows you to define where Tyk can find its policy templates. Policy templates are similar to key definitions in that they allow you to set quotas, access rights and rate limits for keys.
Policies are loaded when Tyk starts and if changed require a hot-reload so they are loaded into memory.
A policy can be defined in a file (stand alone mode) or from the same database as the Dashboard.


**[policies.policy_source](#policies.policy_source)**
Environment Variable: **TYK_GW_POLICIES_POLICYSOURCE**
Type: `string`

Set this value to `file` to look on the file system for a definition file, set to `service` to use the Dashboard service.


**[policies.policy_connection_string](#policies.policy_connection_string)**
Environment Variable: **TYK_GW_POLICIES_POLICYCONNECTIONSTRING**
Type: `string`

This option is required if `policies.policy_source` set to `service`. 
Set this to the URL of your dashboard installation, the URL should take the form of: http://dashboard_host:port.


**[policies.policy_record_name](#policies.policy_record_name)**
Environment Variable: **TYK_GW_POLICIES_POLICYRECORDNAME**
Type: `string`

This option is required if `policies.policy_source` set to `file`. 
Specifies the path of a JSON file containing the available policies.


**[policies.allow_explicit_policy_id](#policies.allow_explicit_policy_id)**
Environment Variable: **TYK_GW_POLICIES_ALLOWEXPLICITPOLICYID**
Type: `bool`

In a Pro installation, Tyk will load Policy IDs and use the internal object-ID as the ID of the policy. 
This is not portable in cases where the data needs to be moved from installation to installation.

If you set this value to true, then the id parameter in a stored policy (or imported policy using the REST API of the Dashboard), will be used instead of the internal ID.

This option should only be used when transporting an installation to a new database.


**[ports_whitelist](#ports_whitelist)**
Defines the ports that will be available for the api services to bind to.
This is a map of protocol to PortWhiteList. This allows per protocol
configurations.


**[disable_ports_whitelist](#disable_ports_whitelist)**
Environment Variable: **TYK_GW_DISABLEPORTWHITELIST**
Type: `bool`

Disable port whilisting, essentially allowing you to use any port for your API


**[app_path](#app_path)**
Environment Variable: **TYK_GW_APPPATH**
Type: `string`

If Tyk is being used in its standard configuration (CE Mode), then API definitions are stored in the apps folder (by default in /opt/tyk-gateway/apps). 
This file is scanned for files that ending in .json extension and interpreted at startup or reload. 
See the API Management section of the Tyk Gateway API for more details.


**[use_db_app_configs](#use_db_app_configs)**
Environment Variable: **TYK_GW_USEDBAPPCONFIGS**
Type: `bool`

If you are a Tyk Pro user, this option will enable polling the Dashboard service for API definitions. 
On startup Tyk will attempt to connect and download any relevant application configurations from from a Dashboard instance.
The documents are exactly the same as the JSON configuration on disk with the exception of a BSON ID supplied by the service.


**[db_app_conf_options](#db_app_conf_options)**
This section defines API loading and shard options, enable these settings to only selectively load API definitions on a node from a Dashboard service.


**[db_app_conf_options.connection_string](#db_app_conf_options.connection_string)**
Environment Variable: **TYK_GW_DBAPPCONFOPTIONS_CONNECTIONSTRING**
Type: `string`

Set the URL to your Dashboard instance (or a load balanced instance), the URL should take the form of: `http://dashboard_host:port`


**[db_app_conf_options.node_is_segmented](#db_app_conf_options.node_is_segmented)**
Environment Variable: **TYK_GW_DBAPPCONFOPTIONS_NODEISSEGMENTED**
Type: `bool`

Set to true to enable filtering (sharding) of APIs.


**[db_app_conf_options.tags](#db_app_conf_options.tags)**
Environment Variable: **TYK_GW_DBAPPCONFOPTIONS_TAGS**
Type: `[]string`

The tags to use when filtering (sharding) Tyk Gateway nodes, tags are processed as OR operations.
If you include a non-filter tag (e.g. an identifier such as `node-id-1`, this will become available to your analytics Dashboard).


**[storage](#storage)**
This section of the configuration is to hold the Redis configuration.


**[storage.type](#storage.type)**
Environment Variable: **TYK_GW_STORAGE_TYPE**
Type: `string`

This should be set to `redis` (lowercase)


**[storage.host](#storage.host)**
Environment Variable: **TYK_GW_STORAGE_HOST**
Type: `string`

The Redis host, by default this is set to `localhost`, but for production this should be set to a cluster.


**[storage.port](#storage.port)**
Environment Variable: **TYK_GW_STORAGE_PORT**
Type: `int`

The Redis instance port.


**[storage.master_name](#storage.master_name)**
Environment Variable: **TYK_GW_STORAGE_MASTERNAME**
Type: `string`

Redis sentinel master name


**[storage.sentinel_password](#storage.sentinel_password)**
Environment Variable: **TYK_GW_STORAGE_SENTINELPASSWORD**
Type: `string`

Redis sentinel password


**[storage.username](#storage.username)**
Environment Variable: **TYK_GW_STORAGE_USERNAME**
Type: `string`

Redis user name


**[storage.password](#storage.password)**
Environment Variable: **TYK_GW_STORAGE_PASSWORD**
Type: `string`

If your Redis instance has a password set for access, you can tell Tyk about it here.


**[storage.database](#storage.database)**
Environment Variable: **TYK_GW_STORAGE_DATABASE**
Type: `int`

Redis database


**[storage.optimisation_max_idle](#storage.optimisation_max_idle)**
Environment Variable: **TYK_GW_STORAGE_MAXIDLE**
Type: `int`

Set the number of maximum idle connections in the Redis connection pool, which defaults to 100. Set to higher if you are expecting more traffic.


**[storage.optimisation_max_active](#storage.optimisation_max_active)**
Environment Variable: **TYK_GW_STORAGE_MAXACTIVE**
Type: `int`

Set the number of maximum connections in the Redis connection pool, which defaults to 500. Set to higher if you are expecting more traffic.


**[storage.timeout](#storage.timeout)**
Environment Variable: **TYK_GW_STORAGE_TIMEOUT**
Type: `int`

Set cutom timeout for Redis network operations. Default value 5 seconds.


**[storage.enable_cluster](#storage.enable_cluster)**
Environment Variable: **TYK_GW_STORAGE_ENABLECLUSTER**
Type: `bool`

Enable Redis Cluster support


**[storage.use_ssl](#storage.use_ssl)**
Environment Variable: **TYK_GW_STORAGE_USESSL**
Type: `bool`

Enable SSL/TLS connection between Tyk Gateway & Redis.


**[storage.ssl_insecure_skip_verify](#storage.ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_STORAGE_SSLINSECURESKIPVERIFY**
Type: `bool`

Disable TLS verification


**[disable_dashboard_zeroconf](#disable_dashboard_zeroconf)**
Environment Variable: **TYK_GW_DISABLEDASHBOARDZEROCONF**
Type: `bool`

Disable the capability of the Gateway to `autodiscover` the Dashboard through heartbeat messages via Redis. 
The goal of zeroconf is auto-discovery, so you do not have to specify the Tyk Dashboard address in `tyk.conf`.
In some specific cases, for example, when the Dashboard is bound to a public domain, not accessible inside an internal network, or similar, `disable_dashboard_zeroconf` can be set to true, in favour of directly specifying a Tyk Dashboard address.


**[slave_options](#slave_options)**
The `slave_options` allow you to configure the RPC slave connection for MDCB installations.
These settings must be configured for every RPC slave/worker node.


**[slave_options.use_rpc](#slave_options.use_rpc)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_USERPC**
Type: `bool`

Set to `true` to connect a worker gateway using RPC.


**[slave_options.use_ssl](#slave_options.use_ssl)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_USESSL**
Type: `bool`

Set this option to `true` to use an SSL RPC connection.


**[slave_options.ssl_insecure_skip_verify](#slave_options.ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_SSLINSECURESKIPVERIFY**
Type: `bool`

Set this option to `true` to allow the certificate validation (certificate chain and hostname) to be skipped.
This can be useful if you use a self-signed certificate.


**[slave_options.connection_string](#slave_options.connection_string)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_CONNECTIONSTRING**
Type: `string`

Use this setting to add the URL for your MDCB or load balancer host.


**[slave_options.rpc_key](#slave_options.rpc_key)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_RPCKEY**
Type: `string`

Your organisation ID to connect to the MDCB installation.


**[slave_options.api_key](#slave_options.api_key)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_APIKEY**
Type: `string`

The user should be a standard Dashboard user with minimal privileges so as to reduce risk if compromised.
The suggested security settings are read for Real-time notifications and the remaining options set to deny.


**[slave_options.enable_rpc_cache](#slave_options.enable_rpc_cache)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_ENABLERPCCACHE**
Type: `bool`

Set this option to `true` to enable RPC caching for keys.


**[slave_options.group_id](#slave_options.group_id)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_GROUPID**
Type: `string`

This is the `zone` that this instance inhabits, e.g. the cluster/data-centre the Gateway lives in. 
The group ID must be the same across all the Gateways of a data-centre/cluster which are also sharing the same Redis instance.
This ID should also be unique per cluster (otherwise another Gateway cluster can pick up your keyspace events and your cluster will get zero updates).


**[slave_options.call_timeout](#slave_options.call_timeout)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_CALLTIMEOUT**
Type: `int`

Call Timeout allows to specify a time in seconds for the maximum allowed duration of a RPC call.


**[slave_options.ping_timeout](#slave_options.ping_timeout)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_PINGTIMEOUT**
Type: `int`

The maximum time in seconds that a RPC ping can last.


**[slave_options.rpc_pool_size](#slave_options.rpc_pool_size)**
Environment Variable: **TYK_GW_SLAVEOPTIONS_RPCPOOLSIZE**
Type: `int`

The number of RPC connections in the pool, basically it creates a set of connections that you can re-use as needed.


**[management_node](#management_node)**
Environment Variable: **TYK_GW_MANAGEMENTNODE**
Type: `bool`

If set to `true`, distributed rate limiter will be disabled for this node, and it will be excluded from rate limit calculation.

{{< note success >}}
If you set `db_app_conf_options.node_is_segmented` to `true` for multiple gateway nodes, you should ensure that `management_node` is set to false. 
This is to ensure visibility for the management node across all APIs.
{{< /note >}}


**[enable_redis_rolling_limiter](#enable_redis_rolling_limiter)**
Environment Variable: **TYK_GW_ENABLEREDISROLLINGLIMITER**
Type: `bool`

Redis based rate limiter with fixed window. Provides 100% rate limiting accuracy, but require two additional Redis roundtrip for each request.


**[enable_sentinel_rate_limiter](#enable_sentinel_rate_limiter)**
Environment Variable: **TYK_GW_ENABLESENTINELRATELIMITER**
Type: `bool`

The standard rate limiter offers similar performance as the sentinel-based limiter. This is disabled by default.


**[enable_non_transactional_rate_limiter](#enable_non_transactional_rate_limiter)**
Environment Variable: **TYK_GW_ENABLENONTRANSACTIONALRATELIMITER**
Type: `bool`

Enchancment for the Redis and Sentinel rate limiters, which that offers a significant improvement in performance by not using transactions on Redis rate-limit buckets.


**[drl_notification_frequency](#drl_notification_frequency)**
Environment Variable: **TYK_GW_DRLNOTIFICATIONFREQUENCY**
Type: `int`

How frequently distributed rate limiter synchronise information between the gateway nodes. Default: 2 seconds.


**[drl_threshold](#drl_threshold)**
Environment Variable: **TYK_GW_DRLTHRESHOLD**
Type: `float64`

Distributed rate limiter is inaccurate on small rate limits, thus it will fallback to Redis or Sentinel rate limiter on individual user basis, if its rate limiter lower then threshold.
Rate limiter threshold calculated using the following formula: `rate_threshold = drl_threshold * number_of_gateways`. 
So you have 2 gateways, and threshold is 5, if user rate limit is bigger then 10, it will use distributed rate limiter algorithm.
Default: 5


**[drl_enable_sentinel_rate_limiter](#drl_enable_sentinel_rate_limiter)**
Environment Variable: **TYK_GW_DRLENABLESENTINELRATELIMITER**
Type: `bool`

Controls which algorthm to use as fallback when distributed rate limiter can't be used.


**[enforce_org_data_age](#enforce_org_data_age)**
Environment Variable: **TYK_GW_ENFORCEORGDATAAGE**
Type: `bool`

Allow dynamically configure analytics expiration on per organisation level 


**[enforce_org_data_detail_logging](#enforce_org_data_detail_logging)**
Environment Variable: **TYK_GW_ENFORCEORGDATADETAILLOGGING**
Type: `bool`

Allow dynamically configure detailed logging on per organisation level 


**[enforce_org_quotas](#enforce_org_quotas)**
Environment Variable: **TYK_GW_ENFORCEORGQUOTAS**
Type: `bool`

Allow dynamically configure organisation quotas on per organisation level 


**[monitor](#monitor)**
The monitor section is useful if you wish to enforce a global trigger limit on organisation and user quotas. 
This feature will trigger a webhook event to fire when specific triggers are reached. 
Triggers can be global (set in the node), by organisation (set in the organisation session object) or by key (set in the key session object)

While Organisation-level and Key-level triggers can be tiered (e.g. trigger at 10%, trigger at 20%, trigger at 80%), in the node-level configuration only a global value can be set.
If a global value and specific trigger level are the same the trigger will only fire once:

```
"monitor": {
  "enable_trigger_monitors": true,
  "configuration": {
   "method": "POST",
   "target_path": "http://domain.com/notify/quota-trigger",
   "template_path": "templates/monitor_template.json",
   "header_map": {
     "some-secret": "89787855"
   },
   "event_timeout": 10
 },
 "global_trigger_limit": 80.0,
 "monitor_user_keys": false,
 "monitor_org_keys": true
},


**[monitor.enable_trigger_monitors](#monitor.enable_trigger_monitors)**
Environment Variable: **TYK_GW_MONITOR_ENABLETRIGGERMONITORS**
Type: `bool`

Set this to `true` to have monitors enabled in your configuration for the node.


**[monitor.configuration.method](#monitor.configuration.method)**
Environment Variable: **TYK_GW_MONITOR_CONFIG_METHOD**
Type: `string`

The method to use for the webhook.


**[monitor.configuration.target_path](#monitor.configuration.target_path)**
Environment Variable: **TYK_GW_MONITOR_CONFIG_TARGETPATH**
Type: `string`

The target path on which to send the request.


**[monitor.configuration.template_path](#monitor.configuration.template_path)**
Environment Variable: **TYK_GW_MONITOR_CONFIG_TEMPLATEPATH**
Type: `string`

The template to load in order to format the request.


**[monitor.configuration.header_map](#monitor.configuration.header_map)**
Environment Variable: **TYK_GW_MONITOR_CONFIG_HEADERLIST**
Type: `map[string]string`

Headers to set when firing the webhook.


**[monitor.configuration.event_timeout](#monitor.configuration.event_timeout)**
Environment Variable: **TYK_GW_MONITOR_CONFIG_EVENTTIMEOUT**
Type: `int64`

The cool-down for the event so it does not trigger again (in seconds).


**[monitor.global_trigger_limit](#monitor.global_trigger_limit)**
Environment Variable: **TYK_GW_MONITOR_GLOBALTRIGGERLIMIT**
Type: `float64`

The trigger limit, as a percentage of the quota that must be reached in order to trigger the event, any time the quota percentage is increased the event will trigger.


**[monitor.monitor_user_keys](#monitor.monitor_user_keys)**
Environment Variable: **TYK_GW_MONITOR_MONITORUSERKEYS**
Type: `bool`

Apply the monitoring subsystem to user keys.


**[monitor.monitor_org_keys](#monitor.monitor_org_keys)**
Environment Variable: **TYK_GW_MONITOR_MONITORORGKEYS**
Type: `bool`

Apply the monitoring subsystem to organisation keys.


**[max_idle_connections](#max_idle_connections)**
Environment Variable: **TYK_GW_MAXIDLECONNS**
Type: `int`

Maximum idle connections, per API, between Tyk and Upstream. By default not limited.


**[max_idle_connections_per_host](#max_idle_connections_per_host)**
Environment Variable: **TYK_GW_MAXIDLECONNSPERHOST**
Type: `int`

Maximum idle connections, per API, per upstream, between Tyk and Upstream. Default: 100


**[max_conn_time](#max_conn_time)**
Environment Variable: **TYK_GW_MAXCONNTIME**
Type: `int64`

Maximum connection time. If set it will force gateway reconnect to the upstream. 


**[close_connections](#close_connections)**
Environment Variable: **TYK_GW_CLOSECONNECTIONS**
Type: `bool`

If set, disable keepalive between User and Tyk


**[enable_custom_domains](#enable_custom_domains)**
Environment Variable: **TYK_GW_ENABLECUSTOMDOMAINS**
Type: `bool`

Allow use of custom domains


**[allow_master_keys](#allow_master_keys)**
Environment Variable: **TYK_GW_ALLOWMASTERKEYS**
Type: `bool`

If AllowMasterKeys is set to true, session objects (key definitions) that do not have explicit access rights set
will be allowed by Tyk. This means that keys that are created have access to ALL APIs, which in many cases is
unwanted behaviour unless you are sure about what you are doing.


**[service_discovery.default_cache_timeout](#service_discovery.default_cache_timeout)**
Environment Variable: **TYK_GW_SERVICEDISCOVERY_DEFAULTCACHETIMEOUT**
Type: `int`

Service discovery cache timeout


**[proxy_ssl_insecure_skip_verify](#proxy_ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_PROXYSSLINSECURESKIPVERIFY**
Type: `bool`

Globally ignore TLS verification between Tyk and Upstream 


**[proxy_enable_http2](#proxy_enable_http2)**
Environment Variable: **TYK_GW_PROXYENABLEHTTP2**
Type: `bool`

Enable HTTP2 support between Tyk and Upstream. Required for gRPC.


**[proxy_ssl_min_version](#proxy_ssl_min_version)**
Environment Variable: **TYK_GW_PROXYSSLMINVERSION**
Type: `uint16`

Minimum TLS version for connection between Tyk and Upstream.


**[proxy_ssl_max_version](#proxy_ssl_max_version)**
Environment Variable: **TYK_GW_PROXYSSLMAXVERSION**
Type: `uint16`

Maximum TLS version for connection between Tyk and Upstream.


**[proxy_ssl_ciphers](#proxy_ssl_ciphers)**
Environment Variable: **TYK_GW_PROXYSSLCIPHERSUITES**
Type: `[]string`

Whitelist ciphers for connection between Tyk and Upstream.


**[proxy_default_timeout](#proxy_default_timeout)**
Environment Variable: **TYK_GW_PROXYDEFAULTTIMEOUT**
Type: `float64`

This can specify a default timeout in seconds for upstream API requests.


**[proxy_ssl_disable_renegotiation](#proxy_ssl_disable_renegotiation)**
Environment Variable: **TYK_GW_PROXYSSLDISABLERENEGOTIATION**
Type: `bool`

Disable TLS renegotiation.


**[proxy_close_connections](#proxy_close_connections)**
Environment Variable: **TYK_GW_PROXYCLOSECONNECTIONS**
Type: `bool`

Disable keepalives between Tyk and Upstream.
Set this value to true to force Tyk to close the connection with the server, otherwise the connections will remain open for as long as your OS keeps TCP connections open. 
This can cause a file-handler limit to be exceeded. Setting to false can have performance benefits as the connection can be reused.


**[uptime_tests](#uptime_tests)**
Tyk nodes can provide uptime awareness, uptime testing and analytics for your underlying APIs uptime and availability.
Tyk can also notify you when a service goes down.


**[uptime_tests.disable](#uptime_tests.disable)**
Environment Variable: **TYK_GW_UPTIMETESTS_DISABLE**
Type: `bool`

To disable uptime tests on this node, switch this value to true.


**[uptime_tests.poller_group](#uptime_tests.poller_group)**
Environment Variable: **TYK_GW_UPTIMETESTS_POLLERGROUP**
Type: `string`

If you have multiple Gateway clusters connected to the same Redis, you need to set uniq poller group for each cluster.


**[uptime_tests.config.failure_trigger_sample_size](#uptime_tests.config.failure_trigger_sample_size)**
Environment Variable: **TYK_GW_UPTIMETESTS_CONFIG_FAILURETRIGGERSAMPLESIZE**
Type: `int`

The sample size to trigger a `HostUp` or `HostDown` event, e.g. a setting of 3 will require at least three failures to occur before the uptime test is triggered.


**[uptime_tests.config.time_wait](#uptime_tests.config.time_wait)**
Environment Variable: **TYK_GW_UPTIMETESTS_CONFIG_TIMEWAIT**
Type: `int`

The amount of seconds between tests runs, all tests will run simultaneously, this value will set the periodicity between those tests. e.g. A value of 60 will run all uptime tests every 60 seconds.


**[uptime_tests.config.checker_pool_size](#uptime_tests.config.checker_pool_size)**
Environment Variable: **TYK_GW_UPTIMETESTS_CONFIG_CHECKERPOOLSIZE**
Type: `int`

The goroutine pool size to keep idle for uptime tests, if you have many uptime tests running at a high periodicity, then make this value higher.


**[uptime_tests.config.enable_uptime_analytics](#uptime_tests.config.enable_uptime_analytics)**
Environment Variable: **TYK_GW_UPTIMETESTS_CONFIG_ENABLEUPTIMEANALYTICS**
Type: `bool`

Set this value to true to have the node capture and record analytics data regarding the uptime tests.


**[health_check](#health_check)**
This section enables the configuration of the health-check API endpoint and the size of the sample data cache (in seconds).


**[health_check.enable_health_checks](#health_check.enable_health_checks)**
Environment Variable: **TYK_GW_HEALTHCHECK_ENABLEHEALTHCHECKS**
Type: `bool`

Setting this value to true will enable the health-check endpoint on /Tyk/health.


**[health_check.health_check_value_timeouts](#health_check.health_check_value_timeouts)**
Environment Variable: **TYK_GW_HEALTHCHECK_HEALTHCHECKVALUETIMEOUT**
Type: `int64`

This setting defaults to 60, this is the time window that Tyk will use to sample health-check data.
Increase this value for more accurate data (larger sample period), and decrease for less accurate.
The reason this value is configurable is because sample data takes up space in your Redis DB to store the data to calculate samples, on high-availability systems this may not be desirable and smaller values may be preferred.


**[health_check_endpoint_name](#health_check_endpoint_name)**
Environment Variable: **TYK_GW_HEALTHCHECKENDPOINTNAME**
Type: `string`

Way to rename the /hello endpoint


**[oauth_refresh_token_expire](#oauth_refresh_token_expire)**
Environment Variable: **TYK_GW_OAUTHREFRESHEXPIRE**
Type: `int64`

Change the expiry time of refresh token, by default 14 days (in seconds).


**[oauth_token_expire](#oauth_token_expire)**
Environment Variable: **TYK_GW_OAUTHTOKENEXPIRE**
Type: `int32`

Change the expiry time of OAuth token (in seconds).


**[oauth_token_expired_retain_period](#oauth_token_expired_retain_period)**
Environment Variable: **TYK_GW_OAUTHTOKENEXPIREDRETAINPERIOD**
Type: `int32`

Specifies how long expired tokens are stored in Redis. The value is in seconds and the default is 0. Using the default means expired tokens are never removed from Redis.


**[oauth_redirect_uri_separator](#oauth_redirect_uri_separator)**
Environment Variable: **TYK_GW_OAUTHREDIRECTURISEPARATOR**
Type: `string`

Character which should be used as a separator for oauth redirect uri urls. Default: ;.


**[oauth_error_status_code](#oauth_error_status_code)**
Environment Variable: **TYK_GW_OAUTHERRORSTATUSCODE**
Type: `int`

Configure the OAuth error status code returned. If not set, it defaults to a 403 error.


**[enable_key_logging](#enable_key_logging)**
Environment Variable: **TYK_GW_ENABLEKEYLOGGING**
Type: `bool`

By default all key ids in logs are hidden. Turn it on if you want to see them for debugging reasons.


**[ssl_force_common_name_check](#ssl_force_common_name_check)**
Environment Variable: **TYK_GW_SSLFORCECOMMONNAMECHECK**
Type: `bool`

Force validation of the hostname against the common name, even if TLS verification is disabled.


**[enable_analytics](#enable_analytics)**
Environment Variable: **TYK_GW_ENABLEANALYTICS**
Type: `bool`

Tyk is capable of recording every hit to your API into a database with various filtering parameters, set this value to true and fill in the sub-section below to enable logging.

{{< note success >}}
For performance reasons, Tyk will store traffic data to Redis initially and then purge the data from Redis to MongoDB or other, data stores, on a regular basis as determined by the purge_delay setting in your Tyk Pump configuration.
{{< /note >}}


**[analytics_storage.type](#analytics_storage.type)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_TYPE**
Type: `string`

This should be set to `redis` (lowercase)


**[analytics_storage.host](#analytics_storage.host)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_HOST**
Type: `string`

The Redis host, by default this is set to `localhost`, but for production this should be set to a cluster.


**[analytics_storage.port](#analytics_storage.port)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_PORT**
Type: `int`

The Redis instance port.


**[analytics_storage.master_name](#analytics_storage.master_name)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_MASTERNAME**
Type: `string`

Redis sentinel master name


**[analytics_storage.sentinel_password](#analytics_storage.sentinel_password)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_SENTINELPASSWORD**
Type: `string`

Redis sentinel password


**[analytics_storage.username](#analytics_storage.username)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_USERNAME**
Type: `string`

Redis user name


**[analytics_storage.password](#analytics_storage.password)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_PASSWORD**
Type: `string`

If your Redis instance has a password set for access, you can tell Tyk about it here.


**[analytics_storage.database](#analytics_storage.database)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_DATABASE**
Type: `int`

Redis database


**[analytics_storage.optimisation_max_idle](#analytics_storage.optimisation_max_idle)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_MAXIDLE**
Type: `int`

Set the number of maximum idle connections in the Redis connection pool, which defaults to 100. Set to higher if you are expecting more traffic.


**[analytics_storage.optimisation_max_active](#analytics_storage.optimisation_max_active)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_MAXACTIVE**
Type: `int`

Set the number of maximum connections in the Redis connection pool, which defaults to 500. Set to higher if you are expecting more traffic.


**[analytics_storage.timeout](#analytics_storage.timeout)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_TIMEOUT**
Type: `int`

Set cutom timeout for Redis network operations. Default value 5 seconds.


**[analytics_storage.enable_cluster](#analytics_storage.enable_cluster)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_ENABLECLUSTER**
Type: `bool`

Enable Redis Cluster support


**[analytics_storage.use_ssl](#analytics_storage.use_ssl)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_USESSL**
Type: `bool`

Enable SSL/TLS connection between Tyk Gateway & Redis.


**[analytics_storage.ssl_insecure_skip_verify](#analytics_storage.ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_ANALYTICSSTORAGE_SSLINSECURESKIPVERIFY**
Type: `bool`

Disable TLS verification


**[dns_cache](#dns_cache)**
Cache


**[cache_storage.type](#cache_storage.type)**
Environment Variable: **TYK_GW_CACHESTORAGE_TYPE**
Type: `string`

This should be set to `redis` (lowercase)


**[cache_storage.host](#cache_storage.host)**
Environment Variable: **TYK_GW_CACHESTORAGE_HOST**
Type: `string`

The Redis host, by default this is set to `localhost`, but for production this should be set to a cluster.


**[cache_storage.port](#cache_storage.port)**
Environment Variable: **TYK_GW_CACHESTORAGE_PORT**
Type: `int`

The Redis instance port.


**[cache_storage.master_name](#cache_storage.master_name)**
Environment Variable: **TYK_GW_CACHESTORAGE_MASTERNAME**
Type: `string`

Redis sentinel master name


**[cache_storage.sentinel_password](#cache_storage.sentinel_password)**
Environment Variable: **TYK_GW_CACHESTORAGE_SENTINELPASSWORD**
Type: `string`

Redis sentinel password


**[cache_storage.username](#cache_storage.username)**
Environment Variable: **TYK_GW_CACHESTORAGE_USERNAME**
Type: `string`

Redis user name


**[cache_storage.password](#cache_storage.password)**
Environment Variable: **TYK_GW_CACHESTORAGE_PASSWORD**
Type: `string`

If your Redis instance has a password set for access, you can tell Tyk about it here.


**[cache_storage.database](#cache_storage.database)**
Environment Variable: **TYK_GW_CACHESTORAGE_DATABASE**
Type: `int`

Redis database


**[cache_storage.optimisation_max_idle](#cache_storage.optimisation_max_idle)**
Environment Variable: **TYK_GW_CACHESTORAGE_MAXIDLE**
Type: `int`

Set the number of maximum idle connections in the Redis connection pool, which defaults to 100. Set to higher if you are expecting more traffic.


**[cache_storage.optimisation_max_active](#cache_storage.optimisation_max_active)**
Environment Variable: **TYK_GW_CACHESTORAGE_MAXACTIVE**
Type: `int`

Set the number of maximum connections in the Redis connection pool, which defaults to 500. Set to higher if you are expecting more traffic.


**[cache_storage.timeout](#cache_storage.timeout)**
Environment Variable: **TYK_GW_CACHESTORAGE_TIMEOUT**
Type: `int`

Set cutom timeout for Redis network operations. Default value 5 seconds.


**[cache_storage.enable_cluster](#cache_storage.enable_cluster)**
Environment Variable: **TYK_GW_CACHESTORAGE_ENABLECLUSTER**
Type: `bool`

Enable Redis Cluster support


**[cache_storage.use_ssl](#cache_storage.use_ssl)**
Environment Variable: **TYK_GW_CACHESTORAGE_USESSL**
Type: `bool`

Enable SSL/TLS connection between Tyk Gateway & Redis.


**[cache_storage.ssl_insecure_skip_verify](#cache_storage.ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_CACHESTORAGE_SSLINSECURESKIPVERIFY**
Type: `bool`

Disable TLS verification


**[enable_bundle_downloader](#enable_bundle_downloader)**
Environment Variable: **TYK_GW_ENABLEBUNDLEDOWNLOADER**
Type: `bool`

Middleware/Plugin Configuration


**[log_level](#log_level)**
Environment Variable: **TYK_GW_LOGLEVEL**
Type: `string`

Monitoring, Logging & Profiling


**[tracing.name](#tracing.name)**
Environment Variable: **TYK_GW_TRACER_NAME**
Type: `string`

The name of the tracer to initialize. For instance appdash, to use appdash tracer


**[tracing.enabled](#tracing.enabled)**
Environment Variable: **TYK_GW_TRACER_ENABLED**
Type: `bool`

Enable tracing


**[tracing.options](#tracing.options)**
Environment Variable: **TYK_GW_TRACER_OPTIONS**
Type: `map[string]interface{}`

Tracing configuration. Refer to the Tracing Docs for the full list of options.


**[newrelic.app_name](#newrelic.app_name)**
Environment Variable: **TYK_GW_NEWRELIC_APPNAME**
Type: `string`

New Relic Application name


**[newrelic.license_key](#newrelic.license_key)**
Environment Variable: **TYK_GW_NEWRELIC_LICENSEKEY**
Type: `string`

New Relic License key


**[event_handlers](#event_handlers)**
Event System


**[hide_generator_header](#hide_generator_header)**
Environment Variable: **TYK_GW_HIDEGENERATORHEADER**
Type: `bool`

HideGeneratorHeader will mask the 'X-Generator' and 'X-Mascot-...' headers, if set to true.


**[suppress_default_org_store](#suppress_default_org_store)**
Environment Variable: **TYK_GW_SUPRESSDEFAULTORGSTORE**
Type: `bool`

TODO: These config options are not documented - What do they do?


**[kv.consul.address](#kv.consul.address)**
Environment Variable: **TYK_GW_KV_CONSUL_ADDRESS**
Type: `string`

Address is the address of the Consul server


**[kv.consul.scheme](#kv.consul.scheme)**
Environment Variable: **TYK_GW_KV_CONSUL_SCHEME**
Type: `string`

Scheme is the URI scheme for the Consul server


**[kv.consul.datacenter](#kv.consul.datacenter)**
Environment Variable: **TYK_GW_KV_CONSUL_DATACENTER**
Type: `string`

Datacenter to use. If not provided, the default agent datacenter is used.


**[kv.consul.http_auth.username](#kv.consul.http_auth.username)**
Environment Variable: **TYK_GW_KV_CONSUL_HTTPAUTH_USERNAME**
Type: `string`

Username to use for HTTP Basic Authentication


**[kv.consul.http_auth.password](#kv.consul.http_auth.password)**
Environment Variable: **TYK_GW_KV_CONSUL_HTTPAUTH_PASSWORD**
Type: `string`

Password to use for HTTP Basic Authentication


**[kv.vault.token](#kv.vault.token)**
Environment Variable: **TYK_GW_KV_VAULT_TOKEN**
Type: `string`

Token is the vault root token


**[kv.vault.kv_version](#kv.vault.kv_version)**
Environment Variable: **TYK_GW_KV_VAULT_KVVERSION**
Type: `int`

KVVersion is the version number of Vault. Usually defaults to 2


**[secrets](#secrets)**
Environment Variable: **TYK_GW_SECRETS**
Type: `map[string]string`

Secrets are key-value pairs that can be accessed in the dashboard via "secrets://"


**[override_messages](#override_messages)**
OverrideMessages is used to override returned API error codes and messages.


**[cloud](#cloud)**
Environment Variable: **TYK_GW_CLOUD**
Type: `bool`

Cloud flag shows that gateway runs in Tyk-cloud.


**[jwt_ssl_insecure_skip_verify](#jwt_ssl_insecure_skip_verify)**
Environment Variable: **TYK_GW_JWTSSLINSECURESKIPVERIFY**
Type: `bool`

SSL options for JWT middleware.



