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
-d '{"server":"user-server-01"}'
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
            "uptime": "6245.90",
            "load_avg": {
                "last": 0.18,
                "5min": 0.13,
                "15min": 0.11,
                "nproc": "1"
            },
            "memory_usage": {
                "total": "1017540",
                "used": "713168",
                "free": "304372",
                "shared": "22212",
                "buffers": "24872",
                "cached": "561680",
                "unit": "KB"
            },
            "filesystems_usage": {
                "\/": {
                    "total": "40188",
                    "used": "1735",
                    "free": "36390",
                    "percentage_of_use": "5",
                    "filesystem": "\/dev\/sda1",
                    "type": "ext4",
                    "unit": "MB"
                }
            }
        },
        "network": {
            "eth0": {
                "IPv4": "10.0.2.15",
                "IPv6": "fe80::a00:27ff:fe20:c544"
            }
        },
        "services": {
            "count": 5,
            "items": {
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
            "count": 4,
            "items": [
                {
                    "package": "apache",
                    "version": "2.4.16",
                    "installed": "2016-08-16T16:55:04+0000"
                },
                {
                    "package": "php7-fpm",
                    "version": "7.0",
                    "installed": "2016-08-16T16:55:44+0000"
                },
                {
                    "package": "php5.5-fpm",
                    "version": "5.5",
                    "installed": "2016-08-18T15:15:06+0000"
                },
                {
                    "package": "php5.6-fpm",
                    "version": "5.6",
                    "installed": "2016-08-18T15:15:57+0000"
                }
            ]
        },
        "time": {
            "timezone": "America\/Los_Angeles",
            "date": "2016-08-18T11:37:39-0700"
        },
        "hostings": {
            "count": "4"
        },
        "antispam": {
            "config": [],
            "enable": false
        }
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedIPsInfo($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "eth0": {
            "IPv4": "92.222.70.176",
            "IPv6": "fe80::f816:3eff:fefb:10a"
        }
    }
}
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
-d '{"server":"user-servers-0013"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerDiskUsage($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "\/": {
            "total": "10047",
            "used": "1859",
            "free": "7748",
            "percentage_of_use": "20",
            "filesystem": "\/dev\/vda1",
            "type": "ext4",
            "unit": "MB"
        }
    }
}
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerLoadAverage($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "last": 0,
        "5min": 0.01,
        "15min": 0.05,
        "nproc": "1"
    }
}
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerMemoryUsage($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "total": "4021048",
        "used": "3045632",
        "free": "975416",
        "shared": "17796",
        "buffers": "121440",
        "cached": "2212696",
        "unit": "KB"
    }
}
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
-d '{"server":"user-servers-001"}'
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerUptime($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "1370297.86"
}
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
-d '{"server":"user-servers-001","service":"ftp"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServiceInformation($server,$service);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "isRunning": true,
        "isEnabled": true
    }
}
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
-d '{"server":"user-server-01"}'
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
            "installed": "2016-08-16T16:55:04+0000"
        },
        {
            "package": "php7-fpm",
            "version": "7.0",
            "installed": "2016-08-16T16:55:44+0000"
        },
        {
            "package": "php5.5-fpm",
            "version": "5.5",
            "installed": "2016-08-18T15:15:06+0000"
        },
        {
            "package": "php5.6-fpm",
            "version": "5.6",
            "installed": "2016-08-18T15:15:57+0000"
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMySQLVersion($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "5.5.49-0ubuntu0.14.04.1"
}
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerSpamassassinPreferences($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "required_score": "10",
        "subject_tag": "test-tag"
    }
}
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
-d '{"server":"user-servers-001","tag":"test-tag","score":"10"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setServerSpamassassinPreferences($server,$tag,$score);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001"}'
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
            "server": "apache",
            "processManager": "php-7",
            "created": "2016-06-28T14:02:48+0000",
            "modified": "2016-08-18T10:37:22+0000"
        },
        "example-3.com": {
            "domain": "example-3.com",
            "status": "enable",
            "server": "apache",
            "processManager": "php-7",
            "created": "2016-08-17T22:13:41+0000",
            "modified": "2016-08-18T18:04:34+0000"
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedHostingsInfo($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "test-domain.com": {
            "domain": "example.com",
            "status": "enable",
            "alias": "test alias",
            "ip": "*",
            "documentRoot": "\/home\/example.com\/htdocs",
            "description": null,
            "logDir": "\/home\/test-domain.com\/logs",
            "server": "apache",
            "processManager": "php-5.6",
            "processManagerOptions": [],
            "sslEnable": "disable",
            "mailEnable": "enable",
            "ftpEnabled": "enable",
            "sshEnabled": "enable",
            "sshAuthMode": "onlyPublicKey",
            "quota": {
                "active": false,
                "soft": 0,
                "hard": 0,
                "unit": "KB"
            },
            "created": "2016-04-05T23:22:50+0000",
            "modified": "2016-04-05T23:22:50+0000",
            "systemUser": {
                "username": "examplecom",
                "homeDir": "\/home\/example.com"
            }
        }
    }
}
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
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"user-servers-001","password":"qweasd123"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setRootPassword($server,$password);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
```

Set MySQL root password.

### HTTP Request

`PATCH  /v1/server/:server/mysql/root-password`

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
-d '{"server":"user-servers-001","priority":"1","direction":"INPUT","action":"DROP","protocol":"all","source":"0.0.0","destination":"83.235.64.44","sourcePort":"all","destinationPort":"all","replace":false}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addFirewallRule($server,$priority,$direction,$action,$protocol,$source,$destination,$sourcePort,$destinationPort,$replace);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
direction | true | Direction | enum | ["INPUT","OUTPUT"] | INPUT
action | true | Action | enum | ["ACCEPT","DROP"] | ACCEPT
protocol | true | Protocol | enum | ["tcp","udp","udplite","icmp","icmpv6","esp","ah","sctp","mh","all"] | tcp
source | true | Source IP or Subnet | string | - | -
destination | true | Destination IP or Subnet | string | - | -
sourcePort | true | Source port | string | - | all
destinationPort | true | Destination port | string | - | all
replace | true | Replace | boolean | [true,false] | 1
## Get firewall rules.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/rules" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"user-servers-001"}'
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
-d '{"server":"user-servers-001","priority":"1","direction":"INPUT"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->removeFirewallRule($server,$priority,$direction);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","ip":"83.235.64.44"}'
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
-d '{"server":"user-servers-001","ip":"123.123.123.123"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->firewallRemoveDisallowedIP($server,$ip);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerTimeInformation($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "timezone": "Europe\/Paris",
        "date": "2016-08-02T00:36:56+0200"
    }
}
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
-d '{"server":"fi9CvJ-037","timezone":"UTC"}'
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
-d '{"server":"user-server-01"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getDetailedServerSettings($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "cpu": {
            "model": "Intel(R) Core(TM) i5-5257U CPU @ 2.70GHz",
            "nproc": "1"
        },
        "distro": {
            "id": "Ubuntu",
            "release": "14.04",
            "codename": "trusty",
            "description": "Ubuntu 14.04.3 LTS"
        },
        "kernel_release": "3.16.0-55-generic",
        "timezone": "America\/Los_Angeles",
        "date": "2016-08-18T11:37:46-0700",
        "memory": {
            "total": "1017540",
            "used": "713368",
            "free": "304172",
            "shared": "22212",
            "buffers": "24880",
            "cached": "561704",
            "unit": "KB"
        }
    }
}
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
-d '{"server":"user-servers-001","service":"apache2","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->manageServerServiceStatus($server,$service,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21604,
    "message": "Service \"apache2\" is enabled!",
    "data": []
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
-d '{"server":"user-servers-001","service":"apache2","action":"start"}'
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
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "user-servers-001": {
            "status": "UP",
            "alias": "storage",
            "name": "user-servers-001",
            "ip": "178.62.25.*",
            "location": "London (United Kingdom)",
            "provider": "Digital Ocean",
            "version": "0.99.39"
        },
        "user-servers-002": {
            "status": "DOWN",
            "alias": "vagrant-slave",
            "name": "user-servers-002",
            "ip": "83.*.101.*",
            "location": "Pontevedra (Spain)",
            "provider": "R Cable",
            "version": "0.99.10"
        },
        "user-servers-003": {
            "status": "DOWN",
            "alias": "ovh-ssd",
            "name": "user-servers-001",
            "ip": "92.*.70.*",
            "location": "Santiago de Compostela (Spain)",
            "provider": "R Cable",
            "version": "0.99.13"
        }
    }
}
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
{
    "code": 10000,
    "message": "Success!",
    "data": [
        "user-servers-001",
        "user-servers-002",
        "user-servers-003"
    ]
}
```

Get list of active servers.

### HTTP Request

`GET  /v1/server/list`


