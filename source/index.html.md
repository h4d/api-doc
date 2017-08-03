---
title: API Reference

language_tabs:
- shell
- php

toc_footers:
- <a href='https://hosting4devs.com'>Manage servers and web apps easily</a>
- <a href='https://cloud.hosting4devs.com/signup'>Sign Up</a>
- <a href='https://github.com/tripit/slate'>Doc Powered by Slate</a>

includes:
- errors

search: true
---
# Introduction

Welcome to the hosting4devs API! You can use our API to manage your servers.

We have language bindings in Shell and PHP! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/tripit/slate).

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.hosting4devs.com"
-u apiUser:apiPassword
```

```php
$user = 'apiUser';
$pass = 'apiPassword';

try
{
    // Configure your http client && set proper adaptor
    $httpClient = new DefaultClient();
    $httpClient->setAuthentication($user, $pass);
    $adaptor = new DefaultAdaptor($httpClient);

    // Pass the http adaptor to API client
    $client = new \H4D\ApiClient\Client($adaptor);

```

> Make sure to replace `apiUser` & `apiPassword` with your API auth data.

<aside class="notice">
    You must replace <code>apiUser</code> & <code>apiPassword</code> with your hosting4devs API auth data.
</aside>

#Server
## Get detailed server info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/info" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedServerInfo($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "metrics": {
            "uptime": "7982867.14",
            "load_avg": {
                "last": 0,
                "5min": 0,
                "15min": 0,
                "nproc": "1"
            },
            "memory_usage": {
                "total": "500388",
                "used": "480292",
                "free": "20096",
                "shared": "46564",
                "buffers": "34748",
                "cached": "144768",
                "unit": "KB"
            },
            "filesystems_usage": {
                "\/": {
                    "total": "20030",
                    "used": "4905",
                    "free": "14095",
                    "percentage_of_use": "26",
                    "filesystem": "\/dev\/vda1",
                    "type": "ext4",
                    "unit": "MB"
                }
            }
        },
        "network": {
            "eth0": {
                "IPv4": "10.14.0.7",
                "IPv6": "fe80::601:18ff:fe89:9f01"
            }
        },
        "services": {
            "count": 11,
            "items": {
                "vsftpd": {
                    "serviceName": "vsftpd",
                    "publicName": "ftp",
                    "isEnabled": true,
                    "isRunning": true
                },
                "ssh": {
                    "serviceName": "ssh",
                    "publicName": "ssh",
                    "isEnabled": true,
                    "isRunning": true
                },
                "spamassassin": {
                    "serviceName": "spamassassin",
                    "publicName": "antispam",
                    "isEnabled": true,
                    "isRunning": true
                },
                "postfix": {
                    "serviceName": "postfix",
                    "publicName": "postfix",
                    "isEnabled": true,
                    "isRunning": true
                },
                "dovecot": {
                    "serviceName": "dovecot",
                    "publicName": "dovecot",
                    "isEnabled": true,
                    "isRunning": true
                },
                "mysql": {
                    "serviceName": "mysql",
                    "publicName": "mysql",
                    "isEnabled": true,
                    "isRunning": true
                },
                "apache2": {
                    "serviceName": "apache2",
                    "publicName": "apache",
                    "isEnabled": true,
                    "isRunning": true
                },
                "h4d-metrics": {
                    "serviceName": "h4d-metrics",
                    "publicName": "metrics",
                    "isEnabled": true,
                    "isRunning": true
                },
                "h4d-php5.5-fpm": {
                    "serviceName": "h4d-php5.5-fpm",
                    "publicName": "php5.5-fpm",
                    "isEnabled": true,
                    "isRunning": true
                },
                "h4d-php5.6-fpm": {
                    "serviceName": "h4d-php5.6-fpm",
                    "publicName": "php5.6-fpm",
                    "isEnabled": true,
                    "isRunning": true
                },
                "h4d-php7-fpm": {
                    "serviceName": "h4d-php7-fpm",
                    "publicName": "php7-fpm",
                    "isEnabled": true,
                    "isRunning": true
                }
            }
        },
        "packages": {
            "count": 10,
            "items": [
                {
                    "package": "apache",
                    "version": "2.4.16",
                    "installed": "2016-12-23T09:47:14+0000"
                },
                {
                    "package": "mysql",
                    "version": "5.5.43",
                    "installed": "2016-12-23T10:02:21+0000"
                },
                {
                    "package": "php7-fpm",
                    "version": "7.0",
                    "installed": "2016-12-23T10:03:06+0000"
                },
                {
                    "package": "php5.6-fpm",
                    "version": "5.6",
                    "installed": "2016-12-23T10:09:09+0000"
                },
                {
                    "package": "php5.5-fpm",
                    "version": "5.5",
                    "installed": "2016-12-23T10:09:47+0000"
                },
                {
                    "package": "ftp",
                    "version": "3.0.2",
                    "installed": "2016-12-23T10:18:59+0000"
                },
                {
                    "package": "ssh",
                    "version": "6.6p1",
                    "installed": "2016-12-23T10:18:59+0000"
                },
                {
                    "package": "postfix",
                    "version": "2.11.0",
                    "installed": "2017-01-17T08:22:10+0000"
                },
                {
                    "package": "dovecot",
                    "version": "2.2.9",
                    "installed": "2017-01-17T08:22:10+0000"
                },
                {
                    "package": "spamassassin",
                    "version": "3.4.0",
                    "installed": "2017-01-17T08:22:10+0000"
                }
            ]
        },
        "time": {
            "timezone": "Etc\/UTC",
            "date": "2017-08-03T16:58:13+0000"
        },
        "hostings": {
            "count": "7"
        },
        "antispam": {
            "config": {
                "required_score": "10.0",
                "subject_tag": "[SPAM]"
            },
            "enable": true
        },
        "cpu": {
            "model": "Intel(R) Xeon(R) CPU E5-2630L 0 @ 2.00GHz",
            "nproc": "1"
        },
        "distro": {
            "id": "Ubuntu",
            "release": "14.04",
            "codename": "trusty",
            "description": "Ubuntu 14.04.5 LTS"
        },
        "kernel_release": "4.4.0-53-generic"
    }
}
```

Get detailed server info.

### HTTP Request

`GET  /v1/server/:server/info`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get detailed IPs info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/ips" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedIPsInfo($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get detailed IPs info.

### HTTP Request

`GET  /v1/server/:server/ips`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server disk usage.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/disk-usage" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerDiskUsage($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server disk usage.

### HTTP Request

`GET  /v1/server/:server/disk-usage`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server load average.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/load-average" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerLoadAverage($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server load average.

### HTTP Request

`GET  /v1/server/:server/load-average`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server memory usage.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/memory" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerMemoryUsage($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server memory usage.

### HTTP Request

`GET  /v1/server/:server/memory`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server services detailed info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/services-status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerServicesDetailedInfo($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "vsftpd": {
            "serviceName": "vsftpd",
            "publicName": "ftp",
            "isEnabled": true,
            "isRunning": true
        },
        "ssh": {
            "serviceName": "ssh",
            "publicName": "ssh",
            "isEnabled": true,
            "isRunning": true
        },
        "mysql": {
            "serviceName": "mysql",
            "publicName": "mysql",
            "isEnabled": true,
            "isRunning": true
        },
        "apache2": {
            "serviceName": "apache2",
            "publicName": "apache",
            "isEnabled": true,
            "isRunning": true
        },
        "h4d-metrics": {
            "serviceName": "h4d-metrics",
            "publicName": "metrics",
            "isEnabled": true,
            "isRunning": true
        },
        "h4d-php5.6-fpm": {
            "serviceName": "h4d-php5.6-fpm",
            "publicName": "php5.6-fpm",
            "isEnabled": true,
            "isRunning": true
        },
        "h4d-php7-fpm": {
            "serviceName": "h4d-php7-fpm",
            "publicName": "php7-fpm",
            "isEnabled": true,
            "isRunning": true
        }
    }
}
```

Get server services detailed info.

### HTTP Request

`GET  /v1/server/:server/services-status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server uptime.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/uptime" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerUptime($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server uptime.

