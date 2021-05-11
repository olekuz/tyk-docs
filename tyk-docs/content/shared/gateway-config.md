---
---

### hostname
EV: **TYK_GW_HOSTNAME**<br />
Type: `string`<br />

Force gateway to work only on a specifc domain name. Can be overriden by API custom domain.

### listen_address
EV: **TYK_GW_LISTENADDRESS**<br />
Type: `string`<br />

If your machine has mulitple network devices or IPs you can force Gateway to use IP address you need

### listen_port
EV: **TYK_GW_LISTENPORT**<br />
Type: `int`<br />

Setting this value will change the port that Tyk listens on. Default: 8080.

### control_api_hostname
EV: **TYK_GW_CONTROLAPIHOSTNAME**<br />
Type: `string`<br />

Custom hostname for the Control API

### control_api_port
EV: **TYK_GW_CONTROLAPIPORT**<br />
Type: `int`<br />

Set to run Gateway Control API on separate port, and protect it behind a firewall if needed. Please make sure you follow instructions when setting the control port https://tyk.io/docs/planning-for-production/#change-your-control-port.

### secret
EV: **TYK_GW_SECRET**<br />
Type: `string`<br />

This should be changed as soon as Tyk is installed on the system. 
This value is used in every interaction with the Tyk REST API, it should be passed along as the X-Tyk-Authorization header in any requests made.
Tyk assumes that you are sensible enough not to expose the management endpoints to the public and to keep this configuration value to yourself.

### node_secret
EV: **TYK_GW_NODESECRET**<br />
Type: `string`<br />

The shared secret between the Gateway and the Dashboard to ensure that API Definition downloads, heartbeat and Policy loads are from a valid source.

### pid_file_location
EV: **TYK_GW_PIDFILELOCATION**<br />
Type: `string`<br />

Linux PID file location. Do not change until you know what you are doing. Default: /var/run/tyk/tyk-gateway.pid

### allow_insecure_configs
EV: **TYK_GW_ALLOWINSECURECONFIGS**<br />
Type: `bool`<br />

Can be set to disable Dashboard message signature verification. When set to `true`, `public_key_path` can be ignored.

### public_key_path
EV: **TYK_GW_PUBLICKEYPATH**<br />
Type: `string`<br />

While communicating with the Dashboard, by default, all the messages are signed by a private/public key pair. Set path to public key.

### allow_remote_config
EV: **TYK_GW_ALLOWREMOTECONFIG**<br />
Type: `bool`<br />

Allow Dashboard to remotely set Gateway configuration via Nodes screen. 

### security
Global Certificate configuration

### security.private_certificate_encoding_secret
EV: **TYK_GW_SECURITY_PRIVATECERTIFICATEENCODINGSECRET**<br />
Type: `string`<br />

Set AES256 secret which is used to encode certificate private keys when they uploaded via certificate storage

### security.control_api_use_mutual_tls
EV: **TYK_GW_SECURITY_CONTROLAPIUSEMUTUALTLS**<br />
Type: `bool`<br />

Enable Gateway Control API to use Mutual TLS. Certificates can be set via `security.certificates.control_api` section

### security.pinned_public_keys
EV: **TYK_GW_SECURITY_PINNEDPUBLICKEYS**<br />
Type: `map[string]string`<br />

Specify public keys used for Certificate Pinning on global level. 

### security.certificates.upstream
EV: **TYK_GW_SECURITY_CERTIFICATES_UPSTREAM**<br />
Type: `map[string]string`<br />

Specify upstream mutual TLS certificates on global level in the following format: { "<host>": "<cert>" }

### security.certificates.control_api
EV: **TYK_GW_SECURITY_CERTIFICATES_CONTROLAPI**<br />
Type: `[]string`<br />

Certificates used for Control API Mutual TLS

### security.certificates.dashboard_api
EV: **TYK_GW_SECURITY_CERTIFICATES_DASHBOARD**<br />
Type: `[]string`<br />

Used for communicating with the Dashboard if it is configured to use Mutual TLS

### security.certificates.mdcb_api
EV: **TYK_GW_SECURITY_CERTIFICATES_MDCB**<br />
Type: `[]string`<br />

Certificates used for MDCB Mutual TLS 

### http_server_options
Gateway HTTP server configuration

### http_server_options.read_timeout
EV: **TYK_GW_HTTPSERVEROPTIONS_READTIMEOUT**<br />
Type: `int`<br />

User -> Gateway network read timeout

### http_server_options.write_timeout
EV: **TYK_GW_HTTPSERVEROPTIONS_WRITETIMEOUT**<br />
Type: `int`<br />

User -> Gateway network write timeout

### http_server_options.use_ssl
EV: **TYK_GW_HTTPSERVEROPTIONS_USESSL**<br />
Type: `bool`<br />

Set to true to enable SSL connections

### http_server_options.use_ssl_le
EV: **TYK_GW_HTTPSERVEROPTIONS_USELE_SSL**<br />
Type: `bool`<br />

Enable lets-encrypt support