## Get git deployments info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/deployments/git" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getGitDeploymentsInfo($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": []
}
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
## Reboot server.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/reboot" \
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"user-servers-001"}'
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
    "data": "47c5a124d2e0158d07d75551f356fe8a"
}
```

Reboot server.

### HTTP Request

`PATCH  /v1/server/:server/reboot`

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
-d '{"server":"user-servers-022"}'
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
    "data": "48be65767cc2cb14d7b274ca16db7ad4"
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
-d '{"title":"Test","code":"# Set path\r\nPATH=\/usr\/local\/sbin:\/usr\/local\/bin:\/usr\/sbin:\/usr\/bin:\/sbin:\/bin\r\n\r\n# Get hostname\r\nhostname=`hostname` 2> \/dev\/null\r\n \r\n# Get distro\r\nif [ -f \"\/etc\/system-release\" ]; then\r\n    distro=`cat \/etc\/system-release`\r\nelse\r\n    distro=`python -c 'import platform; print platform.linux_distribution()[0] + \" \" + platform.linux_distribution()[1]'` 2> \/dev\/null\r\nfi\r\n \r\n# Get uptime\r\nif [ -f \"\/proc\/uptime\" ]; then\r\n    uptime=`cat \/proc\/uptime`\r\n    uptime=${uptime%%.*}\r\n    seconds=$(( uptime%60 ))\r\n    minutes=$(( uptime\/60%60 ))\r\n    hours=$(( uptime\/60\/60%24 ))\r\n    days=$(( uptime\/60\/60\/24 ))\r\n    uptime=\"$days\"d\", $hours\"h\", $minutes\"m\", $seconds\"s\"\"\r\nelse\r\n    uptime=\"\"\r\nfi\r\n \r\n# Get cpus\r\nif [ -f \"\/proc\/cpuinfo\" ]; then\r\n    cpus=`grep -c processor \/proc\/cpuinfo` 2> \/dev\/null\r\nelse\r\n    cpus=\"\"\r\nfi\r\n \r\n# Get load averages\r\nloadavg=`uptime | awk -F'load average:' '{ print $2 }'` 2> \/dev\/null\r\n \r\n# Remove leading whitespace from load averages\r\nloadavg=`echo $loadavg | sed 's\/^ *\/\/g'`\r\n \r\n# Get total memory\r\nif [ -f \"\/proc\/meminfo\" ]; then\r\n    memory=`cat \/proc\/meminfo | grep 'MemTotal:' | awk {'print $2}'` 2> \/dev\/null\r\nelse\r\n    memory=\"\"\r\nfi\r\n \r\n# Get ip addresses using ip\r\nif [ -n `command -v ip` ]; then\r\n    ips=`ip addr show | awk -F \"\/\" '\/inet .*\\\/\/{ gsub(\/inet |^[ \\t]+\/, \"\", $1); if ($1 != \"127.0.0.1\") print $1 }'`\r\n# Try using ifconfig instead\r\nelse\r\n    ips=`ifconfig | awk -F \"[: ]+\" '\/inet addr:\/ { if ($4 != \"127.0.0.1\") print $4 }'` 2> \/dev\/null\r\nfi\r\n \r\n# ips is empty, let's try and get ip addresses with python instead\r\nif [ -z \"${ips}\" ]; then\r\n    ips=`python -c 'import socket; print socket.gethostbyname(socket.gethostname())'` 2> \/dev\/null\r\nfi\r\n \r\necho -n '{\"hostname\": \"'$hostname'\", \"distro\": \"'$distro'\", \"uptime\": \"'$uptime'\", \"cpus\": '$cpus', \"loadavg\": \"'$loadavg'\", \"memory\": '$memory', \"ips\": \"'$ips'\"}'","interpreter":"BASH","visibility":"PRIVATE","notes":""}'
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
    "data": "4f242f07cb316d378e9ce971d3c70561"
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
-d '{"token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSnippetByToken($token);
```

> The above command returns JSON structured like this:

```json
null
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
-d '{"token":"4f242f07cb316d378e9ce971d3c70561"}'
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
        "title": "Test",
        "notes": "",
        "visibility": "PRIVATE",
        "token": "4f242f07cb316d378e9ce971d3c70561",
        "interpreter": "BASH",
        "code": "IyBTZXQgcGF0aA0KUEFUSD0vdXNyL2xvY2FsL3NiaW46L3Vzci9sb2NhbC9iaW46L3Vzci9zYmluOi91c3IvYmluOi9zYmluOi9iaW4NCg0KIyBHZXQgaG9zdG5hbWUNCmhvc3RuYW1lPWBob3N0bmFtZWAgMj4gL2Rldi9udWxsDQogDQojIEdldCBkaXN0cm8NCmlmIFsgLWYgIi9ldGMvc3lzdGVtLXJlbGVhc2UiIF07IHRoZW4NCiAgICBkaXN0cm89YGNhdCAvZXRjL3N5c3RlbS1yZWxlYXNlYA0KZWxzZQ0KICAgIGRpc3Rybz1gcHl0aG9uIC1jICdpbXBvcnQgcGxhdGZvcm07IHByaW50IHBsYXRmb3JtLmxpbnV4X2Rpc3RyaWJ1dGlvbigpWzBdICsgIiAiICsgcGxhdGZvcm0ubGludXhfZGlzdHJpYnV0aW9uKClbMV0nYCAyPiAvZGV2L251bGwNCmZpDQogDQojIEdldCB1cHRpbWUNCmlmIFsgLWYgIi9wcm9jL3VwdGltZSIgXTsgdGhlbg0KICAgIHVwdGltZT1gY2F0IC9wcm9jL3VwdGltZWANCiAgICB1cHRpbWU9JHt1cHRpbWUlJS4qfQ0KICAgIHNlY29uZHM9JCgoIHVwdGltZSU2MCApKQ0KICAgIG1pbnV0ZXM9JCgoIHVwdGltZS82MCU2MCApKQ0KICAgIGhvdXJzPSQoKCB1cHRpbWUvNjAvNjAlMjQgKSkNCiAgICBkYXlzPSQoKCB1cHRpbWUvNjAvNjAvMjQgKSkNCiAgICB1cHRpbWU9IiRkYXlzImQiLCAkaG91cnMiaCIsICRtaW51dGVzIm0iLCAkc2Vjb25kcyJzIiINCmVsc2UNCiAgICB1cHRpbWU9IiINCmZpDQogDQojIEdldCBjcHVzDQppZiBbIC1mICIvcHJvYy9jcHVpbmZvIiBdOyB0aGVuDQogICAgY3B1cz1gZ3JlcCAtYyBwcm9jZXNzb3IgL3Byb2MvY3B1aW5mb2AgMj4gL2Rldi9udWxsDQplbHNlDQogICAgY3B1cz0iIg0KZmkNCiANCiMgR2V0IGxvYWQgYXZlcmFnZXMNCmxvYWRhdmc9YHVwdGltZSB8IGF3ayAtRidsb2FkIGF2ZXJhZ2U6JyAneyBwcmludCAkMiB9J2AgMj4gL2Rldi9udWxsDQogDQojIFJlbW92ZSBsZWFkaW5nIHdoaXRlc3BhY2UgZnJvbSBsb2FkIGF2ZXJhZ2VzDQpsb2FkYXZnPWBlY2hvICRsb2FkYXZnIHwgc2VkICdzL14gKi8vZydgDQogDQojIEdldCB0b3RhbCBtZW1vcnkNCmlmIFsgLWYgIi9wcm9jL21lbWluZm8iIF07IHRoZW4NCiAgICBtZW1vcnk9YGNhdCAvcHJvYy9tZW1pbmZvIHwgZ3JlcCAnTWVtVG90YWw6JyB8IGF3ayB7J3ByaW50ICQyfSdgIDI+IC9kZXYvbnVsbA0KZWxzZQ0KICAgIG1lbW9yeT0iIg0KZmkNCiANCiMgR2V0IGlwIGFkZHJlc3NlcyB1c2luZyBpcA0KaWYgWyAtbiBgY29tbWFuZCAtdiBpcGAgXTsgdGhlbg0KICAgIGlwcz1gaXAgYWRkciBzaG93IHwgYXdrIC1GICIvIiAnL2luZXQgLipcLy97IGdzdWIoL2luZXQgfF5bIFx0XSsvLCAiIiwgJDEpOyBpZiAoJDEgIT0gIjEyNy4wLjAuMSIpIHByaW50ICQxIH0nYA0KIyBUcnkgdXNpbmcgaWZjb25maWcgaW5zdGVhZA0KZWxzZQ0KICAgIGlwcz1gaWZjb25maWcgfCBhd2sgLUYgIls6IF0rIiAnL2luZXQgYWRkcjovIHsgaWYgKCQ0ICE9ICIxMjcuMC4wLjEiKSBwcmludCAkNCB9J2AgMj4gL2Rldi9udWxsDQpmaQ0KIA0KIyBpcHMgaXMgZW1wdHksIGxldCdzIHRyeSBhbmQgZ2V0IGlwIGFkZHJlc3NlcyB3aXRoIHB5dGhvbiBpbnN0ZWFkDQppZiBbIC16ICIke2lwc30iIF07IHRoZW4NCiAgICBpcHM9YHB5dGhvbiAtYyAnaW1wb3J0IHNvY2tldDsgcHJpbnQgc29ja2V0LmdldGhvc3RieW5hbWUoc29ja2V0LmdldGhvc3RuYW1lKCkpJ2AgMj4gL2Rldi9udWxsDQpmaQ0KIA0KZWNobyAtbiAneyJob3N0bmFtZSI6ICInJGhvc3RuYW1lJyIsICJkaXN0cm8iOiAiJyRkaXN0cm8nIiwgInVwdGltZSI6ICInJHVwdGltZSciLCAiY3B1cyI6ICckY3B1cycsICJsb2FkYXZnIjogIickbG9hZGF2ZyciLCAibWVtb3J5IjogJyRtZW1vcnknLCAiaXBzIjogIickaXBzJyJ9Jw==",
        "status": "ACTIVE",
        "createdAt": "2016-07-31T14:17:42+00:00",
        "updatedAt": "2016-08-02T09:31:48+00:00"
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
-d '{"server":"user-servers-001","token":"96bb62b621225623310a94d8f1a7ce68"}'
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
        "slave": "user-servers-001",
        "executionToken": "96bb62b621225623310a94d8f1a7ce68",
        "startDate": "2016-08-16T11:44:30+00:00",
        "endDate": "2016-08-16T11:44:31+00:00",
        "stdout": "eyJob3N0bmFtZSI6ICJkby5lZHVzYWxndWVyby5jb20iLCAiZGlzdHJvIjogIlVidW50dSAxNC4wNCIsICJ1cHRpbWUiOiAiNWQsIDRoLCAyNG0sIDI1cyIsICJjcHVzIjogMSwgImxvYWRhdmciOiAiMC4wNCwgMC4wMywgMC4zMyIsICJtZW1vcnkiOiA1MDE3NDgsICJpcHMiOiAiMTg4LjIyNi4xODkuMzUgMTAuMTQuMC43In0=",
        "stderr": "",
        "terminationCode": 0,
        "status": "COMPLETED",
        "createdAt": "2016-08-16T11:44:30+00:00",
        "updatedAt": "2016-08-16T11:44:31+00:00",
        "snippetToken": "4f242f07cb316d378e9ce971d3c70561",
        "snippetTitle": "Test"
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
    "data": [
        {
            "title": "Get timed",
            "notes": "dddd",
            "visibility": "PRIVATE",
            "token": "f2afce36b66d58bc4d704a3037b503ea",
            "interpreter": "PHP",
            "code": "PD9waHANCmVjaG8gdGltZSgpOw==",
            "status": "ACTIVE",
            "createdAt": "2016-02-23T22:07:54+00:00",
            "updatedAt": "2016-03-31T22:03:52+00:00"
        },
        {
            "title": "Ps",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "5fa21b0711b6d2da4bfd932c7d2ef8db",
            "interpreter": "BASH",
            "code": "cHMgLWF1eA==",
            "status": "ACTIVE",
            "createdAt": "2016-02-27T17:58:03+00:00",
            "updatedAt": "2016-02-27T18:00:25+00:00"
        },
        {
            "title": "dsfsda",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "719d86bb4c92699c08123b8e19ed4c95",
            "interpreter": "BASH",
            "code": "ZGFzZnNkYWZkcw==",
            "status": "ACTIVE",
            "createdAt": "2016-03-17T16:31:42+00:00",
            "updatedAt": "2016-03-17T16:31:42+00:00"
        },
        {
            "title": "Tgg",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "b12400e647a50173f11c95ef89cc2b51",
            "interpreter": "BASH",
            "code": "R2dn",
            "status": "ACTIVE",
            "createdAt": "2016-03-30T09:36:22+00:00",
            "updatedAt": "2016-03-30T09:36:22+00:00"
        },
        {
            "title": "asdfsdfsd",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "1215a4a56dfd60aa3a888489702d4622",
            "interpreter": "BASH",
            "code": "bHM=",
            "status": "ACTIVE",
            "createdAt": "2016-03-31T22:04:06+00:00",
            "updatedAt": "2016-03-31T22:04:06+00:00"
        },
        {
            "title": "top",
            "notes": "Un top",
            "visibility": "PRIVATE",
            "token": "aa10ce25ac904fddd91c1d9732b310c2",
            "interpreter": "BASH",
            "code": "dG9wIC1iIC1uIDE=",
            "status": "ACTIVE",
            "createdAt": "2016-06-30T17:17:56+00:00",
            "updatedAt": "2016-07-13T14:45:04+00:00"
        },
        {
            "title": "Disk usage",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "50f0d59a9567f59634d804802626f0aa",
            "interpreter": "BASH",
            "code": "ZHUgLWggLw==",
            "status": "ACTIVE",
            "createdAt": "2016-07-30T15:31:46+00:00",
            "updatedAt": "2016-07-30T15:32:57+00:00"
        },
        {
            "title": "Git pull",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "3fd930d9a08fde8af2b9eb7a88d1b551",
            "interpreter": "BASH",
            "code": "Y2QgL2hvbWUvbGFyYXZlbC5kby5lZHVzYWxndWVyby5jb20vYmxvZyANCnBocCBhcnRpc2Fu",
            "status": "ACTIVE",
            "createdAt": "2016-07-30T15:41:05+00:00",
            "updatedAt": "2016-07-31T13:18:47+00:00"
        },
        {
            "title": "Test",
            "notes": "",
            "visibility": "PRIVATE",
            "token": "4f242f07cb316d378e9ce971d3c70561",
            "interpreter": "BASH",
            "code": "IyBTZXQgcGF0aA0KUEFUSD0vdXNyL2xvY2FsL3NiaW46L3Vzci9sb2NhbC9iaW46L3Vzci9zYmluOi91c3IvYmluOi9zYmluOi9iaW4NCg0KIyBHZXQgaG9zdG5hbWUNCmhvc3RuYW1lPWBob3N0bmFtZWAgMj4gL2Rldi9udWxsDQogDQojIEdldCBkaXN0cm8NCmlmIFsgLWYgIi9ldGMvc3lzdGVtLXJlbGVhc2UiIF07IHRoZW4NCiAgICBkaXN0cm89YGNhdCAvZXRjL3N5c3RlbS1yZWxlYXNlYA0KZWxzZQ0KICAgIGRpc3Rybz1gcHl0aG9uIC1jICdpbXBvcnQgcGxhdGZvcm07IHByaW50IHBsYXRmb3JtLmxpbnV4X2Rpc3RyaWJ1dGlvbigpWzBdICsgIiAiICsgcGxhdGZvcm0ubGludXhfZGlzdHJpYnV0aW9uKClbMV0nYCAyPiAvZGV2L251bGwNCmZpDQogDQojIEdldCB1cHRpbWUNCmlmIFsgLWYgIi9wcm9jL3VwdGltZSIgXTsgdGhlbg0KICAgIHVwdGltZT1gY2F0IC9wcm9jL3VwdGltZWANCiAgICB1cHRpbWU9JHt1cHRpbWUlJS4qfQ0KICAgIHNlY29uZHM9JCgoIHVwdGltZSU2MCApKQ0KICAgIG1pbnV0ZXM9JCgoIHVwdGltZS82MCU2MCApKQ0KICAgIGhvdXJzPSQoKCB1cHRpbWUvNjAvNjAlMjQgKSkNCiAgICBkYXlzPSQoKCB1cHRpbWUvNjAvNjAvMjQgKSkNCiAgICB1cHRpbWU9IiRkYXlzImQiLCAkaG91cnMiaCIsICRtaW51dGVzIm0iLCAkc2Vjb25kcyJzIiINCmVsc2UNCiAgICB1cHRpbWU9IiINCmZpDQogDQojIEdldCBjcHVzDQppZiBbIC1mICIvcHJvYy9jcHVpbmZvIiBdOyB0aGVuDQogICAgY3B1cz1gZ3JlcCAtYyBwcm9jZXNzb3IgL3Byb2MvY3B1aW5mb2AgMj4gL2Rldi9udWxsDQplbHNlDQogICAgY3B1cz0iIg0KZmkNCiANCiMgR2V0IGxvYWQgYXZlcmFnZXMNCmxvYWRhdmc9YHVwdGltZSB8IGF3ayAtRidsb2FkIGF2ZXJhZ2U6JyAneyBwcmludCAkMiB9J2AgMj4gL2Rldi9udWxsDQogDQojIFJlbW92ZSBsZWFkaW5nIHdoaXRlc3BhY2UgZnJvbSBsb2FkIGF2ZXJhZ2VzDQpsb2FkYXZnPWBlY2hvICRsb2FkYXZnIHwgc2VkICdzL14gKi8vZydgDQogDQojIEdldCB0b3RhbCBtZW1vcnkNCmlmIFsgLWYgIi9wcm9jL21lbWluZm8iIF07IHRoZW4NCiAgICBtZW1vcnk9YGNhdCAvcHJvYy9tZW1pbmZvIHwgZ3JlcCAnTWVtVG90YWw6JyB8IGF3ayB7J3ByaW50ICQyfSdgIDI+IC9kZXYvbnVsbA0KZWxzZQ0KICAgIG1lbW9yeT0iIg0KZmkNCiANCiMgR2V0IGlwIGFkZHJlc3NlcyB1c2luZyBpcA0KaWYgWyAtbiBgY29tbWFuZCAtdiBpcGAgXTsgdGhlbg0KICAgIGlwcz1gaXAgYWRkciBzaG93IHwgYXdrIC1GICIvIiAnL2luZXQgLipcLy97IGdzdWIoL2luZXQgfF5bIFx0XSsvLCAiIiwgJDEpOyBpZiAoJDEgIT0gIjEyNy4wLjAuMSIpIHByaW50ICQxIH0nYA0KIyBUcnkgdXNpbmcgaWZjb25maWcgaW5zdGVhZA0KZWxzZQ0KICAgIGlwcz1gaWZjb25maWcgfCBhd2sgLUYgIls6IF0rIiAnL2luZXQgYWRkcjovIHsgaWYgKCQ0ICE9ICIxMjcuMC4wLjEiKSBwcmludCAkNCB9J2AgMj4gL2Rldi9udWxsDQpmaQ0KIA0KIyBpcHMgaXMgZW1wdHksIGxldCdzIHRyeSBhbmQgZ2V0IGlwIGFkZHJlc3NlcyB3aXRoIHB5dGhvbiBpbnN0ZWFkDQppZiBbIC16ICIke2lwc30iIF07IHRoZW4NCiAgICBpcHM9YHB5dGhvbiAtYyAnaW1wb3J0IHNvY2tldDsgcHJpbnQgc29ja2V0LmdldGhvc3RieW5hbWUoc29ja2V0LmdldGhvc3RuYW1lKCkpJ2AgMj4gL2Rldi9udWxsDQpmaQ0KIA0KZWNobyAtbiAneyJob3N0bmFtZSI6ICInJGhvc3RuYW1lJyIsICJkaXN0cm8iOiAiJyRkaXN0cm8nIiwgInVwdGltZSI6ICInJHVwdGltZSciLCAiY3B1cyI6ICckY3B1cycsICJsb2FkYXZnIjogIickbG9hZGF2ZyciLCAibWVtb3J5IjogJyRtZW1vcnknLCAiaXBzIjogIickaXBzJyJ9Jw==",
            "status": "ACTIVE",
            "createdAt": "2016-07-31T14:17:42+00:00",
            "updatedAt": "2016-08-02T09:31:48+00:00"
        }
    ]
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
    "data": {
        "f2afce36b66d58bc4d704a3037b503ea": {
            "snippet": {
                "title": "Get timed",
                "notes": "dddd",
                "visibility": "PRIVATE",
                "token": "f2afce36b66d58bc4d704a3037b503ea",
                "interpreter": "PHP",
                "code": "PD9waHANCmVjaG8gdGltZSgpOw==",
                "status": "ACTIVE",
                "createdAt": "2016-02-23T22:07:54+00:00",
                "updatedAt": "2016-03-31T22:03:52+00:00"
            }
        },
        "4f242f07cb316d378e9ce971d3c70561": {
            "snippet": {
                "title": "Test",
                "notes": "",
                "visibility": "PRIVATE",
                "token": "4f242f07cb316d378e9ce971d3c70561",
                "interpreter": "BASH",
                "code": "aG9zdG5hbWUNCnBzIC1hdXh4",
                "status": "ACTIVE",
                "createdAt": "2016-07-31T14:17:42+00:00",
                "updatedAt": "2016-07-31T21:44:38+00:00"
            },
            "executions": {
                "b39c91dc6df2cb6f6b218e45a7a3c26b": {
                    "slave": "user-servers-001",
                    "executionToken": "b39c91dc6df2cb6f6b218e45a7a3c26b",
                    "startDate": "2016-07-31T14:18:15+00:00",
                    "endDate": "2016-07-31T14:18:15+00:00",
                    "stdout": "",
                    "stderr": "L3Zhci90bXAvMTQ2OTk3NDY5NS00ZjI0MmYwN2NiMzE2ZDM3OGU5Y2U5NzFkM2M3MDU2MTogbGluZSA0OiAkJ1xyJzogY29tbWFuZCBub3QgZm91bmQKL3Zhci90bXAvMTQ2OTk3NDY5NS00ZjI0MmYwN2NiMzE2ZDM3OGU5Y2U5NzFkM2M3MDU2MTogbGluZSA2OiBob3N0bmFtZTogY29tbWFuZCBub3QgZm91bmQKL3Zhci90bXAvMTQ2OTk3NDY5NS00ZjI0MmYwN2NiMzE2ZDM3OGU5Y2U5NzFkM2M3MDU2MTogbGluZSA3OiAkJ1xyJzogY29tbWFuZCBub3QgZm91bmQKL3Zhci90bXAvMTQ2OTk3NDY5NS00ZjI0MmYwN2NiMzE2ZDM3OGU5Y2U5NzFkM2M3MDU2MTogbGluZSA2Mjogc3ludGF4IGVycm9yOiB1bmV4cGVjdGVkIGVuZCBvZiBmaWxlCg==",
                    "terminationCode": 2,
                    "status": "COMPLETED",
                    "createdAt": "2016-07-31T14:18:15+00:00",
                    "updatedAt": "2016-07-31T14:18:15+00:00"
                }
            }
        }
    }
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
-d '{"server":"server","token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->markSnippetExecutionAsViewed($server,$token);
```

> The above command returns JSON structured like this:

```json
null
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
-d '{"token":"4f242f07cb316d378e9ce971d3c70561","title":"Test","code":"# Set path\r\nPATH=\/usr\/local\/sbin:\/usr\/local\/bin:\/usr\/sbin:\/usr\/bin:\/sbin:\/bin\r\n\r\n# Get hostname\r\nhostname=`hostname` 2> \/dev\/null\r\n \r\n# Get distro\r\nif [ -f \"\/etc\/system-release\" ]; then\r\n    distro=`cat \/etc\/system-release`\r\nelse\r\n    distro=`python -c 'import platform; print platform.linux_distribution()[0] + \" \" + platform.linux_distribution()[1]'` 2> \/dev\/null\r\nfi\r\n \r\n# Get uptime\r\nif [ -f \"\/proc\/uptime\" ]; then\r\n    uptime=`cat \/proc\/uptime`\r\n    uptime=${uptime%%.*}\r\n    seconds=$(( uptime%60 ))\r\n    minutes=$(( uptime\/60%60 ))\r\n    hours=$(( uptime\/60\/60%24 ))\r\n    days=$(( uptime\/60\/60\/24 ))\r\n    uptime=\"$days\"d\", $hours\"h\", $minutes\"m\", $seconds\"s\"\"\r\nelse\r\n    uptime=\"\"\r\nfi\r\n \r\n# Get cpus\r\nif [ -f \"\/proc\/cpuinfo\" ]; then\r\n    cpus=`grep -c processor \/proc\/cpuinfo` 2> \/dev\/null\r\nelse\r\n    cpus=\"\"\r\nfi\r\n \r\n# Get load averages\r\nloadavg=`uptime | awk -F'load average:' '{ print $2 }'` 2> \/dev\/null\r\n \r\n# Remove leading whitespace from load averages\r\nloadavg=`echo $loadavg | sed 's\/^ *\/\/g'`\r\n \r\n# Get total memory\r\nif [ -f \"\/proc\/meminfo\" ]; then\r\n    memory=`cat \/proc\/meminfo | grep 'MemTotal:' | awk {'print $2}'` 2> \/dev\/null\r\nelse\r\n    memory=\"\"\r\nfi\r\n \r\n# Get ip addresses using ip\r\nif [ -n `command -v ip` ]; then\r\n    ips=`ip addr show | awk -F \"\/\" '\/inet .*\\\/\/{ gsub(\/inet |^[ \\t]+\/, \"\", $1); if ($1 != \"127.0.0.1\") print $1 }'`\r\n# Try using ifconfig instead\r\nelse\r\n    ips=`ifconfig | awk -F \"[: ]+\" '\/inet addr:\/ { if ($4 != \"127.0.0.1\") print $4 }'` 2> \/dev\/null\r\nfi\r\n \r\n# ips is empty, let's try and get ip addresses with python instead\r\nif [ -z \"${ips}\" ]; then\r\n    ips=`python -c 'import socket; print socket.gethostbyname(socket.gethostname())'` 2> \/dev\/null\r\nfi\r\n \r\necho -n '{\"hostname\": \"'$hostname'\", \"distro\": \"'$distro'\", \"uptime\": \"'$uptime'\", \"cpus\": '$cpus', \"loadavg\": \"'$loadavg'\", \"memory\": '$memory', \"ips\": \"'$ips'\"}'","interpreter":"BASH","visibility":"PRIVATE","notes":""}'
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
-d '{"server":"user-servers-001","token":"4f242f07cb316d378e9ce971d3c70561"}'
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
    "data": "96bb62b621225623310a94d8f1a7ce68"
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
-d '{"server":"user-server-01","domain":"example.com","alias":"www.example.com","mailEnable":false,"processManager":"php-5.5","password":"123qwe","webRoot":"htdocs"}'
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
-d '{"server":"user-servers-001","domain":"example.com","password":"123456"}'
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingTotalDiskUsage($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "size": "40",
        "unit": "KB",
        "path": "\/home\/example.com"
    }
}
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
-d '{"server":"user-servers-001","domain":"example.com","deep":"1"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingDiskUsageSummary($server,$domain,$deep);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": [
        {
            "size": "364",
            "unit": "KB",
            "path": "\/home\/example.com\/Maildir"
        },
        {
            "size": "16",
            "unit": "KB",
            "path": "\/home\/example.com\/.local"
        },
        {
            "size": "12",
            "unit": "KB",
            "path": "\/home\/example.com\/.db_mysql"
        },
        {
            "size": "20",
            "unit": "KB",
            "path": "\/home\/example.com\/.ssl"
        },
        {
            "size": "3176",
            "unit": "KB",
            "path": "\/home\/example.com\/.config"
        },
        {
            "size": "22536",
            "unit": "KB",
            "path": "\/home\/example.com\/.cache"
        },
        {
            "size": "17160",
            "unit": "KB",
            "path": "\/home\/example.com\/logs"
        },
        {
            "size": "12",
            "unit": "KB",
            "path": "\/home\/example.com\/.ssh"
        },
        {
            "size": "118016",
            "unit": "KB",
            "path": "\/home\/example.com\/blog"
        },
        {
            "size": "163936",
            "unit": "KB",
            "path": "\/home\/example.com"
        }
    ]
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
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
        "alias": "",
        "ip": "*",
        "documentRoot": "\/home\/example.com\/htdocs",
        "description": null,
        "logDir": "\/home\/example.com\/logs",
        "server": "apache",
        "processManager": "php-7",
        "processManagerOptions": [],
        "sslEnable": "enable",
        "mailEnable": "enable",
        "ftpEnabled": "enable",
        "sshEnabled": "enable",
        "sshAuthMode": "onlyPublicKey",
        "quota": {
            "active": true,
            "soft": 0,
            "hard": 0,
            "unit": "KB"
        },
        "created": "2016-06-28T14:02:48+0000",
        "modified": "2016-08-18T10:37:22+0000",
        "systemUser": {
            "username": "examplecom",
            "homeDir": "\/home\/example.com",
            "sshPubKey": ""
        },
        "mail": {
            "status": "enable",
            "alias": {
                "max": 0,
                "count": 1
            },
            "mailbox": {
                "max": 0,
                "count": 1
            },
            "mailDir": "\/home\/example.com\/Maildir",
            "created": "2016-07-23T14:14:27+0000",
            "modified": "2016-08-18T22:10:03+0000",
            "antispam": {
                "status": "enabled",
                "required_score": "7",
                "subject_tag": "Spamito"
            }
        },
        "db": {
            "status": {
                "mysql": "enabled"
            },
            "count": {
                "users": 1,
                "dbs": 1
            }
        },
        "sshKeys": [
            {
                "key": "dfasd",
                "description": "sadfas",
                "fingerprint": "d4:1d:8c:d9:8f:00:b2:04:e9:80:09:98:ec:f8:42:7e",
                "fileLocation": "\/home\/example.com\/.ssh\/authorized_keys",
                "created": "2016-08-11T08:57:17+0000",
                "modified": "2016-08-11T08:57:17+0000"
            },
            {
                "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDn90rfi0wKzwKYLIVtjimd7kofo6UcFhDazNYqxfEwqm4mHrchHCvwOoY6BmX2rKjmzIuoejV7YJ\/VzV00T8zudYog7udNbQTrNp8fNoFsDqTi1gP********j7ubFqMpOnL5k6jaw\/w72xwpDU8PzIrHM43WzqcfYJhT1vSqQmcWqsz3K75cVPhsL1vkk68xkdtorQ0CapEXwHFJSVUL0\/Jxd4A34AP67dGDrxCoqW0\/rX8bB52KvPRjqphDQu1GY7OWiv3SCWkvZdx9rROoFJWuFejgnFDXHwFmAmWztDfmzBvJHSF9ML24Z0vdvUHxnJTzfrdN+1QWjVJs\/i89iIr edu@example.com\r\n",
                "description": "Test",
                "fingerprint": "51:97:8c:80:85:8c:fc:96:ae:1c:8c:b6:03:c5:cc:5f",
                "fileLocation": "\/home\/example.com\/.ssh\/authorized_keys",
                "created": "2016-08-17T07:56:41+0000",
                "modified": "2016-08-17T07:56:41+0000"
            }
        ],
        "sslInfo": {
            "CABundle": "-----BEGIN CERTIFICATE-----\r\nMIIEkjCCA3qgAwIBAgIQCgFBQgAAAVOFc2oLheynCDANBgkqhkiG9w0BAQsFADA\/\r\nMSQwIgYDVQQKExtEaWdpdGFsIFNpZ25hdHVyZSBUcnVzdCBDby4xFzAVBgNVBAMT\r\nDkRTVCBSb290IENBIFgzMB4XDTE2MDMxNzE2NDA0NloXDTIxMDMxNzE2NDA0Nlow\r\nSjELMAkGA1UEBhMCVVMxFjAUBgNVBAoTDUxldCdzIEVuY3J5cHQxIzAhBgNVBAMT\r\nGkxldCdzIEVuY3J5cHQgQXV0aG9yaXR5IFgzMIIBIjANBgkqhkiG9w0BAQEFAAOC\r\nAQ8AMIIBCgKCAQEAnNMM8FrlLke3cl03g7NoYzDq1zUmGSXhvb418XCSL7e4S0EF\r\nq6meNQhY7LEqxGiHC6PjdeTm86dicbp5gWAf15Gan\/PQeGdxyGkOlZHP\/uaZ6WA8\r\nSMx+yk13EiSdRxta67nsHjcAHJyse6cF6s5K671B5TaYucv9bTyWaN8jKkKQDIZ0\r\nZ8h\/pZq4UmEUEz9l6YKHy9v6Dlb2honzhT+Xhq+w3Brvaw2VFn3EK6BlspkENnWA\r\na6xK8xuQSXgvopZPKiAlKQTGdMDQMc2PMTiVFrqoM7hD8bEfwzB\/onkxEz0tNvjj\r\n\/PIzark5McWvxI0NHWQWM6r6hCm21AvA2H3DkwIDAQABo4IBfTCCAXkwEgYDVR0T\r\nAQH\/BAgwBgEB\/wIBADAOBgNVHQ8BAf8EBAMCAYYwfwYIKwYBBQUHAQEEczBxMDIG\r\nCCsGAQUFBzABhiZodHRwOi8vaXNyZy50cnVzdGlkLm9jc3AuaWRlbnRydXN0LmNv\r\nbTA7BggrBgEFBQcwAoYvaHR0cDovL2F**********RydXN0LmNvbS9yb290cy9k\r\nc3Ryb290Y2F4My5wN2MwHwYDVR0jBBgwFoAUxKexpHsscfrb4UuQdf\/EFWCFiRAw\r\nVAYDVR0gBE0wSzAIBgZngQwBAgEwPwYLKwYBBAGC3xMBAQEwMDAuBggrBgEFBQcC\r\nARYiaHR0cDovL2Nwcy5yb290LXgxLmxldHNlbmNyeXB0Lm9yZzA8BgNVHR8ENTAz\r\nMDGgL6AthitodHRwOi8vY3JsLmlkZW50cnVzdC5jb20vRFNUUk9PVENBWDNDUkwu\r\nY3JsMB0GA1UdDgQWBBSoSmpjBH3duubRObemRWXv86jsoTANBgkqhkiG9w0BAQsF\r\nAAOCAQEA3TPXEfNjWDjdGBX7CVW+dla5cEilaUcne8IkCJLxWh9KEik3JHRRHGJo\r\nuM2VcGfl96S8TihRzZvoroed6ti6WqEBmtzw3Wodatg+VyOeph4EYpr\/1wXKtx8\/\r\nwApIvJSwtmVi4MFU5aMqrSDE6ea73Mj2tcMyo5jMd6jmeWUHK8so\/joWUoHOUgwu\r\nX4Po1QYz+3dszkDqMp4fklxBwXRsW10KXzPMTZ+sOPAveyxindmjkW8lGy+QsRlG\r\nPfZ+G6Z6h7mjem0Y+iWlkYcV4PIWL1iwBi8saCbGS5jN2p8M+X+Q7UNKEkROb3N6\r\nKOqkqm57TH2H3eDJAkSnh6\/DNFu0Qg==\r\n-----END CERTIFICATE-----",
            "CertificateCrt": "-----BEGIN CERTIFICATE-----\r\nMIIFGDCCBACgAwIBAgISA4gLsN+sYPjZQQ35MbA6f7kAMA0GCSqGSIb3DQEBCwUA\r\nMEoxCzAJBgNVBAYTAlVTMRYwFAYDVQQKEw1MZXQncyBFbmNyeXB0MSMwIQYDVQQD\r\nExpMZXQncyBFbmNyeXB0IEF1dGhvcml0eSBYMzAeFw0xNjA4MTAxMjI0MDBaFw0x\r\nNjExMDgxMjI0MDBaMCUxIzAhBgNVBAMTGmxhcmF2ZWwuZG8uZWR1c2FsZ3Vlcm8u\r\nY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw9CFgvAC\/s6K62Ue\r\nvhAi3OPkQESqWUTl3SMYxHrwDCAqdEmw+hMRmVPhJ1KpcprE8i0EEb+xTRLPBQX4\r\ndzCgPNHs5XrKalQOaEhsumPpwr\/Jvkque11AHEuCgLoOjs15FEzwNgSVoIlan3Bi\r\n0vgD4gFDcDfc7mpslPFoE7SseHRYsB1\/Xlw0T52yB5dlIRR4MhKte9LXO5Fz4Hch\r\nK2hQB+ypVnFsVXZXqzduS\/5Er08UB0PExJVHgR+34Ok3IPRy5zAk2+J0zoM5k4tS\r\nZyeGNl+d8tiiSyVYMIZ5J5Wc2F3xYk2GRwlIT1Kveu1npkSf4ZT8uAcCOt8g7Lvu\r\nf8aVUwIDAQABo4ICGzCCAhcwDgYDVR0PAQH\/BAQDAgWgMB0GA1UdJQQWMBQGCCsG\r\nAQUFBwMBBggrBgEFBQcDAjAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBSef3XSbfSy\r\nraiJeZrtsMfc92D4+TAfBgNVHSMEGDAWgBSoSmpjBH3duubRObemRWXv86jsoTBw\r\nBggrBgEFBQcBAQRkMGIwLwYIKwYBBQUHMAGGI2h0dHA6Ly9vY3NwLmludC14My5s\r\nZXRzZW5jcnlwdC5vcmcvMC8GCCsGAQUFBzAChiNodHRwOi8vY2VydC5pbnQteDMu\r\nbGV0c2VuY3J5cHQub3JnLzAlBgNVHREEHjAcghps***********LmVkdXNhbGd1\r\nZXJvLmNvbTCB\/gYDVR0gBIH2MIHzMAgGBmeBDAECATCB5gYLKwYBBAGC3xMBAQEw\r\ngdYwJgYIKwYBBQUHAgEWGmh0dHA6Ly9jcHMubGV0c2VuY3J5cHQub3JnMIGrBggr\r\nBgEFBQcCAjCBngyBm1RoaXMgQ2VydGlmaWNhdGUgbWF5IG9ubHkgYmUgcmVsaWVk\r\nIHVwb24gYnkgUmVseWluZyBQYXJ0aWVzIGFuZCBvbmx5IGluIGFjY29yZGFuY2Ug\r\nd2l0aCB0aGUgQ2VydGlmaWNhdGUgUG9saWN5IGZvdW5kIGF0IGh0dHBzOi8vbGV0\r\nc2VuY3J5cHQub3JnL3JlcG9zaXRvcnkvMA0GCSqGSIb3DQEBCwUAA4IBAQBYBZrb\r\nMssiqi700EaLKESalUSVn9F4wVjkII6OoVweY1ykqk7Km5Sl3AaVQh0vJhJ2nEBH\r\n\/\/2ZVhIVQfVZK1kRI6cKlYrXWSxg4fdR+QO3Uq7y9bIYTbAOsmSMsEtT62yun5gP\r\niJ3swN6Lf+3bc+llnk8MjJ54pq3opwvCeaYO1Ub7AyR1xltMLx0KLF29G0HJbsHw\r\ndJ6wQvTnYzZXQsBgIp6qNx6j9624kbnd\/uulDtxWhvE7zkOC0T1RFsKBxICj3AiF\r\nkaq7nWNqQknTZHYT3TcFgP2YQi9j0txA1b9j64ql62vpLg2xOE6owZUADAXnBN3h\r\nGrBN84Y7ombVrOQ0\r\n-----END CERTIFICATE-----",
            "PrivateKey": "-----BEGIN PRIVATE KEY-----\r\nMIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQDD0IWC8AL+zorr\r\nZR6+ECLc4+RARKpZROXdIxjEevAMICp0SbD6ExGZU+EnUqlymsTyLQQRv7FNEs8F\r\nBfh3MKA80ezlespqVA5oSGy6Y+nCv8m+Sq57XUAcS4KAug6OzXkUTPA2BJWgiVqf\r\ncGLS+APiAUNwN9zuamyU8WgTtKx4dFiwHX9eXDRPnbIHl2UhFHgyEq170tc7kXPg\r\ndyEraFAH7KlWcWxVdlerN25L\/kSvTxQHQ8TElUeBH7fg6Tcg9HLnMCTb4nTOgzmT\r\ni1JnJ4Y2X53y2KJLJVgwhnknlZzYXfFiTYZHCUhPUq967WemRJ\/hlPy4BwI63yDs\r\nu+5\/xpVTAgMBAAECggEAdlSomfvYk4rVQHMXJNwzdTDyWjQkjVWpYv02lmWEco9t\r\nmGB\/5l9nnzSlN1Iou+zzXzX844zn5B+dovd8supbquVhNzwA3kh1fGdn7Ss7tEiZ\r\n7bjLwBkWCQNIlenZqkpZBP+JmdsjYKQgc4FC9yKRlh4VVtcrV5hQjaFkt6PTJeZ6\r\npTp4I7i\/290kxg2h77tQoC0Pm01Fn4FDNw8w7DitJDkQvD1LE\/7hArPS\/Qp7oGQN\r\nfn\/9Vsty6TTUYezTWtDN\/\/alIF4S2\/EDcQaHpiNBtp1s576rfnfRam12hI8vQZIw\r\nIx5bB8t3Llx+2Q5CU0o4RkBQZe9c7dELoDu1xoqdwQKBgQDhw1bEXkdQwyl0Jm++\r\ncU**********\/chyUjJVJiyfv8yymGIA2Clk4ASVlhus\/hR7iJ4dgolxj8PMZ\r\ncP065WZt7O4GVg5kl45jTkYi5S\/l+dvJwsBXbN\/bBCqQD\/4cLz54uABMTlxUOgA2\r\nrWsVYhr0iKn3qaCuZc8ViPP8OQKBgQDeClkrfEm3H8ZhzHRdqRhFpTrsNOrR+d8K\r\nXib+GyfFvPr9Wsz2UmjFLt0W3yxh11Vj6jsLeUpXkna00+ZchQszPpjW+bCxoZ6y\r\nYDgJT5KoUIuqZAIgGEL6Lq0MvLUNCVCyLphwDlwQ9g2eeBiU5Ti4O+\/kaWLDRlou\r\nd0LBAch16wKBgBTIV6dyClyb6qf\/lc\/RPGcqROl2odLzyjcyuQDPxDpl7gI\/v392\r\nx+6xmy71pAypk+RgC8zD2MmDiL\/GgYp5BUazsW8zHWJF78NA1GG95eT2didUjfAP\r\n1ob1xdGym3xxjHHpw3V3cseTexph0H04D6CDTHnwTr02x0zmoF6aIeO5AoGATcg2\r\nQIODl0DsT+o9gWnw9MTTBVfsQq5TseAVrMJ6hkyTaBlc35Uy2pB2JsL7WzMB2MR+\r\n9qAAqPjH2MS6WALLT6JIDFbfzPofC8GlH63eZFQC+Sebjv6wx89+E44vpmdy+1hT\r\nUj3VhqOLVc4gXliGLBPjD5LTZDDK+qgQnGgxfw0CgYAQDHqkhlrTwkgDv6a1vgPF\r\nW\/dfcWHAOL52Hm9FTl8+\/Uy\/9KWG0tG8p1baRu4llPoKborvw7mHZWUwYkjkLBHU\r\nUI\/j7bSV579Csgm62ckywGGwSk0qRLuLAwJjMk3btVkQ\/h+i6BXFPwKzjEJVOa1m\r\nQINe24jGInKuNTPaqywDjw==\r\n-----END PRIVATE KEY-----",
            "created": "2016-08-15T15:50:12+0000",
            "modified": "2016-08-15T15:50:12+0000",
            "validTo": "2016-11-08T12:24:00+0000",
            "certInfo": {
                "name": "\/CN=example.com",
                "subject": {
                    "CN": "example.com"
                },
                "hash": "14449f84",
                "issuer": {
                    "C": "US",
                    "O": "Let's Encrypt",
                    "CN": "Let's Encrypt Authority X3"
                },
                "version": 2,
                "serialNumber": "307630799585363704142430864562423783733504",
                "validFrom": "160810122400Z",
                "validTo": "161108122400Z",
                "validFrom_time_t": 1470831840,
                "validTo_time_t": 1478607840,
                "signatureTypeSN": "RSA-SHA256",
                "signatureTypeLN": "sha256WithRSAEncryption",
                "signatureTypeNID": 668,
                "purposes": {
                    "1": [
                        true,
                        false,
                        "sslclient"
                    ],
                    "2": [
                        true,
                        false,
                        "sslserver"
                    ],
                    "3": [
                        true,
                        false,
                        "nssslserver"
                    ],
                    "4": [
                        false,
                        false,
                        "smimesign"
                    ],
                    "5": [
                        false,
                        false,
                        "smimeencrypt"
                    ],
                    "6": [
                        false,
                        false,
                        "crlsign"
                    ],
                    "7": [
                        true,
                        true,
                        "any"
                    ],
                    "8": [
                        true,
                        false,
                        "ocsphelper"
                    ],
                    "9": [
                        false,
                        false,
                        "timestampsign"
                    ]
                },
                "extensions": {
                    "keyUsage": "Digital Signature, Key Encipherment",
                    "extendedKeyUsage": "TLS Web Server Authentication, TLS Web Client Authentication",
                    "basicConstraints": "CA:FALSE",
                    "subjectKeyIdentifier": "9E:7F:75:D2:6D:F4:B2:AD:A8:89:79:9A:ED:B0:C7:DC:F7:60:F8:F9",
                    "authorityKeyIdentifier": "keyid:A8:4A:6A:63:04:7D:DD:BA:E6:D1:39:B7:A6:45:65:EF:F3:A8:EC:A1\n",
                    "authorityInfoAccess": "OCSP - URI:http:\/\/ocsp.int-x3.letsencrypt.org\/\nCA Issuers - URI:http:\/\/cert.int-x3.letsencrypt.org\/\n",
                    "subjectAltName": "DNS:example.com",
                    "certificatePolicies": "Policy: 2.23.140.1.2.1\nPolicy: 1.3.6.1.4.1.44947.1.1.1\n  CPS: http:\/\/cps.letsencrypt.org\n  User Notice:\n    Explicit Text: This Certificate may only be relied upon by Relying Parties and only in accordance with the Certificate Policy found at https:\/\/letsencrypt.org\/repository\/\n"
                }
            }
        },
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingQuota($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "enable"
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingFTPStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "disable"
}
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
-d '{"server":"user-servers-001","domain":"example.com","status":"enable"}'
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
-d '{"server":"user-servers-001","domain":"example.com"}'
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
            "count": 1,
            "items": [
                {
                    "address": "alias@example.com",
                    "goto": "test@example.com",
                    "status": "enable",
                    "created": "2016-07-23T21:45:24+0000",
                    "modified": "2016-07-23T21:45:24+0000"
                }
            ]
        },
        "mailbox": {
            "max": 0,
            "count": 1,
            "items": [
                {
                    "altEmail": "edu@hosting4devs.com",
                    "username": "test@example.com",
                    "status": "enable",
                    "name": "Test",
                    "localPart": "test",
                    "quota": {
                        "active": false,
                        "size": "0"
                    },
                    "created": "2016-07-23T14:15:09+0000",
                    "modified": "2016-08-16T10:50:23+0000"
                }
            ]
        },
        "mailDir": "\/home\/example.com\/Maildir",
        "created": "2016-07-23T14:14:27+0000",
        "modified": "2016-08-18T22:11:09+0000",
        "antispam": {
            "status": "enabled",
            "required_score": "7",
            "subject_tag": "Spamito",
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
-d '{"server":"user-servers-001","domain":"example.com","value":"gmail.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addHostingToBlackList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com","value":"white-list-domain.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addHostingToWhiteList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com","value":"gmail.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteHostingFromBlackList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com","value":"white-list-domain.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteHostingFromWhiteList($server,$domain,$value);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example-2.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSpamassassinPreferences($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example-2.com","type":"black"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingAntispamList($server,$domain,$type);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example-2.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","score":"7","tag":"Spamito"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingSpamassassinPreferences($server,$domain,$score,$tag);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test","password":"123456","name":"Test","altEmail":"edu@hosting4devs.com","quota":"0"}'
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test_user"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxInfo($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test","password":"123456"}'
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test","size":"111"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxQuota($server,$domain,$username,$size);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21208,
    "message": "Param with name \"quota\" does not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test_user","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxStatus($server,$domain,$username,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"alias","goto":"test@example.com"}'
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test_user"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxAliasInfo($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test_user","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxAliasStatus($server,$domain,$username,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"alias"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMailboxAlias($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test_user"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMailbox($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxesAliases($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailboxes($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailServiceStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","status":"enable"}'
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
-d '{"server":"user-servers-001","domain":"example.com"}'
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
                "1": {
                    "username": "laravel",
                    "description": "Bbdd MySQL de probas",
                    "created": "2016-07-23T14:36:37+0000",
                    "modified": "2016-07-23T14:36:37+0000",
                    "type": "mysql"
                }
            },
            "dbs": [
                {
                    "database": "laravel",
                    "databaseDir": "\/home\/example.com\/.db_mysql\/laravel",
                    "accessHost": "%",
                    "description": "Probas",
                    "created": "2016-07-23T14:37:00+0000",
                    "modified": "2016-07-23T14:37:00+0000",
                    "type": "mysql",
                    "user": "laravel"
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
-d '{"server":"user-servers-001","domain":"example.com","username":"pako","password":"pakopako","description":"pako"}'
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
-d '{"server":"user-servers-001","domain":"example.com","username":"test_user","password":"qweasd123"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->changeMySQLUserPassword($server,$domain,$username,$password);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","database":"pako","username":"pakito","dbDescription":"pako db"}'
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
-d '{"server":"user-servers-001","domain":"example.com","database":"test_database"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMySQLDatabase($server,$domain,$database);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
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
-d '{"server":"user-servers-001","domain":"example.com","username":"pakito"}'
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
-d '{"server":"user-servers-001","domain":"example.com","database":"test_database","dbDescription":"database description","username":"test_user_ddbb","password":"qweasd123","userDescription":"user description"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMySQLDatabaseAndUser($server,$domain,$database,$dbDescription,$username,$password,$userDescription);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","size":"0"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingQuota($server,$domain,$size);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSHAuthMode($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSHStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","keyBase64":"c3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQ*******kwcmZpMHdLendLWUxJVnRqaW1kN2tvZm82VWNGaERhek5ZcXhmRXdxbTRtSHJjaEhDdndPb1k2Qm1YMnJLam16SXVvZWpWN1lKL1Z6VjAwVDh6dWRZb2c3dWROYlFUck5wOGZOb0ZzRHFUaTFnUFl0YXlxTWo3dWJGcU1wT25MNWs2amF3L3c3Mnh3cERVOFB6SXJITTQzV3pxY2ZZSmhUMXZTcVFtY1dxc3ozSzc1Y1ZQaHNMMXZrazY4eGtkdG9yUTBDYXBFWHdIRkpTVlVMMC9KeGQ0QTM0QVA2N2RHRHJ4Q29xVzAvclg4YkI1Mkt2UFJqcXBoRFF1MUdZN09XaXYzU0NXa3ZaZHg5clJPb0ZKV3VGZWpnbkZEWEh3Rm1BbVd6dERmbXpCdkpIU0Y5TUwyNFowdmR2VUh4bkpUemZyZE4rMVFXalZKcy9pODlpSXIgZWR1YXJkb0BhbmF2YWxsYXN1aXphLmNvbQ0K","description":"Test"}'
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
-d '{"server":"server","domain":"domain","fingerprint":"fingerprint"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSSHPublicKey($server,$domain,$fingerprint);
```

> The above command returns JSON structured like this:

```json
null
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
-d '{"server":"user-servers-001","domain":"example.com","mode":"onlyPublicKey"}'
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
-d '{"server":"user-servers-001","domain":"example.com","status":"enable"}'
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
-d '{"server":"user-servers-001","domain":"example.com","certificateCrtBase64":"LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tDQpNSUlGR0RDQ0JBQ2dBd0lCQWdJU0E******zWVBqWlFRMzVNYkE2ZjdrQU1BMEdDU3FHU0liM0RRRUJDd1VBDQpNRW94Q3pBSkJnTlZCQVlUQWxWVE1SWXdGQVlEVlFRS0V3MU1aWFFuY3lCRmJtTnllWEIwTVNNd0lRWURWUVFEDQpFeHBNWlhRbmN5QkZibU55ZVhCMElFRjFkR2h2Y21sMGVTQllNekFlRncweE5qQTRNVEF4TWpJME1EQmFGdzB4DQpOakV4TURneE1qSTBNREJhTUNVeEl6QWhCZ05WQkFNVEdteGhjbUYyWld3dVpHOHVaV1IxYzJGc1ozVmxjbTh1DQpZMjl0TUlJQklqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUF3OUNGZ3ZBQy9zNks2MlVlDQp2aEFpM09Qa1FFU3FXVVRsM1NNWXhIcndEQ0FxZEVtdytoTVJtVlBoSjFLcGNwckU4aTBFRWIreFRSTFBCUVg0DQpkekNnUE5IczVYckthbFFPYUVoc3VtUHB3ci9KdmtxdWUxMUFIRXVDZ0xvT2pzMTVGRXp3TmdTVm9JbGFuM0JpDQowdmdENGdGRGNEZmM3bXBzbFBGb0U3U3NlSFJZc0IxL1hsdzBUNTJ5QjVkbElSUjRNaEt0ZTlMWE81Rno0SGNoDQpLMmhRQit5cFZuRnNWWFpYcXpkdVMvNUVyMDhVQjBQRXhKVkhnUiszNE9rM0lQUnk1ekFrMitKMHpvTTVrNHRTDQpaeWVHTmwrZDh0aWlTeVZZTUlaNUo1V2MyRjN4WWsyR1J3bElUMUt2ZXUxbnBrU2Y0WlQ4dUFjQ090OGc3THZ1DQpmOGFWVXdJREFRQUJvNElDR3pDQ0FoY3dEZ1lEVlIwUEFRSC9CQVFEQWdXZ01CMEdBMVVkSlFRV01CUUdDQ3NHDQpBUVVGQndNQkJnZ3JCZ0VGQlFjREFqQU1CZ05WSFJNQkFmOEVBakFBTUIwR0ExVWREZ1FXQkJTZWYzWFNiZlN5DQpyYWlKZVpydHNNZmM5MkQ0K1RBZkJnTlZIU01FR0RBV2dCU29TbXBqQkgzZHV1YlJPYmVtUldYdjg2anNvVEJ3DQpCZ2dyQmdFRkJRY0JBUVJrTUdJd0x3WUlLd1lCQlFVSE1BR0dJMmgwZEhBNkx5OXZZM053TG1sdWRDMTRNeTVzDQpaWFJ6Wlc1amNubHdkQzV2Y21jdk1DOEdDQ3NHQVFVRkJ6QUNoaU5vZEhSd09pOHZZMlZ5ZEM1cGJuUXRlRE11DQpiR1YwYzJWdVkzSjVjSFF1YjNKbkx6QWxCZ05WSFJFRUhqQWNnaHBzWVhKaGRtVnNMbVJ2TG1Wa2RYTmhiR2QxDQpaWEp2TG1OdmJUQ0IvZ1lEVlIwZ0JJSDJNSUh6TUFnR0JtZUJEQUVDQVRDQjVnWUxLd1lCQkFHQzN4TUJBUUV3DQpnZFl3SmdZSUt3WUJCUVVIQWdFV0dtaDBkSEE2THk5amNITXViR1YwYzJWdVkzSjVjSFF1YjNKbk1JR3JCZ2dyDQpCZ0VGQlFjQ0FqQ0JuZ3lCbTFSb2FYTWdRMlZ5ZEdsbWFXTmhkR1VnYldGNUlHOXViSGtnWW1VZ2NtVnNhV1ZrDQpJSFZ3YjI0Z1lua2dVbVZzZVdsdVp5QlFZWEowYVdWeklHRnVaQ0J2Ym14NUlHbHVJR0ZqWTI5eVpHRnVZMlVnDQpkMmwwYUNCMGFHVWdRMlZ5ZEdsbWFXTmhkR1VnVUc5c2FXTjVJR1p2ZFc1a0lHRjBJR2gwZEhCek9pOHZiR1YwDQpjMlZ1WTNKNWNIUXViM0puTDNKbGNHOXphWFJ2Y25rdk1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQllCWnJiDQpNc3NpcWk3MDBFYUxLRVNhbFVTVm45RjR3VmprSUk2T29Wd2VZMXlrcWs3S201U2wzQWFWUWgwdkpoSjJuRUJIDQovLzJaVmhJVlFmVlpLMWtSSTZjS2xZclhXU3hnNGZkUitRTzNVcTd5OWJJWVRiQU9zbVNNc0V0VDYyeXVuNWdQDQppSjNzd042TGYrM2JjK2xsbms4TWpKNTRwcTNvcHd2Q2VhWU8xVWI3QXlSMXhsdE1MeDBLTEYyOUcwSEpic0h3DQpkSjZ3UXZUbll6WlhRc0JnSXA2cU54Nmo5NjI0a2JuZC91dWxEdHhXaHZFN3prT0MwVDFSRnNLQnhJQ2ozQWlGDQprYXE3bldOcVFrblRaSFlUM1RjRmdQMllRaTlqMHR4QTFiOWo2NHFsNjJ2cExnMnhPRTZvd1pVQURBWG5CTjNoDQpHckJOODRZN29tYlZyT1EwDQotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0t","privateKeyBase64":"LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tDQpNSUlFdkFJQkFEQU******aGtpRzl3MEJBUUVGQUFTQ0JLWXdnZ1NpQWdFQUFvSUJBUUREMElXQzhBTCt6b3JyDQpaUjYrRUNMYzQrUkFSS3BaUk9YZEl4akVldkFNSUNwMFNiRDZFeEdaVStFblVxbHltc1R5TFFRUnY3Rk5FczhGDQpCZmgzTUtBODBlemxlc3BxVkE1b1NHeTZZK25DdjhtK1NxNTdYVUFjUzRLQXVnNk96WGtVVFBBMkJKV2dpVnFmDQpjR0xTK0FQaUFVTndOOXp1YW15VThXZ1R0S3g0ZEZpd0hYOWVYRFJQbmJJSGwyVWhGSGd5RXExNzB0YzdrWFBnDQpkeUVyYUZBSDdLbFdjV3hWZGxlck4yNUwva1N2VHhRSFE4VEVsVWVCSDdmZzZUY2c5SExuTUNUYjRuVE9nem1UDQppMUpuSjRZMlg1M3kyS0pMSlZnd2hua25sWnpZWGZGaVRZWkhDVWhQVXE5NjdXZW1SSi9obFB5NEJ3STYzeURzDQp1KzUveHBWVEFnTUJBQUVDZ2dFQWRsU29tZnZZazRyVlFITVhKTnd6ZFREeVdqUWtqVldwWXYwMmxtV0Vjbzl0DQptR0IvNWw5bm56U2xOMUlvdSt6elh6WDg0NHpuNUIrZG92ZDhzdXBicXVWaE56d0Eza2gxZkdkbjdTczd0RWlaDQo3YmpMd0JrV0NRTklsZW5acWtwWkJQK0ptZHNqWUtRZ2M0RkM5eUtSbGg0VlZ0Y3JWNWhRamFGa3Q2UFRKZVo2DQpwVHA0STdpLzI5MGt4ZzJoNzd0UW9DMFBtMDFGbjRGRE53OHc3RGl0SkRrUXZEMUxFLzdoQXJQUy9RcDdvR1FODQpmbi85VnN0eTZUVFVZZXpUV3RETi8vYWxJRjRTMi9FRGNRYUhwaU5CdHAxczU3NnJmbmZSYW0xMmhJOHZRWkl3DQpJeDViQjh0M0xseCsyUTVDVTBvNFJrQlFaZTljN2RFTG9EdTF4b3Fkd1FLQmdRRGh3MWJFWGtkUXd5bDBKbSsrDQpjVTVrSzh0ZkV0cENXV24vY2h5VWpKVkppeWZ2OHl5bUdJQTJDbGs0QVNWbGh1cy9oUjdpSjRkZ29seGo4UE1aDQpjUDA2NVdadDdPNEdWZzVrbDQ1alRrWWk1Uy9sK2R2SndzQlhiTi9iQkNxUUQvNGNMejU0dUFCTVRseFVPZ0EyDQpyV3NWWWhyMGlLbjNxYUN1WmM4VmlQUDhPUUtCZ1FEZUNsa3JmRW0zSDhaaHpIUmRxUmhGcFRyc05PclIrZDhLDQpYaWIrR3lmRnZQcjlXc3oyVW1qRkx0MFczeXhoMTFWajZqc0xlVXBYa25hMDArWmNoUXN6UHBqVytiQ3hvWjZ5DQpZRGdKVDVLb1VJdXFaQUlnR0VMNkxxME12TFVOQ1ZDeUxwaHdEbHdROWcyZWVCaVU1VGk0Tysva2FXTERSbG91DQpkMExCQWNoMTZ3S0JnQlRJVjZkeUNseWI2cWYvbGMvUlBHY3FST2wyb2RMenlqY3l1UURQeERwbDdnSS92MzkyDQp4KzZ4bXk3MXBBeXBrK1JnQzh6RDJNbURpTC9HZ1lwNUJVYXpzVzh6SFdKRjc4TkExR0c5NWVUMmRpZFVqZkFQDQoxb2IxeGRHeW0zeHhqSEhwdzNWM2NzZVRleHBoMEgwNEQ2Q0RUSG53VHIwMngwem1vRjZhSWVPNUFvR0FUY2cyDQpRSU9EbDBEc1QrbzlnV253OU1UVEJWZnNRcTVUc2VBVnJNSjZoa3lUYUJsYzM1VXkycEIySnNMN1d6TUIyTVIrDQo5cUFBcVBqSDJNUzZXQUxMVDZKSURGYmZ6UG9mQzhHbEg2M2VaRlFDK1NlYmp2Nnd4ODkrRTQ0dnBtZHkrMWhUDQpVajNWaHFPTFZjNGdYbGlHTEJQakQ1TFRaRERLK3FnUW5HZ3hmdzBDZ1lBUURIcWtobHJUd2tnRHY2YTF2Z1BGDQpXL2RmY1dIQU9MNTJIbTlGVGw4Ky9VeS85S1dHMHRHOHAxYmFSdTRsbFBvS2JvcnZ3N21IWldVd1lramtMQkhVDQpVSS9qN2JTVjU3OUNzZ202MmNreXdHR3dTazBxUkx1TEF3SmpNazNidFZrUS9oK2k2QlhGUHdLempFSlZPYTFtDQpRSU5lMjRqR0luS3VOVFBhcXl3RGp3PT0NCi0tLS0tRU5EIFBSSVZBVEUgS0VZLS0tLS0=","CABundleBase64":"******1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tDQpNSUlFa2pDQ0EzcWdBd0lCQWdJUUNnRkJRZ0FBQVZPRmMyb0xoZXluQ0RBTkJna3Foa2lHOXcwQkFRc0ZBREEvDQpNU1F3SWdZRFZRUUtFeHRFYVdkcGRHRnNJRk5wWjI1aGRIVnlaU0JVY25WemRDQkRieTR4RnpBVkJnTlZCQU1UDQpEa1JUVkNCU2IyOTBJRU5CSUZnek1CNFhEVEUyTURNeE56RTJOREEwTmxvWERUSXhNRE14TnpFMk5EQTBObG93DQpTakVMTUFrR0ExVUVCaE1DVlZNeEZqQVVCZ05WQkFvVERVeGxkQ2R6SUVWdVkzSjVjSFF4SXpBaEJnTlZCQU1UDQpHa3hsZENkeklFVnVZM0o1Y0hRZ1FYVjBhRzl5YVhSNUlGZ3pNSUlCSWpBTkJna3Foa2lHOXcwQkFRRUZBQU9DDQpBUThBTUlJQkNnS0NBUUVBbk5NTThGcmxMa2UzY2wwM2c3Tm9ZekRxMXpVbUdTWGh2YjQxOFhDU0w3ZTRTMEVGDQpxNm1lTlFoWTdMRXF4R2lIQzZQamRlVG04NmRpY2JwNWdXQWYxNUdhbi9QUWVHZHh5R2tPbFpIUC91YVo2V0E4DQpTTXgreWsxM0VpU2RSeHRhNjduc0hqY0FISnlzZTZjRjZzNUs2NzFCNVRhWXVjdjliVHlXYU44aktrS1FESVowDQpaOGgvcFpxNFVtRVVFejlsNllLSHk5djZEbGIyaG9uemhUK1hocSt3M0JydmF3MlZGbjNFSzZCbHNwa0VObldBDQphNnhLOHh1UVNYZ3ZvcFpQS2lBbEtRVEdkTURRTWMyUE1UaVZGcnFvTTdoRDhiRWZ3ekIvb25reEV6MHROdmpqDQovUEl6YXJrNU1jV3Z4STBOSFdRV002cjZoQ20yMUF2QTJIM0Rrd0lEQVFBQm80SUJmVENDQVhrd0VnWURWUjBUDQpBUUgvQkFnd0JnRUIvd0lCQURBT0JnTlZIUThCQWY4RUJBTUNBWVl3ZndZSUt3WUJCUVVIQVFFRWN6QnhNRElHDQpDQ3NHQVFVRkJ6QUJoaVpvZEhSd09pOHZhWE55Wnk1MGNuVnpkR2xrTG05amMzQXVhV1JsYm5SeWRYTjBMbU52DQpiVEE3QmdnckJnRUZCUWN3QW9ZdmFIUjBjRG92TDJGd2NITXVhV1JsYm5SeWRYTjBMbU52YlM5eWIyOTBjeTlrDQpjM1J5YjI5MFkyRjRNeTV3TjJNd0h3WURWUjBqQkJnd0ZvQVV4S2V4cEhzc2NmcmI0VXVRZGYvRUZXQ0ZpUkF3DQpWQVlEVlIwZ0JFMHdTekFJQmdabmdRd0JBZ0V3UHdZTEt3WUJCQUdDM3hNQkFRRXdNREF1QmdnckJnRUZCUWNDDQpBUllpYUhSMGNEb3ZMMk53Y3k1eWIyOTBMWGd4TG14bGRITmxibU55ZVhCMExtOXlaekE4QmdOVkhSOEVOVEF6DQpNREdnTDZBdGhpdG9kSFJ3T2k4dlkzSnNMbWxrWlc1MGNuVnpkQzVqYjIwdlJGTlVVazlQVkVOQldETkRVa3d1DQpZM0pzTUIwR0ExVWREZ1FXQkJTb1NtcGpCSDNkdXViUk9iZW1SV1h2ODZqc29UQU5CZ2txaGtpRzl3MEJBUXNGDQpBQU9DQVFFQTNUUFhFZk5qV0RqZEdCWDdDVlcrZGxhNWNFaWxhVWNuZThJa0NKTHhXaDlLRWlrM0pIUlJIR0pvDQp1TTJWY0dmbDk2UzhUaWhSelp2b3JvZWQ2dGk2V3FFQm10enczV29kYXRnK1Z5T2VwaDRFWXByLzF3WEt0eDgvDQp3QXBJdkpTd3RtVmk0TUZVNWFNcXJTREU2ZWE3M01qMnRjTXlvNWpNZDZqbWVXVUhLOHNvL2pvV1VvSE9VZ3d1DQpYNFBvMVFZeiszZHN6a0RxTXA0ZmtseEJ3WFJzVzEwS1h6UE1UWitzT1BBdmV5eGluZG1qa1c4bEd5K1FzUmxHDQpQZlorRzZaNmg3bWplbTBZK2lXbGtZY1Y0UElXTDFpd0JpOHNhQ2JHUzVqTjJwOE0rWCtRN1VOS0VrUk9iM042DQpLT3FrcW01N1RIMkgzZURKQWtTbmg2L0RORnUwUWc9PQ0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQ==","install":"true"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addAndInstallSSLCertificate($server,$domain,$certificateCrtBase64,$privateKeyBase64,$CABundleBase64,$install);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSSLCertificate($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSLCertificateInformation($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSLStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21701,
    "message": "\"example.com\" hosting not exist!",
    "data": []
}
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
-d '{"server":"user-servers-001","domain":"example.com","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingSSLStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
}
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
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"user-servers-001","domain":"example.com","processManager":"php-7"}'
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

`PATCH  /v1/server/:server/hosting/:domain/process-manager`

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
-d '{"server":"user-servers-001","domain":"example.com"}'
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
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","deployType":"deployType","gitUrl":"gitUrl","gitBranch":"gitBranch","localPath":"localPath","deployScript":"deployScript"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createGitDeployConfig($server,$domain,$deployType,$gitUrl,$gitBranch,$localPath,$deployScript);
```

> The above command returns JSON structured like this:

```json
null
```

Configure git deploy.

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
deployType | true | Deploy type | enum | ["auto","manual"] | auto
gitUrl | true | Git URL (SSH not HTTP. Sample: git@github.com:vendor/repo.git) | string | - | -
gitBranch | true | Git branch name | string | - | -
localPath | true | Deploy path | string | - | -
deployScript | true | Script | string | - | -
## Update git deploy configuration.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/deploy/git" \
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","deployType":"deployType","gitUrl":"gitUrl","gitBranch":"gitBranch","localPath":"localPath","deployScript":"deployScript"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->updateGitDeployConfig($server,$domain,$deployType,$gitUrl,$gitBranch,$localPath,$deployScript);
```

> The above command returns JSON structured like this:

```json
null
```

Update git deploy configuration.

### HTTP Request

`PATCH  /v1/server/:server/hosting/:domain/deploy/git`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
domain | true | Hostname | string | - | -

### Body parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
deployType | true | Deploy type | enum | ["auto","manual"] | auto
gitUrl | true | Git URL (SSH not HTTP. Sample: git@github.com:vendor/repo.git) | string | - | -
gitBranch | true | Git branch name | string | - | -
localPath | true | Deploy path | string | - | -
deployScript | true | Script | string | - | -
## Set web document root path.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/web/document-root" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","domain":"domain","path":"path"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setWebDocumentRoot($server,$domain,$path);
```

> The above command returns JSON structured like this:

```json
null
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
-d '{"server":"user-servers-001","domain":"example.com","email":"edu@example.com"}'
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
    "data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDSpVx5v7YIvbqdsTBVWblO3e1P38+2Hs+KbxPnOlPirPcOdXqC3qJk6tyV2DGF+D\/DQXGq\/aha3kuPQ8SxreiBmICGjLYnfCDdxnC426\/W8ij1r2UFQ\/q5prvw9*******ThZjOhKzsLeKQ51tsj1aLXSzysfhTVkUDlm\/vlZQ\/JTcAvLj3uXyGL+pMZTl4io\/WJFwOWpRQry7zrFv2qDLXngEWcxYu6Jl9Rz+B65Q7n9eJVz2A1rwxWhy4rbOBkbSQHL3VRNWF4Qsduc1v+Ptdkw49Oh+yYpMwfMG4YvFYH7yt9WMk\/DdHSAmKKeImA0FUUvkuPS9w4uuZaSCr6cL edu@example.com\n"
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
-d '{"server":"user-server-01"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getAvailableRecipes($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": [
        {
            "recipe": "apache",
            "description": "Apache web server",
            "isAvailableToInstall": false,
            "packages": [
                "apache"
            ]
        },
        {
            "recipe": "apache-itk",
            "description": "Apache web server with ITK MPM @deprecated",
            "isAvailableToInstall": false,
            "packages": [
                "apache-itk"
            ]
        },
        {
            "recipe": "mail",
            "description": "Mail recipe: postfix, dovecot and spamassassin",
            "isAvailableToInstall": true,
            "packages": [
                "postfix",
                "dovecot",
                "spamassassin"
            ]
        },
        {
            "recipe": "mysql",
            "description": "MySQL Server",
            "isAvailableToInstall": true,
            "packages": [
                "mysql"
            ]
        },
        {
            "recipe": "nginx",
            "description": "Nginx server",
            "isAvailableToInstall": false,
            "packages": [
                "nginx"
            ]
        },
        {
            "recipe": "quota",
            "description": "Quota packages",
            "isAvailableToInstall": true,
            "packages": [
                "quota"
            ]
        },
        {
            "recipe": "ssh-ftp",
            "description": "VSFTP and SSH configuration",
            "isAvailableToInstall": true,
            "packages": [
                "ftp",
                "ssh"
            ]
        },
        {
            "recipe": "php-5.5",
            "description": "PHP 5.5 \"Full equip\"",
            "isAvailableToInstall": false,
            "packages": [
                "php5.5-fpm"
            ]
        },
        {
            "recipe": "php-5.6",
            "description": "PHP 5.6 \"Full equip\"",
            "isAvailableToInstall": false,
            "packages": [
                "php5.6-fpm"
            ]
        },
        {
            "recipe": "php-7",
            "description": "PHP 7 \"Full equip\"",
            "isAvailableToInstall": false,
            "packages": [
                "php7-fpm"
            ]
        }
    ]
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
-d '{"server":"user-servers-001"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getServerRecipes($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": []
}
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
-d '{"server":"user-server-01","recipes":["php-5.6"]}'
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
    "data": "0a974f39387c94b3644fa5aa4881eb9f"
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