### HTTP Request

`GET  /v1/server/:server/uptime`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get service information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/service/:service" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","service":"service"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServiceInformation($server,$service);
```

> The above command returns JSON structured like this:

```json
null
```

Get service information.

### HTTP Request

`GET  /v1/server/:server/service/:service`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
service | true | Service name | string | - | -

## Get installed packages.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/packages" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getInstalledPackages($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": [
        {
            "package": "apache",
            "version": "2.4.16",
            "installed": "2016-12-23T09:47:14+0000"
        },
        {
            "package": "mysql",
            "version": "5.5.43",
            "installed": "2016-12-23T10:02:21+0000"
        },
        {
            "package": "php7-fpm",
            "version": "7.0",
            "installed": "2016-12-23T10:03:06+0000"
        },
        {
            "package": "php5.6-fpm",
            "version": "5.6",
            "installed": "2016-12-23T10:09:09+0000"
        },
        {
            "package": "php5.5-fpm",
            "version": "5.5",
            "installed": "2016-12-23T10:09:47+0000"
        },
        {
            "package": "ftp",
            "version": "3.0.2",
            "installed": "2016-12-23T10:18:59+0000"
        },
        {
            "package": "ssh",
            "version": "6.6p1",
            "installed": "2016-12-23T10:18:59+0000"
        },
        {
            "package": "postfix",
            "version": "2.11.0",
            "installed": "2017-01-17T08:22:10+0000"
        },
        {
            "package": "dovecot",
            "version": "2.2.9",
            "installed": "2017-01-17T08:22:10+0000"
        },
        {
            "package": "spamassassin",
            "version": "3.4.0",
            "installed": "2017-01-17T08:22:10+0000"
        }
    ]
}
```

Get installed packages.

### HTTP Request

`GET  /v1/server/:server/packages`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get MySQL version.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/mysql/version" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMySQLVersion($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get MySQL version.

### HTTP Request

`GET  /v1/server/:server/mysql/version`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server spamassassin preferences.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/antispam" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerSpamassassinPreferences($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server spamassassin preferences.

### HTTP Request

`GET  /v1/server/:server/antispam`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Set server spamassassin preferences.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/antispam" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","tag":"tag","score":"score"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setServerSpamassassinPreferences($server,$tag,$score);
```

> The above command returns JSON structured like this:

```json
null
```

Set server spamassassin preferences.

### HTTP Request

`PUT  /v1/server/:server/antispam`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
tag | true | Tag for antispam preference | string | - | -
score | true | Score for antispam preference | string | - | -
## Get hostings.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hostings" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostings($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "example.com": {
            "domain": "example.com",
            "status": "enable",
            "server": "mYSeRvEr-Id",
            "processManager": "php-7",
            "created": "2016-12-23T10:10:19+0000",
            "modified": "2017-07-29T10:27:08+0000"
        },
        "php56.example.com": {
            "domain": "php56.example.com",
            "status": "enable",
            "server": "mYSeRvEr-Id",
            "processManager": "php-5.6",
            "created": "2016-12-23T10:10:33+0000",
            "modified": "2016-12-23T10:10:33+0000"
        },
        "php55.example.com": {
            "domain": "php55.example.com",
            "status": "enable",
            "server": "mYSeRvEr-Id",
            "processManager": "php-5.5",
            "created": "2016-12-23T10:10:47+0000",
            "modified": "2016-12-23T10:10:47+0000"
        },
        "blog.example.com": {
            "domain": "blog.example.com",
            "status": "enable",
            "server": "mYSeRvEr-Id",
            "processManager": "php-7",
            "created": "2017-04-16T17:49:53+0000",
            "modified": "2017-04-26T06:47:31+0000"
        },
        "test.example.com": {
            "domain": "test.example.com",
            "status": "enable",
            "server": "mYSeRvEr-Id",
            "processManager": "php-7",
            "created": "2017-05-10T17:02:07+0000",
            "modified": "2017-05-10T17:02:07+0000"
        }
    }
}
```

Get hostings.

### HTTP Request

`GET  /v1/server/:server/hostings`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get detailed hostings info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hostings-info" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedHostingsInfo($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get detailed hostings info.

### HTTP Request

`GET  /v1/server/:server/hostings-info`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Set MySQL root password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/mysql/root-password" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","password":"password"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setRootPassword($server,$password);
```

> The above command returns JSON structured like this:

```json
null
```

Set MySQL root password.

### HTTP Request

`PUT  /v1/server/:server/mysql/root-password`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
password | true | Password | string | - | -
## Add new firewall rule.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/rule" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","priority":"priority","source":"source","destination":"destination","sourcePort":"sourcePort","destinationPort":"destinationPort","direction":"direction","action":"action","protocol":"protocol","replace":"replace"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addFirewallRule($server,$priority,$source,$destination,$sourcePort,$destinationPort,$direction,$action,$protocol,$replace);
```