### http_server_options.enable_http2
EV: **TYK_GW_HTTPSERVEROPTIONS_ENABLEHTTP2**<br />
Type: `bool`<br />

Enable HTTP2 protocol handling

### http_server_options.ssl_insecure_skip_verify
EV: **TYK_GW_HTTPSERVEROPTIONS_SSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

Disable TLS verification. Required if you are using self-signed certificates.

### http_server_options.enable_websockets
EV: **TYK_GW_HTTPSERVEROPTIONS_ENABLEWEBSOCKETS**<br />
Type: `bool`<br />

Enabled websockets and server side events support

### http_server_options.certificates
EV: **TYK_GW_HTTPSERVEROPTIONS_CERTIFICATES**<br />
Type: `[]CertData`<br />

Deprecated. SSL certificates used by Gateway server. 

### http_server_options.ssl_certificates
EV: **TYK_GW_HTTPSERVEROPTIONS_SSLCERTIFICATES**<br />
Type: `[]string`<br />

SSL certificates used by Gateway server. List of certificate IDs or path to files.

### http_server_options.server_name
EV: **TYK_GW_HTTPSERVEROPTIONS_SERVERNAME**<br />
Type: `string`<br />

Start Gateway HTTP server on specific server name

### http_server_options.min_version
EV: **TYK_GW_HTTPSERVEROPTIONS_MINVERSION**<br />
Type: `uint16`<br />

Minimum TLS version. Possible values: https://tyk.io/docs/basic-config-and-security/security/tls-and-ssl/#values-for-tls-versions

### http_server_options.max_version
EV: **TYK_GW_HTTPSERVEROPTIONS_MAXVERSION**<br />
Type: `uint16`<br />

Maximum TLS version. 

### http_server_options.flush_interval
EV: **TYK_GW_HTTPSERVEROPTIONS_FLUSHINTERVAL**<br />
Type: `int`<br />

Set this to the number of seconds that Tyk should use to flush content from the proxied upstream connection to the open downstream connection. 
This option needed be set streaming protocols like Server Side Events, or gRPC streaming.

### http_server_options.skip_url_cleaning
EV: **TYK_GW_HTTPSERVEROPTIONS_SKIPURLCLEANING**<br />
Type: `bool`<br />

Allow the use of a double slash in url path, and can be useful if you need to pass raw URLs to your API endpoints. 
For example: `http://myapi.com/get/http://example.com`.

### http_server_options.skip_target_path_escaping
EV: **TYK_GW_HTTPSERVEROPTIONS_SKIPTARGETPATHESCAPING**<br />
Type: `bool`<br />

Disable automatic character escaping, allowing to path original url data to the upstream.

### http_server_options.ssl_ciphers
EV: **TYK_GW_HTTPSERVEROPTIONS_CIPHERS**<br />
Type: `[]string`<br />

Custom SSL ciphers. See list of ciphers here https://tyk.io/docs/basic-config-and-security/security/tls-and-ssl/#specify-tls-cipher-suites-for-tyk-gateway--tyk-dashboard

### version_header
EV: **TYK_GW_VERSIONHEADER**<br />
Type: `string`<br />

Expose version header with a given name. Works only for versioned APIs.

### suppress_redis_signal_reload
EV: **TYK_GW_SUPPRESSREDISSIGNALRELOAD**<br />
Type: `bool`<br />

Disable dynamic API and Policcy reloads, e.g. it will load new changes only on procecss start.

### hash_keys
EV: **TYK_GW_HASHKEYS**<br />
Type: `bool`<br />

Enable Key hashing

### hash_key_function
EV: **TYK_GW_HASHKEYFUNCTION**<br />
Type: `string`<br />

Specify Key hashing algorithm. Possible values: murmur64, murmur128, sha256

### hash_key_function_fallback
EV: **TYK_GW_HASHKEYFUNCTIONFALLBACK**<br />
Type: `[]string`<br />

Specify previous key hashing algorithms if you migrated from one algorithm to another.

### enable_hashed_keys_listing
EV: **TYK_GW_ENABLEHASHEDKEYSLISTING**<br />
Type: `bool`<br />

Allow listing hashed API keys

### min_token_length
EV: **TYK_GW_MINTOKENLENGTH**<br />
Type: `int`<br />

Minimum API token length

### template_path
EV: **TYK_GW_TEMPLATEPATH**<br />
Type: `string`<br />

Path to error and webhook templates. Defaults to current binary path.

### policies
The policies section allows you to define where Tyk can find its policy templates. Policy templates are similar to key definitions in that they allow you to set quotas, access rights and rate limits for keys.
Policies are loaded when Tyk starts and if changed require a hot-reload so they are loaded into memory.
A policy can be defined in a file (stand alone mode) or from the same database as the Dashboard.

### policies.policy_source
EV: **TYK_GW_POLICIES_POLICYSOURCE**<br />
Type: `string`<br />

Set this value to `file` to look on the file system for a definition file, set to `service` to use the Dashboard service.

### policies.policy_connection_string
EV: **TYK_GW_POLICIES_POLICYCONNECTIONSTRING**<br />
Type: `string`<br />