> The above command returns JSON structured like this:

```json
null
```

Add new firewall rule.

### HTTP Request

`POST  /v1/server/:server/firewall/rule`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
priority | true | Priority | string | - | -
source | true | Source IP or Subnet | string | - | -
destination | true | Destination IP or Subnet | string | - | -
sourcePort | true | Source port | string | - | all
destinationPort | true | Destination port | string | - | all
direction | true | Direction | enum | ["INPUT","OUTPUT"] | INPUT
action | true | Action | enum | ["ACCEPT","DROP"] | ACCEPT
protocol | true | Protocol | enum | ["tcp","udp","udplite","icmp","icmpv6","esp","ah","sctp","mh","all"] | tcp
replace | true | Replace | boolean | [true,false] | 1
## Get firewall rules.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/rules" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getFirewallRules($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": []
}
```

Get firewall rules.

### HTTP Request

`GET  /v1/server/:server/firewall/rules`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Remove firewall rule.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/rule" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","priority":"priority","direction":"direction"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->removeFirewallRule($server,$priority,$direction);
```

> The above command returns JSON structured like this:

```json
null
```

Remove firewall rule.

### HTTP Request

`DELETE  /v1/server/:server/firewall/rule`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
priority | true | Priority | string | - | -
direction | true | Direction | enum | ["INPUT","OUTPUT"] | INPUT
## Block IP.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/block/:ip" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","ip":"1.2.3.4"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->firewallDisallowIP($server,$ip);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Block IP.

### HTTP Request

`PUT  /v1/server/:server/firewall/block/:ip`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
ip | true | Source IP or subnet | string | - | -

## Unblock IP.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/block/:ip" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","ip":"ip"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->firewallRemoveDisallowedIP($server,$ip);
```

> The above command returns JSON structured like this:

```json
null
```

Unblock IP.

### HTTP Request

`DELETE  /v1/server/:server/firewall/block/:ip`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
ip | true | Source IP or subnet | string | - | -

## Get server time information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/time" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerTimeInformation($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server time information.

### HTTP Request

`GET  /v1/server/:server/time`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Set server timezone.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/time/timezone" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","timezone":"Europe\/Madrid"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setServerTimezone($server,$timezone);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Set server timezone.

### HTTP Request

`PUT  /v1/server/:server/time/timezone`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
timezone | true | Timezone | string | - | -
## Get detailed server settings.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/settings" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedServerSettings($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get detailed server settings.

### HTTP Request

`GET  /v1/server/:server/settings`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Manage server service status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/service/:service/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","service":"spamassassin","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->manageServerServiceStatus($server,$service,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Manage server service status.

### HTTP Request

`PUT  /v1/server/:server/service/:service/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
service | true | Service name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Manage server service.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/service/:service/command" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","service":"h4d-php5.6-fpm","action":"restart"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->manageServerService($server,$service,$action);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Manage server service.

### HTTP Request

`PUT  /v1/server/:server/service/:service/command`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
service | true | Service name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
action | true | Action | enum | ["start","stop","restart","reload"] | start
## Get full list of active servers.
```shell
curl "https://api.hosting4devs.com/v1/server/list-full" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getActiveServersFullList();
```

> The above command returns JSON structured like this:

```json
null
```

Get full list of active servers.

### HTTP Request

`GET  /v1/server/list-full`


## Get list of active servers.
```shell
curl "https://api.hosting4devs.com/v1/server/list" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getActiveServersList();
```

> The above command returns JSON structured like this:

```json
null
```

Get list of active servers.

### HTTP Request

`GET  /v1/server/list`


## Get deploy information by token.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/deployments/:token" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getGitDeployInfoByToken($server,$token);
```

> The above command returns JSON structured like this:

```json
null
```

Get deploy information by token.

### HTTP Request

`GET  /v1/server/:server/deployments/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
token | true | Deploy token | string | - | -

## Get git deployments info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/deployments/git" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getGitDeploymentsInfo($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get git deployments info.

### HTTP Request

`GET  /v1/server/:server/deployments/git`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Run the deploy identified by the given deploy token.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/run-deploy" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->runGitDeployment($server,$token);
```

> The above command returns JSON structured like this:

```json
null
```

Run the deploy identified by the given deploy token (git clone for new deploys, git pull for existing deploys).

### HTTP Request

`PUT  /v1/server/:server/run-deploy`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
token | true | Deploy token | string | - | -
## Install hosting addon.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/addon" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","addonName":"phpmyadmin","publicPath":"pma","settings":[]}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->installAddon($server,$domain,$addonName,$publicPath,$settings);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "ea87040fee0ef5d3cabc365ebd308ef0"
}
```

Install and setup a hosting addon.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/addon`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
addonName | true | Addon name | string | - | -
publicPath | true | Public URL path | string | - | -
settings | false | Addon settings | string | - | -
## Reboot server.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/reboot" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->rebootServer($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "101d0cc55760ef932a2d02ddb5a12485"
}
```

Reboot server.

### HTTP Request

`POST  /v1/server/:server/reboot`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Uninstall H4DCS and remove the server from hosting4devs platform.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/uninstall" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->uninstallH4DCS($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "8caeffdadc87ed289318a7289652f6d8"
}
```

Uninstall H4DCS and remove your server from hosting4devs platform. This action does not delete any data from your server, however you will no longer be able to manage the server, its apps, or its databases through hosting4devs platform.

### HTTP Request

`DELETE  /v1/server/:server/uninstall`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

#Snippets
## Add new snippet.
```shell
curl "https://api.hosting4devs.com/v1/snippet" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"title":"free","code":"free","interpreter":"BASH","visibility":"PRIVATE","notes":""}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->publishSnippet($title,$code,$interpreter,$visibility,$notes);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "9c7f4649f7b390091d85b052042fb600"
}
```

Add new snippet.

### HTTP Request

`POST  /v1/snippet`


### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
title | true | Snippet title | string | - | -
code | true | Snippet code | string | - | -
interpreter | true | Snippet interpreter | enum | ["BASH","PHP","PYTHON"] | BASH
visibility | true | Snippet visibility | enum | ["PRIVATE","PROTECTED","PUBLIC"] | PRIVATE
notes | false | Notes about the snippet | string | - | 
## Delete snippet by token.
```shell
curl "https://api.hosting4devs.com/v1/snippet/:token" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"token":"8b220f9629cb4e5fbbdb2ca914bbbde4"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSnippetByToken($token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Delete snippet by token.

### HTTP Request

`DELETE  /v1/snippet/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
token | true | Snippet token | string | - | -

## Get snippet by token.
```shell
curl "https://api.hosting4devs.com/v1/snippet/:token" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"token":"8cfb6ea983807b096ed07cc4f559fce9"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getSnippetByToken($token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "title": "ps -aux",
        "notes": "",
        "visibility": "PRIVATE",
        "interpreter": "BASH",
        "token": "8cfb6ea983807b096ed07cc4f559fce9",
        "code": "cHMgLWF1eA==",
        "status": "ACTIVE",
        "createdAt": "2016-12-22T12:22:31Z",
        "updatedAt": "2016-12-22T12:22:31Z",
        "executionsCount": 8,
        "lastExecution": {
            "slave": "asQnPb-002",
            "executionToken": "dcfd024aadb76d649f2ee62c01cd95e7",
            "startDate": "2017-06-02T12:32:11Z",
            "endDate": "2017-06-02T12:32:12Z",
            "stdOut": "BASE64OUTPUT",
            "stdErr": "",
            "terminationCode": 0,
            "status": "COMPLETED",
            "createdAt": "2017-06-02T12:32:11Z",
            "updatedAt": "2017-06-02T12:32:12Z"
        }
    }
}
```

Get snippet by token.

### HTTP Request

`GET  /v1/snippet/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
token | true | Snippet token | string | - | -

## Get snippet execution by execution token.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/snippet/:token" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","token":"dcfd024aadb76d649f2ee62c01cd95e7"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getSnippetExecutionInfo($server,$token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "slave": "asQnPb-002",
        "executionToken": "dcfd024aadb76d649f2ee62c01cd95e7",
        "startDate": "2017-06-02T12:32:11Z",
        "endDate": "2017-06-02T12:32:12Z",
        "stdOut": "BASE64OUTPUT",
        "stdErr": "",
        "terminationCode": 0,
        "status": "COMPLETED",
        "createdAt": "2017-06-02T12:32:11Z",
        "updatedAt": "2017-06-02T12:32:12Z",
        "snippet": {
            "title": "ps -aux",
            "notes": "",
            "visibility": "PRIVATE",
            "interpreter": "BASH",
            "token": "8cfb6ea983807b096ed07cc4f559fce9",
            "code": "cHMgLWF1eA==",
            "status": "ACTIVE",
            "createdAt": "2016-12-22T12:22:31Z",
            "updatedAt": "2016-12-22T12:22:31Z",
            "executionsCount": 8
        }
    }
}
```

Get snippet execution by execution token.

### HTTP Request

`GET  /v1/server/:server/snippet/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
token | true | Snippet execution token | string | - | -

## Get snippet executions.
```shell
curl "https://api.hosting4devs.com/v1/snippet/:token/executions" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"token":"27f0c9f5274d6f931f2c8676267866f8"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getSnippetExecutionsByToken($token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "snippet": {
            "title": "Process list",
            "notes": "O",
            "visibility": "PRIVATE",
            "interpreter": "BASH",
            "token": "27f0c9f5274d6f931f2c8676267866f8",
            "code": "cHMgLWF1eA==",
            "status": "ACTIVE",
            "createdAt": "2017-01-19T15:53:51Z",
            "updatedAt": "2017-01-19T15:53:51Z",
            "executionsCount": 4
        },
        "executions": [
            {
                "slave": "mYSeRvEr-Id",
                "executionToken": "0d32e3f7fa771c8ee6546923a19f7df0",
                "startDate": "2017-01-27T12:33:21Z",
                "endDate": "2017-01-27T12:33:21Z",
                "stdOut": "BASE64OUTPUT",
                "stdErr": "",
                "terminationCode": 0,
                "status": "COMPLETED",
                "createdAt": "2017-01-27T12:33:21Z",
                "updatedAt": "2017-01-27T12:33:21Z"
            }
        ]
    }
}
```

Get snippet executions.

### HTTP Request

`GET  /v1/snippet/:token/executions`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
token | true | Snippet token | string | - | -

## Get user snippets.
```shell
curl "https://api.hosting4devs.com/v1/snippets" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getUserSnippets();
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": []
}
```

Get user snippets.

### HTTP Request

`GET  /v1/snippets`


## Get user snippets execution queue.
```shell
curl "https://api.hosting4devs.com/v1/snippets/execution-queue" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getUserSnippetsExecutionQueue();
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": []
}
```

Get user snippets execution queue.

### HTTP Request

`GET  /v1/snippets/execution-queue`


## Mark a snippet execution as viewed.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/snippet/:token/viewed" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","token":"f322f17ecf893073c3f8074bad4042cd"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->markSnippetExecutionAsViewed($server,$token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Mark a snippet execution as viewed.

### HTTP Request

`PUT  /v1/server/:server/snippet/:token/viewed`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
token | true | Snippet token | string | - | -

## Update the snippet indetified by token.
```shell
curl "https://api.hosting4devs.com/v1/snippet/:token" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"token":"8e87a554c345512d819130bbaf8a4556","title":"Update PHP versions","code":"apt-get update\r\napt-get install -y h4d-php-7\r\napt-get install -y h4d-php-5.6\r\napt-get install -y h4d-php-5.5","interpreter":"BASH","visibility":"PRIVATE","notes":""}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->updateSnippet($token,$title,$code,$interpreter,$visibility,$notes);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Update the snippet indetified by token.

### HTTP Request

`PUT  /v1/snippet/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
token | true | Snippet token | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
title | true | Snippet title | string | - | -
code | true | Snippet code | string | - | -
interpreter | true | Snippet interpreter | enum | ["BASH","PHP","PYTHON"] | BASH
visibility | true | Snippet visibility | enum | ["PRIVATE","PROTECTED","PUBLIC"] | PRIVATE
notes | false | Notes about the snippet | string | - | 
## Execute a snippet with the given token.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/snippet/:token" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","token":"8cfb6ea983807b096ed07cc4f559fce9"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->executeSnippet($server,$token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "dcfd024aadb76d649f2ee62c01cd95e7"
}
```

Execute a snippet with the given token.

### HTTP Request

`PUT  /v1/server/:server/snippet/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
token | true | Snippet token | string | - | -