This option is required if `policies.policy_source` set to `service`. 
Set this to the URL of your dashboard installation, the URL should take the form of: http://dashboard_host:port.

### policies.policy_record_name
EV: **TYK_GW_POLICIES_POLICYRECORDNAME**<br />
Type: `string`<br />

This option is required if `policies.policy_source` set to `file`. 
Specifies the path of a JSON file containing the available policies.

### policies.allow_explicit_policy_id
EV: **TYK_GW_POLICIES_ALLOWEXPLICITPOLICYID**<br />
Type: `bool`<br />

In a Pro installation, Tyk will load Policy IDs and use the internal object-ID as the ID of the policy. 
This is not portable in cases where the data needs to be moved from installation to installation.

If you set this value to true, then the id parameter in a stored policy (or imported policy using the REST API of the Dashboard), will be used instead of the internal ID.

This option should only be used when transporting an installation to a new database.

### ports_whitelist
Defines the ports that will be available for the api services to bind to.
This is a map of protocol to PortWhiteList. This allows per protocol
configurations.

### disable_ports_whitelist
EV: **TYK_GW_DISABLEPORTWHITELIST**<br />
Type: `bool`<br />

Disable port whilisting, essentially allowing you to use any port for your API

### app_path
EV: **TYK_GW_APPPATH**<br />
Type: `string`<br />

If Tyk is being used in its standard configuration (CE Mode), then API definitions are stored in the apps folder (by default in /opt/tyk-gateway/apps). 
This file is scanned for files that ending in .json extension and interpreted at startup or reload. 
See the API Management section of the Tyk Gateway API for more details.

### use_db_app_configs
EV: **TYK_GW_USEDBAPPCONFIGS**<br />
Type: `bool`<br />

If you are a Tyk Pro user, this option will enable polling the Dashboard service for API definitions. 
On startup Tyk will attempt to connect and download any relevant application configurations from from a Dashboard instance.
The documents are exactly the same as the JSON configuration on disk with the exception of a BSON ID supplied by the service.

### db_app_conf_options
This section defines API loading and shard options, enable these settings to only selectively load API definitions on a node from a Dashboard service.

### db_app_conf_options.connection_string
EV: **TYK_GW_DBAPPCONFOPTIONS_CONNECTIONSTRING**<br />
Type: `string`<br />

Set the URL to your Dashboard instance (or a load balanced instance), the URL should take the form of: `http://dashboard_host:port`

### db_app_conf_options.node_is_segmented
EV: **TYK_GW_DBAPPCONFOPTIONS_NODEISSEGMENTED**<br />
Type: `bool`<br />

Set to true to enable filtering (sharding) of APIs.

### db_app_conf_options.tags
EV: **TYK_GW_DBAPPCONFOPTIONS_TAGS**<br />
Type: `[]string`<br />

The tags to use when filtering (sharding) Tyk Gateway nodes, tags are processed as OR operations.
If you include a non-filter tag (e.g. an identifier such as `node-id-1`, this will become available to your analytics Dashboard).

### storage
This section of the configuration is to hold the Redis configuration.

### storage.type
EV: **TYK_GW_STORAGE_TYPE**<br />
Type: `string`<br />

This should be set to `redis` (lowercase)

### storage.host
EV: **TYK_GW_STORAGE_HOST**<br />
Type: `string`<br />

The Redis host, by default this is set to `localhost`, but for production this should be set to a cluster.

### storage.port
EV: **TYK_GW_STORAGE_PORT**<br />
Type: `int`<br />

The Redis instance port.

### storage.master_name
EV: **TYK_GW_STORAGE_MASTERNAME**<br />
Type: `string`<br />

Redis sentinel master name

### storage.sentinel_password
EV: **TYK_GW_STORAGE_SENTINELPASSWORD**<br />
Type: `string`<br />

Redis sentinel password

### storage.username
EV: **TYK_GW_STORAGE_USERNAME**<br />
Type: `string`<br />

Redis user name

### storage.password
EV: **TYK_GW_STORAGE_PASSWORD**<br />
Type: `string`<br />

If your Redis instance has a password set for access, you can tell Tyk about it here.

### storage.database
EV: **TYK_GW_STORAGE_DATABASE**<br />
Type: `int`<br />

Redis database

### storage.optimisation_max_idle
EV: **TYK_GW_STORAGE_MAXIDLE**<br />
Type: `int`<br />

Set the number of maximum idle connections in the Redis connection pool, which defaults to 100. Set to higher if you are expecting more traffic.

### storage.optimisation_max_active
EV: **TYK_GW_STORAGE_MAXACTIVE**<br />
Type: `int`<br />

Set the number of maximum connections in the Redis connection pool, which defaults to 500. Set to higher if you are expecting more traffic.

### storage.timeout
EV: **TYK_GW_STORAGE_TIMEOUT**<br />
Type: `int`<br />

Set cutom timeout for Redis network operations. Default value 5 seconds.

### storage.enable_cluster
EV: **TYK_GW_STORAGE_ENABLECLUSTER**<br />
Type: `bool`<br />