#Hosting
## Create new hosting.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","alias":"example.com","mailEnable":false,"processManager":"php-5.6","password":"*******","webRoot":"www"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createHosting($server,$domain,$alias,$mailEnable,$processManager,$password,$webRoot);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Create new hosting.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
alias | false | Alias | string | - | 
mailEnable | true | Enable mail service | boolean | [true,false] | 1
processManager | true | Process manager which handles requests | enum | ["php-5.5","php-5.6","php-7"] | php-5.5
password | false | Password | string | - | 
webRoot | false | Web document root | string | - | htdocs
## Change hosting password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/pass" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","password":"*******"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingPassword($server,$domain,$password);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Change hosting password.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/pass`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
password | true | Password | string | - | -
## Get hosting total disk usage.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/info/disk-usage" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingTotalDiskUsage($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting total disk usage.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/info/disk-usage`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting disk usage summary.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/info/disk-usage-sumary/deep/:deep" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","deep":"deep"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingDiskUsageSummary($server,$domain,$deep);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting disk usage summary.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/info/disk-usage-sumary/deep/:deep`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
deep | true | Deep (default value = 1) | string | - | -

## Get detailed information about a hosting.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/info" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingDetailedInformation($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "domain": "example.com",
        "status": "enable",
        "alias": "www.example.com",
        "ip": "*",
        "documentRoot": "\/home\/example.com\/htdocs",
        "description": null,
        "logDir": "\/home\/example.com\/logs",
        "server": "mYSeRvEr-Id",
        "processManager": "php-5.6",
        "processManagerOptions": [],
        "sslEnable": "disable",
        "mailEnable": "enable",
        "ftpEnabled": "enable",
        "sshEnabled": "enable",
        "sshAuthMode": "password",
        "quota": {
            "active": false,
            "soft": 0,
            "hard": 0,
            "unit": "KB"
        },
        "created": "2017-03-25T14:40:21+0000",
        "modified": "2017-04-16T14:57:54+0000",
        "systemUser": {
            "username": "username",
            "homeDir": "\/home\/example.com",
            "sshPubKey": ""
        },
        "mail": {
            "status": "enable",
            "alias": {
                "max": 0,
                "count": 0
            },
            "mailbox": {
                "max": 0,
                "count": 0
            },
            "mailDir": "\/home\/example.com\/Maildir",
            "created": "2017-04-16T14:57:54+0000",
            "modified": "2017-08-03T17:17:32+0000",
            "antispam": {
                "status": "enabled",
                "required_score": "10.0",
                "subject_tag": "[SPAM]"
            }
        },
        "db": {
            "status": {
                "mysql": "enabled"
            },
            "count": {
                "users": 0,
                "dbs": 0
            }
        },
        "sshKeys": [],
        "sslInfo": [],
        "gitDeploy": []
    }
}
```

Get detailed information about a hosting.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/info`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting quota.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/quota" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingQuota($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting quota.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/quota`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting status.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting FTP status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ftp/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingFTPStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting FTP status.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/ftp/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Set hosting FTP status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ftp/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","status":"disable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingFTPStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Set hosting FTP status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/ftp/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Get hosting mail service detailed information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailServiceDetailedInformation($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "status": "enable",
        "alias": {
            "max": 0,
            "count": 0,
            "items": []
        },
        "mailbox": {
            "max": 0,
            "count": 0,
            "items": []
        },
        "mailDir": "\/home\/example.com\/Maildir",
        "created": "2017-04-16T14:57:54+0000",
        "modified": "2017-07-15T15:42:25+0000",
        "antispam": {
            "status": "enabled",
            "required_score": "10.0",
            "subject_tag": "[SPAM]",
            "list": []
        }
    }
}
```

Get hosting mail service detailed information.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mail`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Add a domain to black list.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam/black-list" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","value":"value"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addHostingToBlackList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
null
```

Add a domain to black list.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mail/antispam/black-list`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
value | true | Domain to be blocked | string | - | -
## Add a domain to white list.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam/white-list" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","value":"value"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addHostingToWhiteList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
null
```

Add a domain to white list.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mail/antispam/white-list`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
value | true | Domain to be accepted | string | - | -
## Delete a domain from black list.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam/black-list" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","value":"value"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteHostingFromBlackList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
null
```

Delete a domain from black list.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/mail/antispam/black-list`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
value | true | Domain to be blocked | string | - | -
## Delete a domain from white list.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam/white-list" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","value":"value"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteHostingFromWhiteList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
null
```

Delete a domain from white list.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/mail/antispam/white-list`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
value | true | Domain to be accepted | string | - | -
## Get hosting spamassassin preferences.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSpamassassinPreferences($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting spamassassin preferences.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mail/antispam`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting antispam list.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam/list/:type" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","type":"type"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingAntispamList($server,$domain,$type);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting antispam list.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mail/antispam/list/:type`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
type | true | Antispan list type | enum | ["black","white","all"] | black

## Set hosting spamassassin preferences.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","score":"score","tag":"tag"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingSpamassassinPreferences($server,$domain,$score,$tag);
```

> The above command returns JSON structured like this:

```json
null
```

Set hosting spamassassin preferences.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mail/antispam`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
score | true | Score for antispam preference | string | - | -
tag | true | Tag for antispam preference | string | - | -
## Create new mailbox.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","username":"edu","password":"*******","name":"Edu Salguero","altEmail":"mail@example.com","quota":"0"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMailbox($server,$domain,$username,$password,$name,$altEmail,$quota);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Create new mailbox.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mailbox/:username`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
password | true | Password | string | - | -
name | true | Account owner name | string | - | -
altEmail | true | Alternative email eddress | string | - | -
quota | true | Quota in MB (0 = unlimited) | string | - | -
## Get mailbox info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxInfo($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
null
```

Get mailbox info.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mailbox/:username`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

## Change mailbox password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/pass" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","username":"edu","password":"*******"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxPassword($server,$domain,$username,$password);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Change mailbox password.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mailbox/:username/pass`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
password | true | Password | string | - | -
## Set mailbox quota.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/quota" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username","size":"size"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxQuota($server,$domain,$username,$size);
```

> The above command returns JSON structured like this:

```json
null
```

Set mailbox quota.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mailbox/:username/quota`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
size | true | Quota in MB (0 = unlimited) | string | - | -
## Set mailbox status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username","status":"status"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxStatus($server,$domain,$username,$status);
```

> The above command returns JSON structured like this:

```json
null
```

Set mailbox status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mailbox/:username/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## New mailbox alias.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","username":"edu","goto":"mail@example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMailboxAlias($server,$domain,$username,$goto);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

New mailbox alias.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mailbox/:username/alias`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
goto | true | Target email address | string | - | -
## Get mailbox alias info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxAliasInfo($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
null
```

Get mailbox alias info.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mailbox/:username/alias`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

## Set mailbox alias status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username","status":"status"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxAliasStatus($server,$domain,$username,$status);
```

> The above command returns JSON structured like this:

```json
null
```

Set mailbox alias status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mailbox/:username/alias/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Delete a mailbox alias.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMailboxAlias($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
null
```

Delete a mailbox alias.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/mailbox/:username/alias`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

## Delete a mailbox.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMailbox($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
null
```

Delete a mailbox.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/mailbox/:username`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

## Get mailboxes aliases.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/aliases" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxesAliases($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get mailboxes aliases.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mail/aliases`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting mailboxes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/mailboxes" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailboxes($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting mailboxes.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mail/mailboxes`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting mail service status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailServiceStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting mail service status.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mail/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Set hosting mail service status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingMailServiceStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Set hosting mail service status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mail/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Get hosting MySQL detailed info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMySQLDetailedInfo($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "status": {
            "mysql": "enabled"
        },
        "count": {
            "users": 1,
            "dbs": 1
        },
        "items": {
            "users": {
                "4": {
                    "username": "username",
                    "description": "Usuario para a BD da web de probas de Curtocircuito",
                    "created": "2017-06-21T14:37:24+0000",
                    "modified": "2017-06-21T14:37:24+0000",
                    "type": "mysql"
                }
            },
            "dbs": [
                {
                    "database": "curtocircuito",
                    "databaseDir": "\/home\/example.com\/.db_mysql\/curtocircuito",
                    "accessHost": "%",
                    "description": "Base de datos da web de probas de Curtocircuito",
                    "created": "2017-06-21T14:38:20+0000",
                    "modified": "2017-06-21T14:38:20+0000",
                    "type": "mysql",
                    "user": "curto"
                }
            ]
        }
    }
}
```

Get hosting MySQL detailed info.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/mysql`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Create new MySQL user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/user" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","username":"username","password":"*******","description":"Usuario para a BD da web de probas de Curtocircuito"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMySQLUser($server,$domain,$username,$password,$description);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Create new MySQL user.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mysql/user`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
username | true | User name | string | - | -
password | true | Password | string | - | -
description | true | Description | string | - | -
## Change MySQL user password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/user/:username" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","username":"username","password":"password"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->changeMySQLUserPassword($server,$domain,$username,$password);
```

> The above command returns JSON structured like this:

```json
null
```

Change MySQL user password.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/mysql/user/:username`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
password | true | Password | string | - | -
## Create new MySQL database and assign it to an existing user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/db" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","database":"curtocircuito","username":"username","dbDescription":"Base de datos da web de probas de Curtocircuito"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMySQLDatabaseAndAssignItToAnExistingUser($server,$domain,$database,$username,$dbDescription);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Create new MySQL database and assign it to an existing user.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mysql/db`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
database | true | Database name | string | - | -
username | true | User name | string | - | -
dbDescription | true | Description | string | - | -
## Delete a MySQL database.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/db" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","database":"numax_test"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMySQLDatabase($server,$domain,$database);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Delete a MySQL database.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/mysql/db`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
database | true | Database name | string | - | -
## Delete a MySQL user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/user/:username" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","username":"numax_test"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMySQLUser($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Delete a MySQL user.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/mysql/user/:username`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
username | true | User name | string | - | -