Enable Redis Cluster support

### storage.use_ssl
EV: **TYK_GW_STORAGE_USESSL**<br />
Type: `bool`<br />

Enable SSL/TLS connection between Tyk Gateway & Redis.

### storage.ssl_insecure_skip_verify
EV: **TYK_GW_STORAGE_SSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

Disable TLS verification

### disable_dashboard_zeroconf
EV: **TYK_GW_DISABLEDASHBOARDZEROCONF**<br />
Type: `bool`<br />

Disable the capability of the Gateway to `autodiscover` the Dashboard through heartbeat messages via Redis. 
The goal of zeroconf is auto-discovery, so you do not have to specify the Tyk Dashboard address in `tyk.conf`.
In some specific cases, for example, when the Dashboard is bound to a public domain, not accessible inside an internal network, or similar, `disable_dashboard_zeroconf` can be set to true, in favour of directly specifying a Tyk Dashboard address.

### slave_options
The `slave_options` allow you to configure the RPC slave connection for MDCB installations.
These settings must be configured for every RPC slave/worker node.

### slave_options.use_rpc
EV: **TYK_GW_SLAVEOPTIONS_USERPC**<br />
Type: `bool`<br />

Set to `true` to connect a worker gateway using RPC.

### slave_options.use_ssl
EV: **TYK_GW_SLAVEOPTIONS_USESSL**<br />
Type: `bool`<br />

Set this option to `true` to use an SSL RPC connection.

### slave_options.ssl_insecure_skip_verify
EV: **TYK_GW_SLAVEOPTIONS_SSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

Set this option to `true` to allow the certificate validation (certificate chain and hostname) to be skipped.
This can be useful if you use a self-signed certificate.

### slave_options.connection_string
EV: **TYK_GW_SLAVEOPTIONS_CONNECTIONSTRING**<br />
Type: `string`<br />

Use this setting to add the URL for your MDCB or load balancer host.

### slave_options.rpc_key
EV: **TYK_GW_SLAVEOPTIONS_RPCKEY**<br />
Type: `string`<br />

Your organisation ID to connect to the MDCB installation.

### slave_options.api_key
EV: **TYK_GW_SLAVEOPTIONS_APIKEY**<br />
Type: `string`<br />

The user should be a standard Dashboard user with minimal privileges so as to reduce risk if compromised.
The suggested security settings are read for Real-time notifications and the remaining options set to deny.

### slave_options.enable_rpc_cache
EV: **TYK_GW_SLAVEOPTIONS_ENABLERPCCACHE**<br />
Type: `bool`<br />

Set this option to `true` to enable RPC caching for keys.

### slave_options.group_id
EV: **TYK_GW_SLAVEOPTIONS_GROUPID**<br />
Type: `string`<br />

This is the `zone` that this instance inhabits, e.g. the cluster/data-centre the Gateway lives in. 
The group ID must be the same across all the Gateways of a data-centre/cluster which are also sharing the same Redis instance.
This ID should also be unique per cluster (otherwise another Gateway cluster can pick up your keyspace events and your cluster will get zero updates).

### slave_options.call_timeout
EV: **TYK_GW_SLAVEOPTIONS_CALLTIMEOUT**<br />
Type: `int`<br />

Call Timeout allows to specify a time in seconds for the maximum allowed duration of a RPC call.

### slave_options.ping_timeout
EV: **TYK_GW_SLAVEOPTIONS_PINGTIMEOUT**<br />
Type: `int`<br />

The maximum time in seconds that a RPC ping can last.

### slave_options.rpc_pool_size
EV: **TYK_GW_SLAVEOPTIONS_RPCPOOLSIZE**<br />
Type: `int`<br />

The number of RPC connections in the pool, basically it creates a set of connections that you can re-use as needed.

### management_node
EV: **TYK_GW_MANAGEMENTNODE**<br />
Type: `bool`<br />

If set to `true`, distributed rate limiter will be disabled for this node, and it will be excluded from rate limit calculation.

{{< note success >}}
**Note**

If you set `db_app_conf_options.node_is_segmented` to `true` for multiple gateway nodes, you should ensure that `management_node` is set to false. 
This is to ensure visibility for the management node across all APIs.
{{< /note >}}

### enable_redis_rolling_limiter
EV: **TYK_GW_ENABLEREDISROLLINGLIMITER**<br />
Type: `bool`<br />

Redis based rate limiter with fixed window. Provides 100% rate limiting accuracy, but require two additional Redis roundtrip for each request.

### enable_sentinel_rate_limiter
EV: **TYK_GW_ENABLESENTINELRATELIMITER**<br />
Type: `bool`<br />

The standard rate limiter offers similar performance as the sentinel-based limiter. This is disabled by default.

### enable_non_transactional_rate_limiter
EV: **TYK_GW_ENABLENONTRANSACTIONALRATELIMITER**<br />
Type: `bool`<br />

Enchancment for the Redis and Sentinel rate limiters, which that offers a significant improvement in performance by not using transactions on Redis rate-limit buckets.

### drl_notification_frequency
EV: **TYK_GW_DRLNOTIFICATIONFREQUENCY**<br />
Type: `int`<br />

How frequently distributed rate limiter synchronise information between the gateway nodes. Default: 2 seconds.

### drl_threshold
EV: **TYK_GW_DRLTHRESHOLD**<br />
Type: `float64`<br />

Distributed rate limiter is inaccurate on small rate limits, thus it will fallback to Redis or Sentinel rate limiter on individual user basis, if its rate limiter lower then threshold.
Rate limiter threshold calculated using the following formula: `rate_threshold = drl_threshold * number_of_gateways`. 
So you have 2 gateways, and threshold is 5, if user rate limit is bigger then 10, it will use distributed rate limiter algorithm.
Default: 5

### drl_enable_sentinel_rate_limiter
EV: **TYK_GW_DRLENABLESENTINELRATELIMITER**<br />
Type: `bool`<br />

Controls which algorthm to use as fallback when distributed rate limiter can't be used.

### enforce_org_data_age
EV: **TYK_GW_ENFORCEORGDATAAGE**<br />
Type: `bool`<br />

Allow dynamically configure analytics expiration on per organisation level 

### enforce_org_data_detail_logging
EV: **TYK_GW_ENFORCEORGDATADETAILLOGGING**<br />
Type: `bool`<br />

Allow dynamically configure detailed logging on per organisation level 

### enforce_org_quotas
EV: **TYK_GW_ENFORCEORGQUOTAS**<br />
Type: `bool`<br />

Allow dynamically configure organisation quotas on per organisation level 