## Create new MySQL database and user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/db-and-user" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","database":"database","dbDescription":"dbDescription","username":"username","password":"password","userDescription":"userDescription"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMySQLDatabaseAndUser($server,$domain,$database,$dbDescription,$username,$password,$userDescription);
```

> The above command returns JSON structured like this:

```json
null
```

Create new MySQL database and user.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/mysql/db-and-user`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
database | true | Database name | string | - | -
dbDescription | true | Description | string | - | -
username | true | User name | string | - | -
password | true | Password | string | - | -
userDescription | true | Description | string | - | -
## Set hosting quota.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/quota" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","size":"size"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingQuota($server,$domain,$size);
```

> The above command returns JSON structured like this:

```json
null
```

Set hosting quota.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/quota`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
size | true | Quota in MB (0 = unlimited) | string | - | -
## Set hosting status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","status":"status"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
null
```

Set hosting status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Get hosting SSH auth mode.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/auth-mode" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSHAuthMode($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting SSH auth mode.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/ssh/auth-mode`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting SSH status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSHStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting SSH status.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/ssh/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Add a SSH public key for a user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/key" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","keyBase64":"c3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFDQVFDNzI4cXpSbXpTdko0VG5hVUgzRktaTVMwYUJXWi9VQ2FpSk40OXhIR0ZqKzQ0bWtRTzZUN1dPVjdvSENtekxKajBPZ2Y0NnJYY2E5bnRyWENSUXNma29FRWI4SVFneVFIendsZnNuT1hxa05uOGd3YnRLdS9kcXRmQlZzK1d1N0ZRc2JONi9ISW5JbWUxdzVJd284L3pkbWc4T3haZC9EaHBqUUdpYXdpTnoxMEhmNXNaRmxRZjMyNDhONjN6b3MxVVF1NFFPNVVHMzhhRy9iRGcyS1ZLSVI2SXdOQUhZTUFIVVBsY2pLTEVHYWFSY2Q3VmswSGl2Vk1pSlB5Sm8vWW8rYjh0OHg1eXlmajkwb1ZUV1FpT243K1JhRnZCSnFhb0o5ZWFSeEI3VHQ3aDJncm5lQXZ0SHp6QnFPbkg2dE5sQ0ZPa2FYUmg2TkxnUHZnRDZYRkswS1dkbVJkSVVZcDNocmJNamdVdEVFYTNLS0ZDbitYVFRkMWwyQzJlclNWTUJqYk5TcHNlOXNaNitHZWoxQjgzb0dRbFFMRllKam9iaXJkMUlTWGdDSER4U2JxeTd2R3dDSWJMRm92cldQdXpQTlNMWmtYSndPeEpWalA1d1Z4ZWVOVzYxaSswN2lmMEw3b0lSME1heDNhZ2ZzS0JjRUdralNkWGpaL2hkL0hxNm14Vlk1WUFVZnRtZlkwNTF6ektsMEcwQnpjVExHTmtXY3VwNVNpcVhLdG5mT29YSStpbGN0YWkzVzlnWS9TS2l6QzlEUHhwR1Q4MmdXcTR3dlZXeXJIaEE1b0h5aGtIcHJ1dkQvYUI5VytyeXlheFhVZUlOZEsvNmQvcTRQUS9TQ0puQWF2NUhCK1VuSUEvYnYrdllDWUJ6RHpLREl2R2tFQmxveTJvQVE9PSBhZHJpYW5AbnVtYXgub3Jn","description":"mail@example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addSSHPublicKey($server,$domain,$keyBase64,$description);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Add a SSH public key for a user.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/ssh/key`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
keyBase64 | true | Public key (base64) | string | - | -
description | true | Description | string | - | -
## Delete a SSH public key.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/key" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","fingerprint":"43:36:fe:b7:55:76:22:41:f2:51:db:d3:4e:7f:08:ef"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSSHPublicKey($server,$domain,$fingerprint);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Delete a SSH public key.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/ssh/key`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
fingerprint | true | SSH key fingerprint | string | - | -
## Set SSH auth mode.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/auth-mode" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","mode":"onlyPublicKey"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setSSHAuthMode($server,$domain,$mode);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Set SSH auth mode.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/ssh/auth-mode`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
mode | true | SSH auth mode | enum | ["onlyPublicKey","password"] | onlyPublicKey
## Set hosting SSH status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingSSHStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Set hosting SSH status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/ssh/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Add and install an SSL certificate.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssl-cert" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","certificateCrtBase64":"certificateCrtBase64","privateKeyBase64":"privateKeyBase64","CABundleBase64":"CABundleBase64","install":"install"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addAndInstallSSLCertificate($server,$domain,$certificateCrtBase64,$privateKeyBase64,$CABundleBase64,$install);
```

> The above command returns JSON structured like this:

```json
null
```

Add and install an SSL certificate.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/ssl-cert`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
certificateCrtBase64 | true | Certificate Crt (base64) | string | - | -
privateKeyBase64 | true | Private Key (base64) | string | - | -
CABundleBase64 | false | CA Bundle (base64, null is valid for self signed certs) | string | - | 
install | true | Install and enable SSL Cert | boolean | [true,false] | 1
## Delete an SSL certificate.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssl-cert" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSSLCertificate($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Delete an SSL certificate.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/ssl-cert`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting SSL certificate information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssl-cert" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSLCertificateInformation($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting SSL certificate information.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/ssl-cert`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get hosting SSL status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssl-cert/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSLStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get hosting SSL status.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/ssl-cert/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Set hosting SSL status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssl-cert/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","status":"status"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingSSLStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
null
```

Set hosting SSL status.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/ssl-cert/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
status | true | Status | enum | ["enable","disable"] | enable
## Change hosting process manager.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/process-manager" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","processManager":"php-7"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->changeHostingProcessManager($server,$domain,$processManager);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Change hosting process manager.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/process-manager`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
processManager | true | Process manager which handles the requests | enum | ["php-5.5","php-5.6","php-7"] | php-5.5
## Delete a hosting.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteHosting($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Delete a hosting.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Request and install Let's encrypt certificate.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/lets-encrypt" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","email":"mail@example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->requestAndInstallLetsEncryptCertificate($server,$domain,$email);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Request and install Let's encrypt certificate.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/lets-encrypt`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
email | true | Email | string | - | -
## Renew the Let's encrypt certificate.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/lets-encrypt" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->renewLetsEncryptCertificate($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21740,
    "message": "Certificate does not need renewal",
    "data": []
}
```

Renew the Let's encrypt certificate.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/lets-encrypt`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get the Let's encrypt certificate status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/lets-encrypt" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getLetsEncryptCertificateStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "issuer": "Let's Encrypt Authority X3",
        "domain": "example.com",
        "fromDate": "2017-08-03 16:18:00",
        "toDate": "2017-11-01 16:18:00"
    }
}
```

Get the Let's encrypt certificate status.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/lets-encrypt`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get installed addons.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/addon" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getInstalledAddons($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "rainloop-1492363472": {
            "id": "rainloop-1492363472",
            "type": "rainloop",
            "addonPath": "\/home\/example.com\/.addons\/rainloop-1492363472",
            "publicPath": "\/home\/example.com\/htdocs\/webmail",
            "options": {
                "url": "example.com\/webmail\/"
            },
            "createdAt": "2017-04-16T17:24:35+0000"
        },
        "owncloud-1492364081": {
            "id": "owncloud-1492364081",
            "type": "owncloud",
            "addonPath": "\/home\/example.com\/.addons\/owncloud-1492364081",
            "publicPath": "\/home\/example.com\/htdocs\/own",
            "options": {
                "adminEmail": "edu@example.com",
                "database": "ownc",
                "dbUsername": "ownc",
                "url": "example.com\/own\/"
            },
            "createdAt": "2017-04-16T17:35:05+0000"
        }
    }
}
```

Get installed addons.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/addon`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get available addons.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/addon/available" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getAvailableAddons($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "owncloud": {
            "name": "owncloud",
            "publicName": "ownCloud",
            "description": "ownCloud is an open source, self-hosted file sync and share app platform. Access & sync your files, contacts, calendars & bookmarks across your devices.",
            "aditionalModules": [
                "mysql"
            ],
            "url": "https:\/\/owncloud.org",
            "license": "GPLv2",
            "settings": [
                "database",
                "dbUsername",
                "dbPassword",
                "adminEmail",
                "adminPassword"
            ]
        },
        "wordpress": {
            "name": "wordpress",
            "publicName": "WordPress",
            "description": "WordPress is open source software you can use to create a beautiful website, blog, or app.",
            "aditionalModules": [
                "mysql"
            ],
            "url": "https:\/\/wordpress.org",
            "license": "AGPLv3",
            "settings": [
                "database",
                "dbUsername",
                "dbPassword",
                "title",
                "adminEmail",
                "adminPassword"
            ]
        },
        "rainloop": {
            "name": "rainloop",
            "publicName": "RainLoop Webmail",
            "description": "RainLoop Webmail - Simple, modern & fast web-based email client.",
            "aditionalModules": [],
            "url": "https:\/\/www.rainloop.net",
            "license": "AGPLv3",
            "settings": []
        },
        "phpmyadmin": {
            "name": "phpmyadmin",
            "publicName": "phpMyAdmin",
            "description": "A tool written in PHP intended to handle the administration of MySQL over the WWW.",
            "url": "https:\/\/www.phpmyadmin.net",
            "license": "GPLv2",
            "aditionalModules": [],
            "settings": []
        }
    }
}
```

Get available addons to install in a hosting.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/addon/available`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Uninstall addon.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/addon/:addonId" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","addonId":"addonId"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->uninstallAddon($server,$domain,$addonId);
```

> The above command returns JSON structured like this:

```json
null
```

Uninstall and remove a hosting addon.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/addon/:addonId`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -
addonId | true | Addon identifier | string | - | -