### monitor
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
```

### monitor.enable_trigger_monitors
EV: **TYK_GW_MONITOR_ENABLETRIGGERMONITORS**<br />
Type: `bool`<br />

Set this to `true` to have monitors enabled in your configuration for the node.

### monitor.configuration.method
EV: **TYK_GW_MONITOR_CONFIG_METHOD**<br />
Type: `string`<br />

The method to use for the webhook.

### monitor.configuration.target_path
EV: **TYK_GW_MONITOR_CONFIG_TARGETPATH**<br />
Type: `string`<br />

The target path on which to send the request.

### monitor.configuration.template_path
EV: **TYK_GW_MONITOR_CONFIG_TEMPLATEPATH**<br />
Type: `string`<br />

The template to load in order to format the request.

### monitor.configuration.header_map
EV: **TYK_GW_MONITOR_CONFIG_HEADERLIST**<br />
Type: `map[string]string`<br />

Headers to set when firing the webhook.

### monitor.configuration.event_timeout
EV: **TYK_GW_MONITOR_CONFIG_EVENTTIMEOUT**<br />
Type: `int64`<br />

The cool-down for the event so it does not trigger again (in seconds).

### monitor.global_trigger_limit
EV: **TYK_GW_MONITOR_GLOBALTRIGGERLIMIT**<br />
Type: `float64`<br />

The trigger limit, as a percentage of the quota that must be reached in order to trigger the event, any time the quota percentage is increased the event will trigger.

### monitor.monitor_user_keys
EV: **TYK_GW_MONITOR_MONITORUSERKEYS**<br />
Type: `bool`<br />

Apply the monitoring subsystem to user keys.

### monitor.monitor_org_keys
EV: **TYK_GW_MONITOR_MONITORORGKEYS**<br />
Type: `bool`<br />

Apply the monitoring subsystem to organisation keys.

### max_idle_connections
EV: **TYK_GW_MAXIDLECONNS**<br />
Type: `int`<br />

Maximum idle connections, per API, between Tyk and Upstream. By default not limited.

### max_idle_connections_per_host
EV: **TYK_GW_MAXIDLECONNSPERHOST**<br />
Type: `int`<br />

Maximum idle connections, per API, per upstream, between Tyk and Upstream. Default: 100

### max_conn_time
EV: **TYK_GW_MAXCONNTIME**<br />
Type: `int64`<br />

Maximum connection time. If set it will force gateway reconnect to the upstream. 

### close_connections
EV: **TYK_GW_CLOSECONNECTIONS**<br />
Type: `bool`<br />

If set, disable keepalive between User and Tyk

### enable_custom_domains
EV: **TYK_GW_ENABLECUSTOMDOMAINS**<br />
Type: `bool`<br />

Allow use of custom domains

### allow_master_keys
EV: **TYK_GW_ALLOWMASTERKEYS**<br />
Type: `bool`<br />

If AllowMasterKeys is set to true, session objects (key definitions) that do not have explicit access rights set
will be allowed by Tyk. This means that keys that are created have access to ALL APIs, which in many cases is
unwanted behaviour unless you are sure about what you are doing.

### service_discovery.default_cache_timeout
EV: **TYK_GW_SERVICEDISCOVERY_DEFAULTCACHETIMEOUT**<br />
Type: `int`<br />

Service discovery cache timeout

### proxy_ssl_insecure_skip_verify
EV: **TYK_GW_PROXYSSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

Globally ignore TLS verification between Tyk and Upstream 

### proxy_enable_http2
EV: **TYK_GW_PROXYENABLEHTTP2**<br />
Type: `bool`<br />

Enable HTTP2 support between Tyk and Upstream. Required for gRPC.

### proxy_ssl_min_version
EV: **TYK_GW_PROXYSSLMINVERSION**<br />
Type: `uint16`<br />

Minimum TLS version for connection between Tyk and Upstream.

### proxy_ssl_max_version
EV: **TYK_GW_PROXYSSLMAXVERSION**<br />
Type: `uint16`<br />

Maximum TLS version for connection between Tyk and Upstream.

### proxy_ssl_ciphers
EV: **TYK_GW_PROXYSSLCIPHERSUITES**<br />
Type: `[]string`<br />

Whitelist ciphers for connection between Tyk and Upstream.

### proxy_default_timeout
EV: **TYK_GW_PROXYDEFAULTTIMEOUT**<br />
Type: `float64`<br />

This can specify a default timeout in seconds for upstream API requests.

### proxy_ssl_disable_renegotiation
EV: **TYK_GW_PROXYSSLDISABLERENEGOTIATION**<br />
Type: `bool`<br />

Disable TLS renegotiation.

### proxy_close_connections
EV: **TYK_GW_PROXYCLOSECONNECTIONS**<br />
Type: `bool`<br />

Disable keepalives between Tyk and Upstream.
Set this value to true to force Tyk to close the connection with the server, otherwise the connections will remain open for as long as your OS keeps TCP connections open. 
This can cause a file-handler limit to be exceeded. Setting to false can have performance benefits as the connection can be reused.

### uptime_tests
Tyk nodes can provide uptime awareness, uptime testing and analytics for your underlying APIs uptime and availability.
Tyk can also notify you when a service goes down.

### uptime_tests.disable
EV: **TYK_GW_UPTIMETESTS_DISABLE**<br />
Type: `bool`<br />

To disable uptime tests on this node, switch this value to true.

### uptime_tests.poller_group
EV: **TYK_GW_UPTIMETESTS_POLLERGROUP**<br />
Type: `string`<br />

If you have multiple Gateway clusters connected to the same Redis, you need to set uniq poller group for each cluster.

### uptime_tests.config.failure_trigger_sample_size
EV: **TYK_GW_UPTIMETESTS_CONFIG_FAILURETRIGGERSAMPLESIZE**<br />
Type: `int`<br />

The sample size to trigger a `HostUp` or `HostDown` event, e.g. a setting of 3 will require at least three failures to occur before the uptime test is triggered.

### uptime_tests.config.time_wait
EV: **TYK_GW_UPTIMETESTS_CONFIG_TIMEWAIT**<br />
Type: `int`<br />

The amount of seconds between tests runs, all tests will run simultaneously, this value will set the periodicity between those tests. e.g. A value of 60 will run all uptime tests every 60 seconds.

### uptime_tests.config.checker_pool_size
EV: **TYK_GW_UPTIMETESTS_CONFIG_CHECKERPOOLSIZE**<br />
Type: `int`<br />

The goroutine pool size to keep idle for uptime tests, if you have many uptime tests running at a high periodicity, then make this value higher.

### uptime_tests.config.enable_uptime_analytics
EV: **TYK_GW_UPTIMETESTS_CONFIG_ENABLEUPTIMEANALYTICS**<br />
Type: `bool`<br />

Set this value to true to have the node capture and record analytics data regarding the uptime tests.

### health_check
This section enables the configuration of the health-check API endpoint and the size of the sample data cache (in seconds).

### health_check.enable_health_checks
EV: **TYK_GW_HEALTHCHECK_ENABLEHEALTHCHECKS**<br />
Type: `bool`<br />

Setting this value to true will enable the health-check endpoint on /Tyk/health.

### health_check.health_check_value_timeouts
EV: **TYK_GW_HEALTHCHECK_HEALTHCHECKVALUETIMEOUT**<br />
Type: `int64`<br />

This setting defaults to 60, this is the time window that Tyk will use to sample health-check data.
Increase this value for more accurate data (larger sample period), and decrease for less accurate.
The reason this value is configurable is because sample data takes up space in your Redis DB to store the data to calculate samples, on high-availability systems this may not be desirable and smaller values may be preferred.

### health_check_endpoint_name
EV: **TYK_GW_HEALTHCHECKENDPOINTNAME**<br />
Type: `string`<br />

Way to rename the /hello endpoint

### oauth_refresh_token_expire
EV: **TYK_GW_OAUTHREFRESHEXPIRE**<br />
Type: `int64`<br />

Change the expiry time of refresh token, by default 14 days (in seconds).

### oauth_token_expire
EV: **TYK_GW_OAUTHTOKENEXPIRE**<br />
Type: `int32`<br />

Change the expiry time of OAuth token (in seconds).

### oauth_token_expired_retain_period
EV: **TYK_GW_OAUTHTOKENEXPIREDRETAINPERIOD**<br />
Type: `int32`<br />

Specifies how long expired tokens are stored in Redis. The value is in seconds and the default is 0. Using the default means expired tokens are never removed from Redis.

### oauth_redirect_uri_separator
EV: **TYK_GW_OAUTHREDIRECTURISEPARATOR**<br />
Type: `string`<br />

Character which should be used as a separator for oauth redirect uri urls. Default: ;.

### oauth_error_status_code
EV: **TYK_GW_OAUTHERRORSTATUSCODE**<br />
Type: `int`<br />

Configure the OAuth error status code returned. If not set, it defaults to a 403 error.

### enable_key_logging
EV: **TYK_GW_ENABLEKEYLOGGING**<br />
Type: `bool`<br />

By default all key ids in logs are hidden. Turn it on if you want to see them for debugging reasons.

### ssl_force_common_name_check
EV: **TYK_GW_SSLFORCECOMMONNAMECHECK**<br />
Type: `bool`<br />

Force validation of the hostname against the common name, even if TLS verification is disabled.

### enable_analytics
EV: **TYK_GW_ENABLEANALYTICS**<br />
Type: `bool`<br />

Tyk is capable of recording every hit to your API into a database with various filtering parameters, set this value to true and fill in the sub-section below to enable logging.

{{< note success >}}
**Note**

For performance reasons, Tyk will store traffic data to Redis initially and then purge the data from Redis to MongoDB or other, data stores, on a regular basis as determined by the purge_delay setting in your Tyk Pump configuration.
{{< /note >}}

### analytics_storage.type
EV: **TYK_GW_ANALYTICSSTORAGE_TYPE**<br />
Type: `string`<br />

This should be set to `redis` (lowercase)

### analytics_storage.host
EV: **TYK_GW_ANALYTICSSTORAGE_HOST**<br />
Type: `string`<br />

The Redis host, by default this is set to `localhost`, but for production this should be set to a cluster.

### analytics_storage.port
EV: **TYK_GW_ANALYTICSSTORAGE_PORT**<br />
Type: `int`<br />

The Redis instance port.

### analytics_storage.master_name
EV: **TYK_GW_ANALYTICSSTORAGE_MASTERNAME**<br />
Type: `string`<br />

Redis sentinel master name

### analytics_storage.sentinel_password
EV: **TYK_GW_ANALYTICSSTORAGE_SENTINELPASSWORD**<br />
Type: `string`<br />

Redis sentinel password

### analytics_storage.username
EV: **TYK_GW_ANALYTICSSTORAGE_USERNAME**<br />
Type: `string`<br />

Redis user name

### analytics_storage.password
EV: **TYK_GW_ANALYTICSSTORAGE_PASSWORD**<br />
Type: `string`<br />

If your Redis instance has a password set for access, you can tell Tyk about it here.

### analytics_storage.database
EV: **TYK_GW_ANALYTICSSTORAGE_DATABASE**<br />
Type: `int`<br />

Redis database

### analytics_storage.optimisation_max_idle
EV: **TYK_GW_ANALYTICSSTORAGE_MAXIDLE**<br />
Type: `int`<br />

Set the number of maximum idle connections in the Redis connection pool, which defaults to 100. Set to higher if you are expecting more traffic.

### analytics_storage.optimisation_max_active
EV: **TYK_GW_ANALYTICSSTORAGE_MAXACTIVE**<br />
Type: `int`<br />

Set the number of maximum connections in the Redis connection pool, which defaults to 500. Set to higher if you are expecting more traffic.

### analytics_storage.timeout
EV: **TYK_GW_ANALYTICSSTORAGE_TIMEOUT**<br />
Type: `int`<br />

Set cutom timeout for Redis network operations. Default value 5 seconds.

### analytics_storage.enable_cluster
EV: **TYK_GW_ANALYTICSSTORAGE_ENABLECLUSTER**<br />
Type: `bool`<br />

Enable Redis Cluster support

### analytics_storage.use_ssl
EV: **TYK_GW_ANALYTICSSTORAGE_USESSL**<br />
Type: `bool`<br />

Enable SSL/TLS connection between Tyk Gateway & Redis.

### analytics_storage.ssl_insecure_skip_verify
EV: **TYK_GW_ANALYTICSSTORAGE_SSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

Disable TLS verification

### dns_cache
Cache

### cache_storage.type
EV: **TYK_GW_CACHESTORAGE_TYPE**<br />
Type: `string`<br />

This should be set to `redis` (lowercase)

### cache_storage.host
EV: **TYK_GW_CACHESTORAGE_HOST**<br />
Type: `string`<br />

The Redis host, by default this is set to `localhost`, but for production this should be set to a cluster.

### cache_storage.port
EV: **TYK_GW_CACHESTORAGE_PORT**<br />
Type: `int`<br />

The Redis instance port.

### cache_storage.master_name
EV: **TYK_GW_CACHESTORAGE_MASTERNAME**<br />
Type: `string`<br />

Redis sentinel master name

### cache_storage.sentinel_password
EV: **TYK_GW_CACHESTORAGE_SENTINELPASSWORD**<br />
Type: `string`<br />

Redis sentinel password

### cache_storage.username
EV: **TYK_GW_CACHESTORAGE_USERNAME**<br />
Type: `string`<br />

Redis user name

### cache_storage.password
EV: **TYK_GW_CACHESTORAGE_PASSWORD**<br />
Type: `string`<br />

If your Redis instance has a password set for access, you can tell Tyk about it here.

### cache_storage.database
EV: **TYK_GW_CACHESTORAGE_DATABASE**<br />
Type: `int`<br />

Redis database

### cache_storage.optimisation_max_idle
EV: **TYK_GW_CACHESTORAGE_MAXIDLE**<br />
Type: `int`<br />

Set the number of maximum idle connections in the Redis connection pool, which defaults to 100. Set to higher if you are expecting more traffic.

### cache_storage.optimisation_max_active
EV: **TYK_GW_CACHESTORAGE_MAXACTIVE**<br />
Type: `int`<br />

Set the number of maximum connections in the Redis connection pool, which defaults to 500. Set to higher if you are expecting more traffic.

### cache_storage.timeout
EV: **TYK_GW_CACHESTORAGE_TIMEOUT**<br />
Type: `int`<br />

Set cutom timeout for Redis network operations. Default value 5 seconds.

### cache_storage.enable_cluster
EV: **TYK_GW_CACHESTORAGE_ENABLECLUSTER**<br />
Type: `bool`<br />

Enable Redis Cluster support

### cache_storage.use_ssl
EV: **TYK_GW_CACHESTORAGE_USESSL**<br />
Type: `bool`<br />

Enable SSL/TLS connection between Tyk Gateway & Redis.

### cache_storage.ssl_insecure_skip_verify
EV: **TYK_GW_CACHESTORAGE_SSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

Disable TLS verification

### enable_bundle_downloader
EV: **TYK_GW_ENABLEBUNDLEDOWNLOADER**<br />
Type: `bool`<br />

Middleware/Plugin Configuration

### log_level
EV: **TYK_GW_LOGLEVEL**<br />
Type: `string`<br />

Monitoring, Logging & Profiling

### tracing.name
EV: **TYK_GW_TRACER_NAME**<br />
Type: `string`<br />

The name of the tracer to initialize. For instance appdash, to use appdash tracer

### tracing.enabled
EV: **TYK_GW_TRACER_ENABLED**<br />
Type: `bool`<br />

Enable tracing

### tracing.options
EV: **TYK_GW_TRACER_OPTIONS**<br />
Type: `map[string]interface{}`<br />

Tracing configuration. Refer to the Tracing Docs for the full list of options.

### newrelic.app_name
EV: **TYK_GW_NEWRELIC_APPNAME**<br />
Type: `string`<br />

New Relic Application name

### newrelic.license_key
EV: **TYK_GW_NEWRELIC_LICENSEKEY**<br />
Type: `string`<br />

New Relic License key

### event_handlers
Event System

### hide_generator_header
EV: **TYK_GW_HIDEGENERATORHEADER**<br />
Type: `bool`<br />

HideGeneratorHeader will mask the 'X-Generator' and 'X-Mascot-...' headers, if set to true.

### suppress_default_org_store
EV: **TYK_GW_SUPRESSDEFAULTORGSTORE**<br />
Type: `bool`<br />

TODO: These config options are not documented - What do they do?

### kv.consul.address
EV: **TYK_GW_KV_CONSUL_ADDRESS**<br />
Type: `string`<br />

Address is the address of the Consul server

### kv.consul.scheme
EV: **TYK_GW_KV_CONSUL_SCHEME**<br />
Type: `string`<br />

Scheme is the URI scheme for the Consul server

### kv.consul.datacenter
EV: **TYK_GW_KV_CONSUL_DATACENTER**<br />
Type: `string`<br />

Datacenter to use. If not provided, the default agent datacenter is used.

### kv.consul.http_auth.username
EV: **TYK_GW_KV_CONSUL_HTTPAUTH_USERNAME**<br />
Type: `string`<br />

Username to use for HTTP Basic Authentication

### kv.consul.http_auth.password
EV: **TYK_GW_KV_CONSUL_HTTPAUTH_PASSWORD**<br />
Type: `string`<br />

Password to use for HTTP Basic Authentication

### kv.vault.token
EV: **TYK_GW_KV_VAULT_TOKEN**<br />
Type: `string`<br />

Token is the vault root token

### kv.vault.kv_version
EV: **TYK_GW_KV_VAULT_KVVERSION**<br />
Type: `int`<br />

KVVersion is the version number of Vault. Usually defaults to 2

### secrets
EV: **TYK_GW_SECRETS**<br />
Type: `map[string]string`<br />

Secrets are key-value pairs that can be accessed in the dashboard via "secrets://"

### override_messages
OverrideMessages is used to override returned API error codes and messages.

### cloud
EV: **TYK_GW_CLOUD**<br />
Type: `bool`<br />

Cloud flag shows that gateway runs in Tyk-cloud.

### jwt_ssl_insecure_skip_verify
EV: **TYK_GW_JWTSSLINSECURESKIPVERIFY**<br />
Type: `bool`<br />

SSL options for JWT middleware.