## Delete git deploy configuration.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/deploy/git" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteGitDeployConfig($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Delete git deploy configuration.

### HTTP Request

`DELETE  /v1/server/:server/hosting/:domain/deploy/git`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Get info about git deploy configuration and last execution.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/deploy/git" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getGitDeployInfo($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get info about git deploy configuration and last execution.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/deploy/git`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

## Configure git deploy.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/deploy/git" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","gitUrl":"gitUrl","gitBranch":"gitBranch","localPath":"localPath","deployScript":"deployScript","deployType":"deployType"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createGitDeployConfig($server,$domain,$gitUrl,$gitBranch,$localPath,$deployScript,$deployType);
```

> The above command returns JSON structured like this:

```json
null
```

Configure git deploy.

### HTTP Request

`PUT  /v1/server/:server/hosting/:domain/deploy/git`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
gitUrl | true | Git URL (SSH not HTTP. Sample: git@github.com:vendor/repo.git) | string | - | -
gitBranch | true | Git branch name | string | - | -
localPath | true | Deploy path | string | - | -
deployScript | true | Script | string | - | -
deployType | true | Deploy type | enum | ["auto","manual"] | auto
## Update git deploy configuration.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/deploy/git" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","gitUrl":"gitUrl","gitBranch":"gitBranch","localPath":"localPath","deployScript":"deployScript","deployType":"deployType"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->updateGitDeployConfig($server,$domain,$gitUrl,$gitBranch,$localPath,$deployScript,$deployType);
```

> The above command returns JSON structured like this:

```json
null
```

Update git deploy configuration.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/deploy/git`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
gitUrl | false | Git URL (SSH not HTTP. Sample: git@github.com:vendor/repo.git) | string | - | -
gitBranch | false | Git branch name | string | - | -
localPath | false | Deploy path | string | - | -
deployScript | false | Script | string | - | -
deployType | false | Deploy type | enum | ["auto","manual"] | auto
## Set web document root path.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/web/document-root" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","path":"www\/current\/public"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setWebDocumentRoot($server,$domain,$path);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "\/home\/example.com\/www\/current\/public"
}
```

Set web document root path.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/web/document-root`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
path | true | Web document root | string | - | -
## Generate a new SSH key and add it to the ssh-agent.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/key-gen" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","domain":"example.com","email":"mail@example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->generateSSHKey($server,$domain,$email);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD2zWbRD1doOgzOosRV1nzunHBrFLlUQZwKS+VnbL2J+Vv4fgzUGKb7dhq5s53Jg4uCVc2OM\/74fZWofsj8AUa6uRl\/ywiQLdzZYfPVhqjmRntcwvFOX\/QepZ3\/J37siUeRIJXiKOp731bXJov+jdWr6K03tvc6NwST+JxE7BgXaPUjnr5XcwCP5Xh9KD+oKoVGMKf+qbB1QeNowwYbHSEFxKxpjhN6QMWOjf1u\/3\/xjQkLjRA85T99Vq8rkPJ2V7QbruOCcywTrtE+ALeC47zLlzUH6dw\/C7uVZcSHUSUgAU0QaDppOzJeLKDSdN0G\/Qakxwm8DffMRgeP9dHhXNaB mail@example.com\n"
}
```

Generate a new SSH key and add it to the ssh-agent.

### HTTP Request

`POST  /v1/server/:server/hosting/:domain/ssh/key-gen`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
email | true | Email | string | - | -
## Get SSH public key content.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/key" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getSSHPublicKey($server,$domain);
```

> The above command returns JSON structured like this:

```json
null
```

Get SSH public key content.

### HTTP Request

`GET  /v1/server/:server/hosting/:domain/ssh/key`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

#Recipes
## Get available recipes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/available-recipes" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getAvailableRecipes($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 50006,
    "message": "Installation in progress",
    "data": []
}
```

Get available recipes.

### HTTP Request

`GET  /v1/server/:server/available-recipes`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get server recipes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/recipes" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerRecipes($server);
```

> The above command returns JSON structured like this:

```json
null
```

Get server recipes.

### HTTP Request

`GET  /v1/server/:server/recipes`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Get recipe installation status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/recipe/:recipe/:token/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","token":"token","recipe":"recipe"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getRecipeInstallationStatus($server,$token,$recipe);
```

> The above command returns JSON structured like this:

```json
null
```

Get recipe installation status.

### HTTP Request

`GET  /v1/server/:server/recipe/:recipe/:token/status`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
token | true | Recipes API token | string | - | -
recipe | true | Recipe's name | string | - | -

## Install recipes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/install" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"mYSeRvEr-Id","recipes":["mail"]}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->installRecipes($server,$recipes);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "af994cbd5d395803c8d58c0c8353a8d2"
}
```

Install recipes.

### HTTP Request

`PUT  /v1/server/:server/install`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
recipes | true | Recipes (json) | string | - | -
