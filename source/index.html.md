---
title: API Reference

language_tabs:
- shell
- php

toc_footers:
- <a href='https://hosting4devs.com'>Manage servers and web apps easily with hosting4devs.</a>
- <a href='https://cloud.hosting4devs.com/signup'>Sign Up</a>
- <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

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
        "fi9CvJ-001",
        "fi9CvJ-002",
        "fi9CvJ-003",
        "fi9CvJ-004",
        "fi9CvJ-005",
        "fi9CvJ-006",
        "fi9CvJ-007",
        "fi9CvJ-008",
        "fi9CvJ-009",
        "fi9CvJ-010",
        "fi9CvJ-011",
        "fi9CvJ-012",
        "fi9CvJ-013",
        "fi9CvJ-014",
        "fi9CvJ-015",
        "fi9CvJ-016"
    ]
}
```

Get list of active servers.

### HTTP Request

`GET  /v1/server/list`


## Get server spamassassin preferences.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/antispam" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004"}'
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
-d '{"server":"lnqlqx-004","tag":"test-tag","score":"10"}'
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
## Add new firewall rule.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/rule" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","priority":"1","direction":"INPUT","action":"ACCEPT","protocol":"tcp","source":"111.111.111.111","destination":"222.222.222.222","sourcePort":"8001","destinationPort":"8002","replace":"true"}'
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
## Block IP.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/block/:ip" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","ip":"123.123.123.123"}'
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

## Get firewall rules.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/rules" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012"}'
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
-d '{"server":"lnqlqx-004","priority":"1","direction":"INPUT"}'
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
## Unblock IP.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/firewall/block/:ip" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","ip":"123.123.123.123"}'
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

## Get installed packages.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/packages" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012"}'
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
            "package": "php7-fpm",
            "version": "7.0",
            "installed": "2016-04-26T20:23:12+0000"
        },
        {
            "package": "ftp",
            "version": "3.0.2",
            "installed": "2016-04-26T20:24:33+0000"
        },
        {
            "package": "ssh",
            "version": "6.6p1",
            "installed": "2016-04-26T20:24:33+0000"
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

## Get detailed server settings.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/settings" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"fi9CvJ-016"}'
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
            "description": "Ubuntu 14.04.2 LTS"
        },
        "kernel_release": "3.13.0-46-generic",
        "timezone": "Etc\/UTC",
        "date": "2016-04-28T21:10:25+0000",
        "memory": {
            "total": "501756",
            "used": "375028",
            "free": "126728",
            "shared": "20988",
            "buffers": "8832",
            "cached": "127636",
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

## Get hostings.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hostings" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004"}'
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
        "test-domain.com": {
            "domain": "test-domain.com",
            "status": "enable",
            "server": "apache",
            "processManager": "php-5.6",
            "created": "2016-04-05T23:22:50+0000",
            "modified": "2016-04-05T23:22:50+0000"
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
-d '{"server":"lnqlqx-004"}'
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
            "domain": "test-domain.com",
            "status": "enable",
            "alias": "test alias",
            "ip": "*",
            "documentRoot": "\/home\/test-domain.com\/htdocs",
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
                "username": "test-domaincom",
                "homeDir": "\/home\/test-domain.com"
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

## Get detailed server info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/info" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-001"}'
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
            "uptime": "39667449.94",
            "load_avg": {
                "last": 1.13,
                "5min": 1.1,
                "15min": 1.12,
                "nproc": "4"
            },
            "memory_usage": {
                "total": "4021048",
                "used": "3772616",
                "free": "248432",
                "shared": "21048",
                "buffers": "160512",
                "cached": "2895456",
                "unit": "KB"
            },
            "filesystems_usage": {
                "\/": {
                    "total": "19557",
                    "used": "7307",
                    "free": "11235",
                    "percentage_of_use": "40",
                    "filesystem": "\/dev\/root",
                    "type": "ext4",
                    "unit": "MB"
                },
                "\/home": {
                    "total": "1857474",
                    "used": "88420",
                    "free": "1674677",
                    "percentage_of_use": "6",
                    "filesystem": "\/dev\/sda3",
                    "type": "ext4",
                    "unit": "MB"
                }
            }
        },
        "network": {
            "eth0": {
                "IPv4": "37.187.126.170",
                "IPv6": "fe80::222:4dff:feae:339f"
            }
        },
        "services": {
            "count": 1,
            "items": {
                "metrics": {
                    "serviceName": "h4d-metrics",
                    "publicName": "metrics",
                    "isEnabled": true,
                    "isRunning": true
                }
            }
        },
        "packages": {
            "count": 0,
            "items": []
        },
        "time": {
            "timezone": "Etc\/UTC",
            "date": "2016-04-30T08:59:16+0000"
        },
        "hostings": {
            "count": "0"
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
-d '{"server":"lnqlqx-004"}'
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
-d '{"server":"lnqlqx-004"}'
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
            "used": "2289",
            "free": "7319",
            "percentage_of_use": "24",
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
-d '{"server":"lnqlqx-011"}'
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
        "5min": 0.03,
        "15min": 0.09,
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
-d '{"server":"lnqlqx-004"}'
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
        "total": "2000908",
        "used": "976128",
        "free": "1024780",
        "shared": "20720",
        "buffers": "87820",
        "cached": "544648",
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
-d '{"server":"lnqlqx-012"}'
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
        "h4d-metrics": {
            "serviceName": "h4d-metrics",
            "publicName": "metrics",
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

## Get server time information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/time" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012"}'
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
        "date": "2016-04-28T22:37:21+0200"
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

## Get server uptime.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/uptime" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004"}'
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
    "data": "1121373.70"
}
```

Get server uptime.

### HTTP Request

`GET  /v1/server/:server/uptime`

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
-d '{"server":"lnqlqx-004"}'
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
    "data": "5.5.47-0ubuntu0.14.04.1"
}
```

Get MySQL version.

### HTTP Request

`GET  /v1/server/:server/mysql/version`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -

## Set root password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/mysql/root-password" \
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","password":"qweasd123"}'
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

Set root password.

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
## Manage server service.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/service/:service/command" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012","service":"vsftpd","action":"stop"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->manageServerService($server,$service,$action);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21604,
    "message": "Service \"vsftpd\" is disabled!",
    "data": []
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
## Manage server service status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/service/:service/status" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012","service":"vsftpd","status":"disable"}'
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
## Get service information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/service/:service" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","service":"ftp"}'
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

## Set server timezone.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/time/timezone" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","timezone":"timezone"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setServerTimezone($server,$timezone);
```

> The above command returns JSON structured like this:

```json
null
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
## Reboot server.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/reboot" \
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->rebootServer($server);
```

> The above command returns JSON structured like this:

```json
null
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
-d '{"server":"lnqlqx-002"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->uninstallH4DCS($server);
```

> The above command returns JSON structured like this:

```json
{
    "code": 20000,
    "message": "Execution error!",
    "data": []
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
## Execute a snippet with the given token.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/snippet/:token" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"fi9CvJ-016","token":"f2afce36b66d58bc4d704a3037b503ea"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->executeSnippet($server,$token);
```

> The above command returns JSON structured like this:

```json
{
    "code": 20000,
    "message": "Execution error!",
    "data": []
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
## Change hosting password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/pass" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","password":"qweasd123"}'
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
## Change hosting process manager.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/process-manager" \
-X PATCH \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","processManager":"php-5.6"}'
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
## Create new hosting.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"fi9CvJ-016","domain":"test.com","alias":"www.test.com","mailEnable":false,"processManager":"php-7","password":"23234324234123"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createHosting($server,$domain,$alias,$mailEnable,$processManager,$password);
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
## Delete a hosting.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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

## Get hosting FTP status.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ftp/status" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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
    "data": "enable"
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","status":"enable"}'
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
## Get hosting total disk usage.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/info/disk-usage" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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
        "size": "36",
        "unit": "KB",
        "path": "\/home\/test-000.com"
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","deep":"3"}'
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
            "size": "4.0",
            "unit": "KB",
            "path": "\/home\/test-000.com\/Maildir"
        },
        {
            "size": "4.0",
            "unit": "KB",
            "path": "\/home\/test-000.com\/logs"
        },
        {
            "size": "4.0",
            "unit": "KB",
            "path": "\/home\/test-000.com\/.ssh"
        },
        {
            "size": "8.0",
            "unit": "KB",
            "path": "\/home\/test-000.com\/htdocs"
        },
        {
            "size": "36",
            "unit": "KB",
            "path": "\/home\/test-000.com"
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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
        "domain": "test-000.com",
        "status": "enable",
        "alias": "My test-domain.com alias",
        "ip": "*",
        "documentRoot": "\/home\/test-000.com\/htdocs",
        "description": null,
        "logDir": "\/home\/test-000.com\/logs",
        "server": "apache",
        "processManager": "php-5.5",
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
        "created": "2016-04-22T16:57:17+0000",
        "modified": "2016-04-22T16:57:17+0000",
        "systemUser": {
            "username": "test-000com",
            "homeDir": "\/home\/test-000.com"
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
            "mailDir": "\/home\/test-000.com\/Maildir",
            "created": "2016-04-22T16:57:17+0000",
            "modified": "2016-04-22T16:57:19+0000",
            "antispam": {
                "status": "enabled",
                "required_score": "10",
                "subject_tag": "test-tag"
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
        "sslInfo": []
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingQuota($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "active": false,
        "soft": 0,
        "hard": 0,
        "unit": "KB"
    }
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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

## New mailbox alias.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","goto":"test@mail.com"}'
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
## Delete a mailbox alias.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user"}'
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

## Get mailbox alias info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/alias" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxAliasInfo($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "address": "test_user@test-000.com",
        "goto": "test@mail.com",
        "status": "enable",
        "created": "2016-04-22T16:57:28+0000",
        "modified": "2016-04-22T16:57:28+0000"
    }
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxAliasStatus($server,$domain,$username,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
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
## Add a domain to black list.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/antispam/black-list" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","value":"black-list-domain.com"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","value":"white-list-domain.com"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","value":"black-list-domain.com"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","value":"white-list-domain.com"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSpamassassinPreferences($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "status": "enabled",
        "required_score": "10",
        "subject_tag": "test-tag"
    }
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","type":"black"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingAntispamList($server,$domain,$type);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","score":"10","tag":"test-tag"}'
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
## Change mailbox password.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/pass" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","password":"qweasd123"}'
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
## Create new mailbox.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","password":"qweasd123","name":"Test Name","altEmail":"alt@mail.com","quota":"0"}'
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
## Delete a mailbox.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteMailbox($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
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

## Get mailbox info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxInfo($server,$domain,$username);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": {
        "altEmail": "alt@mail.com",
        "username": "test_user@test-000.com",
        "status": "enable",
        "name": "Test Name",
        "localPart": "test_user",
        "quota": {
            "active": false,
            "size": "0"
        },
        "created": "2016-04-22T16:57:25+0000",
        "modified": "2016-04-22T16:57:25+0000"
    }
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

## Set mailbox quota.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mailbox/:username/quota" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","size":"0"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxQuota($server,$domain,$username,$size);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setMailboxStatus($server,$domain,$username,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
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
## Get mailboxes aliases.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/aliases" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getMailboxesAliases($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
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

## Get hosting mail service detailed information.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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
        "mailDir": "\/home\/test-000.com\/Maildir",
        "created": "2016-04-22T16:57:17+0000",
        "modified": "2016-04-22T16:57:22+0000",
        "antispam": {
            "status": "enabled",
            "required_score": "10",
            "subject_tag": "test-tag",
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

## Get hosting mailboxes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mail/mailboxes" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailboxes($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingMailServiceStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "enable"
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","status":"enable"}'
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
## Create new MySQL database and user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/db-and-user" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","database":"test_database","dbDescription":"database description","username":"test_user_ddbb","password":"qweasd123","userDescription":"user description"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->createMySQLDatabaseAndUser($server,$domain,$database,$dbDescription,$username,$password,$userDescription);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
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
## Create new MySQL database and assign it to an existing user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/db" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","database":"test_database","username":"test_user","dbDescription":"database description"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","database":"test_database"}'
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
## Get hosting MySQL detailed info.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
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
            "users": 0,
            "dbs": 0
        },
        "items": {
            "users": [],
            "dbs": []
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","password":"qweasd123","description":"test description"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user","password":"qweasd123"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->changeMySQLUserPassword($server,$domain,$username,$password);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": true
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
## Delete a MySQL user.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/mysql/user/:username" \
-X DELETE \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","username":"test_user"}'
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

## Set hosting quota.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/quota" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","size":"0"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","status":"disable"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSHAuthMode($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "password"
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSHStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "enable"
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
-d '{"server":"server","domain":"domain","keyBase64":"keyBase64","description":"description"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->addSSHPublicKey($server,$domain,$keyBase64,$description);
```

> The above command returns JSON structured like this:

```json
null
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
-d '{"server":"server","domain":"domain","keyMD5":"keyMD5"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->deleteSSHPublicKey($server,$domain,$keyMD5);
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
keyMD5 | true | Public key (md5) | string | - | -
## Set SSH auth mode.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/hosting/:domain/ssh/auth-mode" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-004","domain":"test-000.com","mode":"onlyPublicKey"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","status":"enable"}'
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSLCertificateInformation($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21703,
    "message": "\"SSL Cert\" not exist!",
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
-d '{"server":"lnqlqx-004","domain":"test-000.com"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getHostingSSLStatus($server,$domain);
```

> The above command returns JSON structured like this:

```json
{
    "code": 10000,
    "message": "Success!",
    "data": "disable"
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
-d '{"server":"lnqlqx-004","domain":"test-000.com","status":"enable"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->setHostingSSLStatus($server,$domain,$status);
```

> The above command returns JSON structured like this:

```json
{
    "code": 21703,
    "message": "\"SSL Cert\" not exist!",
    "data": []
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
#Recipes
## Add new snippet.
```shell
curl "https://api.hosting4devs.com/v1/snippet" \
-X POST \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"title":"title","code":"code","interpreter":"interpreter","visibility":"visibility","notes":"notes"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->publishSnippet($title,$code,$interpreter,$visibility,$notes);
```

> The above command returns JSON structured like this:

```json
null
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

## Get available recipes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/available-recipes" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012"}'
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
            "isAvailableToInstall": true,
            "packages": [
                "apache"
            ]
        },
        {
            "recipe": "apache-itk",
            "description": "Apache web server with ITK MPM @deprecated",
            "isAvailableToInstall": true,
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
            "isAvailableToInstall": true,
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
            "isAvailableToInstall": false,
            "packages": [
                "ftp",
                "ssh"
            ]
        },
        {
            "recipe": "php-5.5",
            "description": "PHP 5.5 \"Full equip\"",
            "isAvailableToInstall": true,
            "packages": [
                "php5.5-fpm"
            ]
        },
        {
            "recipe": "php-5.6",
            "description": "PHP 5.6 \"Full equip\"",
            "isAvailableToInstall": true,
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

## Get snippet by token.
```shell
curl "https://api.hosting4devs.com/v1/snippet/:token" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"token":"f2afce36b66d58bc4d704a3037b503ea"}'
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
-d '{"server":"server","token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getSnippetExecutionInfo($server,$token);
```

> The above command returns JSON structured like this:

```json
null
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
            },
            "executions": {
                "2fc84567566082dba53ce9b1944fd2a4": {
                    "slave": "fi9CvJ-003",
                    "executionToken": "2fc84567566082dba53ce9b1944fd2a4",
                    "startDate": "2016-02-25T16:51:30+00:00",
                    "endDate": "2016-02-25T16:51:30+00:00",
                    "stdout": "MTQ1NjQxOTA5MA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-02-25T16:51:30+00:00",
                    "updatedAt": "2016-02-25T16:51:30+00:00"
                },
                "f05709abb95c6ad7ea103ba1abc94594": {
                    "slave": "fi9CvJ-003",
                    "executionToken": "f05709abb95c6ad7ea103ba1abc94594",
                    "startDate": "2016-02-25T16:53:25+00:00",
                    "endDate": "2016-02-25T16:53:26+00:00",
                    "stdout": "MTQ1NjQxOTIwNQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-02-25T16:53:25+00:00",
                    "updatedAt": "2016-02-25T16:53:26+00:00"
                },
                "74b72e0ba043b8a322e7e122820ed011": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "74b72e0ba043b8a322e7e122820ed011",
                    "startDate": "2016-03-02T18:41:35+00:00",
                    "endDate": "2016-03-02T18:41:35+00:00",
                    "stdout": "MTQ1Njk0NDEwMw==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T18:41:35+00:00",
                    "updatedAt": "2016-03-02T18:41:35+00:00"
                },
                "7834c893bbff5bb797cfe6e78d58b094": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "7834c893bbff5bb797cfe6e78d58b094",
                    "startDate": "2016-03-02T18:42:02+00:00",
                    "endDate": "2016-03-02T18:42:02+00:00",
                    "stdout": "MTQ1Njk0NDEzMA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T18:42:02+00:00",
                    "updatedAt": "2016-03-02T18:42:02+00:00"
                },
                "92f0bc082ac107852089308da9dcf5ba": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "92f0bc082ac107852089308da9dcf5ba",
                    "startDate": "2016-03-02T18:45:34+00:00",
                    "endDate": "2016-03-02T18:45:34+00:00",
                    "stdout": "MTQ1Njk0NDMzNA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T18:45:34+00:00",
                    "updatedAt": "2016-03-02T18:45:34+00:00"
                },
                "9358b158108f14c36defd8f18ab64af1": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "9358b158108f14c36defd8f18ab64af1",
                    "startDate": "2016-03-02T19:03:19+00:00",
                    "endDate": "2016-03-02T19:03:19+00:00",
                    "stdout": "MTQ1Njk0NTM5OQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:03:19+00:00",
                    "updatedAt": "2016-03-02T19:03:19+00:00"
                },
                "c97d9a981fdc2b17e6e2a6a302ee281a": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "c97d9a981fdc2b17e6e2a6a302ee281a",
                    "startDate": "2016-03-02T19:03:36+00:00",
                    "endDate": "2016-03-02T19:03:36+00:00",
                    "stdout": "MTQ1Njk0NTQxNg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:03:36+00:00",
                    "updatedAt": "2016-03-02T19:03:36+00:00"
                },
                "4b3bbf710dcc75fa00143e2fb905e3db": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "4b3bbf710dcc75fa00143e2fb905e3db",
                    "startDate": "2016-03-02T19:04:08+00:00",
                    "endDate": "2016-03-02T19:04:08+00:00",
                    "stdout": "MTQ1Njk0NTQ0OA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:04:08+00:00",
                    "updatedAt": "2016-03-02T19:04:08+00:00"
                },
                "47acbc17592c6cb5d4110f0aca979fd6": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "47acbc17592c6cb5d4110f0aca979fd6",
                    "startDate": "2016-03-02T19:27:31+00:00",
                    "endDate": "2016-03-02T19:27:32+00:00",
                    "stdout": "MTQ1Njk0Njg1MQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:27:31+00:00",
                    "updatedAt": "2016-03-02T19:27:32+00:00"
                },
                "b6b25e52f538928e4988645664b951a0": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "b6b25e52f538928e4988645664b951a0",
                    "startDate": "2016-03-02T19:27:44+00:00",
                    "endDate": "2016-03-02T19:27:44+00:00",
                    "stdout": "MTQ1Njk0Njg2NA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:27:44+00:00",
                    "updatedAt": "2016-03-02T19:27:44+00:00"
                },
                "5b5fe109d92e8033c5e11ff793cdd8a9": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "5b5fe109d92e8033c5e11ff793cdd8a9",
                    "startDate": "2016-03-02T19:27:54+00:00",
                    "endDate": "2016-03-02T19:27:54+00:00",
                    "stdout": "MTQ1Njk0Njg3NA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:27:54+00:00",
                    "updatedAt": "2016-03-02T19:27:54+00:00"
                },
                "28994c8853d6d2026db8ded4f68c0f11": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "28994c8853d6d2026db8ded4f68c0f11",
                    "startDate": "2016-03-02T19:28:14+00:00",
                    "endDate": "2016-03-02T19:28:15+00:00",
                    "stdout": "MTQ1Njk0Njg5NQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T19:28:14+00:00",
                    "updatedAt": "2016-03-02T19:28:15+00:00"
                },
                "0b125e66982d6cc2d4da5c1c170499f6": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "0b125e66982d6cc2d4da5c1c170499f6",
                    "startDate": "2016-03-02T20:18:23+00:00",
                    "endDate": "2016-03-02T20:18:23+00:00",
                    "stdout": "MTQ1Njk0OTE5Mw==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T20:18:23+00:00",
                    "updatedAt": "2016-03-02T20:18:23+00:00"
                },
                "560250246ad725f9e5b35eaa51fa8c6d": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "560250246ad725f9e5b35eaa51fa8c6d",
                    "startDate": "2016-03-02T20:20:25+00:00",
                    "endDate": "2016-03-02T20:20:26+00:00",
                    "stdout": "MTQ1Njk0OTMxNg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T20:20:25+00:00",
                    "updatedAt": "2016-03-02T20:20:26+00:00"
                },
                "765939e77710d3bebc51d7c68265578a": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "765939e77710d3bebc51d7c68265578a",
                    "startDate": "2016-03-02T20:26:15+00:00",
                    "endDate": "2016-03-02T20:26:15+00:00",
                    "stdout": "MTQ1Njk0OTY2NQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T20:26:15+00:00",
                    "updatedAt": "2016-03-02T20:26:15+00:00"
                },
                "6c4fb98c1c61305191e076d48196f820": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "6c4fb98c1c61305191e076d48196f820",
                    "startDate": "2016-03-02T21:00:15+00:00",
                    "endDate": "2016-03-02T21:00:15+00:00",
                    "stdout": "MTQ1Njk1MjQxNQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:00:15+00:00",
                    "updatedAt": "2016-03-02T21:00:15+00:00"
                },
                "7ad50f68e2933c4173f12da62e559436": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "7ad50f68e2933c4173f12da62e559436",
                    "startDate": "2016-03-02T21:00:34+00:00",
                    "endDate": "2016-03-02T21:00:36+00:00",
                    "stdout": "MTQ1Njk1MjQzNg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:00:34+00:00",
                    "updatedAt": "2016-03-02T21:00:36+00:00"
                },
                "540fb68e3a6054db2721620e0d35a485": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "540fb68e3a6054db2721620e0d35a485",
                    "startDate": "2016-03-02T21:01:25+00:00",
                    "endDate": "2016-03-02T21:01:25+00:00",
                    "stdout": "MTQ1Njk1MjQ4NQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:01:25+00:00",
                    "updatedAt": "2016-03-02T21:01:25+00:00"
                },
                "af0257696bf74fd7bd6ed1f66697aa71": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "af0257696bf74fd7bd6ed1f66697aa71",
                    "startDate": "2016-03-02T21:03:24+00:00",
                    "endDate": "2016-03-02T21:03:25+00:00",
                    "stdout": "MTQ1Njk1MjYwNQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:03:24+00:00",
                    "updatedAt": "2016-03-02T21:03:25+00:00"
                },
                "f783e37ec1e2f65ee0993451ed111543": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "f783e37ec1e2f65ee0993451ed111543",
                    "startDate": "2016-03-02T21:03:47+00:00",
                    "endDate": "2016-03-02T21:03:48+00:00",
                    "stdout": "MTQ1Njk1MjYyOA==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:03:47+00:00",
                    "updatedAt": "2016-03-02T21:03:48+00:00"
                },
                "a122d384f87a5b8424267275dcc52e35": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "a122d384f87a5b8424267275dcc52e35",
                    "startDate": "2016-03-02T21:55:33+00:00",
                    "endDate": "2016-03-02T21:55:33+00:00",
                    "stdout": "MTQ1Njk1NTczMw==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:55:33+00:00",
                    "updatedAt": "2016-03-02T21:55:33+00:00"
                },
                "3c3b45de521d9ccae3243dd595cb08f3": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "3c3b45de521d9ccae3243dd595cb08f3",
                    "startDate": "2016-03-02T21:55:59+00:00",
                    "endDate": "2016-03-02T21:55:59+00:00",
                    "stdout": "MTQ1Njk1NTc1OQ==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T21:55:59+00:00",
                    "updatedAt": "2016-03-02T21:55:59+00:00"
                },
                "938374ff1456bd8ef0900a70900c561b": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "938374ff1456bd8ef0900a70900c561b",
                    "startDate": "2016-03-02T22:18:25+00:00",
                    "endDate": "2016-03-02T22:18:26+00:00",
                    "stdout": "MTQ1Njk1NzEwNg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T22:18:25+00:00",
                    "updatedAt": "2016-03-02T22:18:26+00:00"
                }
            }
        },
        "5fa21b0711b6d2da4bfd932c7d2ef8db": {
            "snippet": {
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
            "executions": {
                "7c853d27e95b547f711a28f3a5d87b5c": {
                    "slave": "fi9CvJ-003",
                    "executionToken": "7c853d27e95b547f711a28f3a5d87b5c",
                    "startDate": "2016-02-27T17:58:35+00:00",
                    "endDate": "2016-02-27T17:58:35+00:00",
                    "stdout": "",
                    "stderr": "dG9wOiBmYWlsZWQgdHR5IGdldAo=",
                    "terminationCode": 1,
                    "status": "COMPLETED",
                    "createdAt": "2016-02-27T17:58:35+00:00",
                    "updatedAt": "2016-02-27T17:58:35+00:00"
                },
                "787cc7aa00e4809fcd303c129cf57330": {
                    "slave": "fi9CvJ-003",
                    "executionToken": "787cc7aa00e4809fcd303c129cf57330",
                    "startDate": "2016-02-27T18:02:36+00:00",
                    "endDate": "2016-02-27T18:02:36+00:00",
                    "stdout": "VVNFUiAgICAgICBQSUQgJUNQVSAlTUVNICAgIFZTWiAgIFJTUyBUVFkgICAgICBTVEFUIFNUQVJUICAgVElNRSBDT01NQU5ECnJvb3QgICAgICAgICAxICAwLjAgIDEuMiAgMzY4MTIgIDYxNTYgPyAgICAgICAgU3MgICBGZWIyNiAgIDA6MDMgL3NiaW4vaW5pdApyb290ICAgICAgICAgMiAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtrdGhyZWFkZF0Kcm9vdCAgICAgICAgIDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBba3NvZnRpcnFkLzBdCnJvb3QgICAgICAgICA1ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2t3b3JrZXIvMDowSF0Kcm9vdCAgICAgICAgIDYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBba3dvcmtlci91MjowXQpyb290ICAgICAgICAgNyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAyIFtyY3Vfc2NoZWRdCnJvb3QgICAgICAgICA4ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDIgW3JjdW9zLzBdCnJvb3QgICAgICAgICA5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDAgW3JjdV9iaF0Kcm9vdCAgICAgICAgMTAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBbcmN1b2IvMF0Kcm9vdCAgICAgICAgMTEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBbbWlncmF0aW9uLzBdCnJvb3QgICAgICAgIDEyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDAgW3dhdGNoZG9nLzBdCnJvb3QgICAgICAgIDEzICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2toZWxwZXJdCnJvb3QgICAgICAgIDE0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDAgW2tkZXZ0bXBmc10Kcm9vdCAgICAgICAgMTUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIEZlYjI2ICAgMDowMCBbbmV0bnNdCnJvb3QgICAgICAgIDE2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW3dyaXRlYmFja10Kcm9vdCAgICAgICAgMTcgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIEZlYjI2ICAgMDowMCBba2ludGVncml0eWRdCnJvb3QgICAgICAgIDE4ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2Jpb3NldF0Kcm9vdCAgICAgICAgMTkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIEZlYjI2ICAgMDowMCBba3dvcmtlci91MzowXQpyb290ICAgICAgICAyMCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgRmViMjYgICAwOjAwIFtrYmxvY2tkXQpyb290ICAgICAgICAyMSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgRmViMjYgICAwOjAwIFthdGFfc2ZmXQpyb290ICAgICAgICAyMiAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtraHViZF0Kcm9vdCAgICAgICAgMjMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIEZlYjI2ICAgMDowMCBbbWRdCnJvb3QgICAgICAgIDI0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2RldmZyZXFfd3FdCnJvb3QgICAgICAgIDI1ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDUgW2t3b3JrZXIvMDoxXQpyb290ICAgICAgICAyNyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtraHVuZ3Rhc2tkXQpyb290ICAgICAgICAyOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtrc3dhcGQwXQpyb290ICAgICAgICAyOSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFNOICAgRmViMjYgICAwOjAwIFtrc21kXQpyb290ICAgICAgICAzMCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtmc25vdGlmeV9tYXJrXQpyb290ICAgICAgICAzMSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtlY3J5cHRmcy1rdGhyZWFdCnJvb3QgICAgICAgIDMyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2NyeXB0b10Kcm9vdCAgICAgICAgNDQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIEZlYjI2ICAgMDowMCBba3Rocm90bGRdCnJvb3QgICAgICAgIDQ1ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDIgW2t3b3JrZXIvdTI6MV0Kcm9vdCAgICAgICAgNDYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBbdmJhbGxvb25dCnJvb3QgICAgICAgIDQ3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICBGZWIyNiAgIDA6MDAgW3Njc2lfZWhfMF0Kcm9vdCAgICAgICAgNDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBbc2NzaV9laF8xXQpyb290ICAgICAgICA2OSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgRmViMjYgICAwOjAwIFtkZWZlcndxXQpyb290ICAgICAgICA3MCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgRmViMjYgICAwOjAwIFtjaGFyZ2VyX21hbmFnZXJdCnJvb3QgICAgICAgMTE1ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2twc21vdXNlZF0Kcm9vdCAgICAgICAxMjMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMiBbamJkMi92ZGExLThdCnJvb3QgICAgICAgMTI0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2V4dDQtcnN2LWNvbnZlcl0Kcm9vdCAgICAgICAxMzggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMDowMCBba3dvcmtlci8wOjJdCnJvb3QgICAgICAgMzEwICAwLjAgIDAuMSAgIDQ0NDAgICA2NTYgPyAgICAgICAgU3MgICBGZWIyNiAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtbWV0cmljcyAgPj4gL3Zhci9sb2cvaDRkL21ldHJpY3MubG9nIC9iaW4vc2gKcm9vdCAgICAgICAzMTEgIDAuMCAgMi44IDIzMjQyMCAxNDA4MCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMTowNSBoNGQtbWV0cmljcyAgICAgICAgICAgICAKcm9vdCAgICAgICA0NTEgIDAuMCAgMC4zICA1MTIzMiAgMTUyMCA\/ICAgICAgICBTcyAgIEZlYjI2ICAgMDowMCAvbGliL3N5c3RlbWQvc3lzdGVtZC11ZGV2ZCAtLWRhZW1vbgpyb290ICAgICAgIDUwNiAgMC4wICAwLjEgICA0NDQwICAgNjUyID8gICAgICAgIFNzICAgRmViMjYgICAwOjAwIC9iaW4vc2ggLWUgLWMgL3Vzci9iaW4vaDRkLXdhdGNoZG9nICA+PiAvdmFyL2xvZy9oNGQvd2F0Y2hkb2cubG9nIC9iaW4vc2gKcm9vdCAgICAgICA1MDcgIDAuMCAgMy4wIDIzNTUxNiAxNTU0MCA\/ICAgICAgICBTICAgIEZlYjI2ICAgMTowOCBoNGQtd2F0Y2hkb2cgICAgICAgICAgICAgCnJvb3QgICAgICAgNjQ0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW3R0bV9zd2FwXQpyb290ICAgICAgIDY5MCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgRmViMjYgICAwOjAwIFtrdm0taXJxZmQtY2xlYW5dCm1lc3NhZ2UrICAgODIzICAwLjAgIDAuMiAgMzkxMTIgIDEwMjggPyAgICAgICAgU3MgICBGZWIyNiAgIDA6MDAgZGJ1cy1kYWVtb24gLS1zeXN0ZW0gLS1mb3JrCnJvb3QgICAgICAgODc4ICAwLjAgIDAuMyAgNDM0NDggIDE4MDAgPyAgICAgICAgU3MgICBGZWIyNiAgIDA6MDAgL2xpYi9zeXN0ZW1kL3N5c3RlbWQtbG9naW5kCnN5c2xvZyAgICAgODgxICAwLjAgIDAuNSAyNTU4NDAgIDI5MzIgPyAgICAgICAgU3NsICBGZWIyNiAgIDA6MDIgcnN5c2xvZ2QKcm9vdCAgICAgICA5NTcgIDAuMCAgMC4xICAxNTgxNiAgIDk2MCB0dHk0ICAgICBTcysgIEZlYjI2ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHk0CnJvb3QgICAgICAgOTYwICAwLjAgIDAuMSAgMTU4MTYgICA5NjAgdHR5NSAgICAgU3MrICBGZWIyNiAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5NQpyb290ICAgICAgIDk2NSAgMC4wICAwLjEgIDE1ODE2ICAgOTU2IHR0eTIgICAgIFNzKyAgRmViMjYgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTIKcm9vdCAgICAgICA5NjYgIDAuMCAgMC4xICAxNTgxNiAgIDk2NCB0dHkzICAgICBTcysgIEZlYjI2ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHkzCnJvb3QgICAgICAgOTY4ICAwLjAgIDAuMSAgMTU4MTYgICA5NjQgdHR5NiAgICAgU3MrICBGZWIyNiAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5Ngpyb290ICAgICAgIDk5MCAgMC4wICAwLjYgIDYxMzcyICAzMDcyID8gICAgICAgIFNzICAgRmViMjYgICAwOjAxIC91c3Ivc2Jpbi9zc2hkIC1ECnJvb3QgICAgICAgOTk1ICAwLjAgIDAuMSAgIDQzNjQgICA2NTYgPyAgICAgICAgU3MgICBGZWIyNiAgIDA6MDAgYWNwaWQgLWMgL2V0Yy9hY3BpL2V2ZW50cyAtcyAvdmFyL3J1bi9hY3BpZC5zb2NrZXQKcm9vdCAgICAgICA5OTYgIDAuMCAgMC4yICAyMzY1MiAgMTA0NCA\/ICAgICAgICBTcyAgIEZlYjI2ICAgMDowMCBjcm9uCmRhZW1vbiAgICAgOTk3ICAwLjAgIDAuMCAgMTkxMzYgICAxNjQgPyAgICAgICAgU3MgICBGZWIyNiAgIDA6MDAgYXRkCnJvb3QgICAgICAxMTM3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICBGZWIyNiAgIDA6MDAgW2t3b3JrZXIvdTM6MV0KbnRwICAgICAgIDExNjcgIDAuMCAgMC40ICAzMTQ0OCAgMjEwNCA\/ICAgICAgICBTcyAgIEZlYjI2ICAgMDowOCAvdXNyL3NiaW4vbnRwZCAtcCAvdmFyL3J1bi9udHBkLnBpZCAtZyAtdSAxMDY6MTE0CnJvb3QgICAgICAxMjM4ICAwLjAgIDAuMSAgMTU4MTYgICA5NDggdHR5MSAgICAgU3MrICBGZWIyNiAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5MQpyb290ICAgICAgMTI5NyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgRmViMjYgICAwOjAwIFtrYXVkaXRkXQpyb290ICAgICAgNDgzNCAgMC4wICAwLjEgIDE5NDcyICAgNjUyID8gICAgICAgIFMgICAgMTc6NTUgICAwOjAwIHVwc3RhcnQtdWRldi1icmlkZ2UgLS1kYWVtb24Kcm9vdCAgICAgIDQ4MzcgIDAuMCAgMC4xICAxNTI1NiAgIDYyOCA\/ICAgICAgICBTICAgIDE3OjU1ICAgMDowMCB1cHN0YXJ0LXNvY2tldC1icmlkZ2UgLS1kYWVtb24Kcm9vdCAgICAgIDQ4NDAgIDAuMCAgMC4xICAxNTI3MiAgIDYyOCA\/ICAgICAgICBTICAgIDE3OjU1ICAgMDowMCB1cHN0YXJ0LWZpbGUtYnJpZGdlIC0tZGFlbW9uCnJvb3QgICAgIDEwOTAyICAwLjAgIDAuMyAgMTc3NzIgIDE1MjAgPyAgICAgICAgU3MgICAxNzo1NiAgIDA6MDAgL3Vzci9zYmluL2RvdmVjb3QgLUYgLWMgL2V0Yy9kb3ZlY290L2RvdmVjb3QuY29uZgpkb3ZlY290ICAxMDkxMyAgMC4wICAwLjEgICA5MjgwICAgOTc2ID8gICAgICAgIFMgICAgMTc6NTYgICAwOjAwIGRvdmVjb3QvYW52aWwKcm9vdCAgICAgMTA5MTQgIDAuMCAgMC4yICAgOTQwOCAgMTE0OCA\/ICAgICAgICBTICAgIDE3OjU2ICAgMDowMCBkb3ZlY290L2xvZwpyb290ICAgICAxMDkxNiAgMC4wICAwLjQgIDE4NzMyICAyMjI0ID8gICAgICAgIFMgICAgMTc6NTYgICAwOjAwIGRvdmVjb3QvY29uZmlnCnJvb3QgICAgIDEwOTE4ICAwLjQgMTIuNyAxMzc0NTIgNjQxNzIgPyAgICAgICAgU3MgICAxNzo1NiAgIDA6MDEgL3Vzci9zYmluL3NwYW1kIC1kIC1tNSAteCAtcSAtUSAtLXVzZXJuYW1lIHNwYW1kIC0taGVscGVyLWhvbWUtZGlyIC92YXIvbG9nL3NwYW1hc3Nhc3Npbi8gLXMgL3Zhci9sb2cvc3BhbWFzc2Fzc2luL3NwYW1kLmxvZyAtZCAtLXBpZGZpbGU9L3Zhci9sb2cvc3BhbWFzc2Fzc2luL3NwYW1kLnBpZApzcGFtZCAgICAxMDkxOSAgMC4wIDEyLjQgMTM3NDUyIDYyNjUyID8gICAgICAgIFMgICAgMTc6NTYgICAwOjAwIHNwYW1kIGNoaWxkCnNwYW1kICAgIDEwOTIxICAwLjAgMTIuNCAxMzc0NTIgNjI2NTIgPyAgICAgICAgUyAgICAxNzo1NiAgIDA6MDAgc3BhbWQgY2hpbGQKcm9vdCAgICAgMTEwMzcgIDAuMCAgMC4zICAyNTM0MCAgMTYwNCA\/ICAgICAgICBTcyAgIDE3OjU2ICAgMDowMCAvdXNyL2xpYi9wb3N0Zml4L21hc3Rlcgpwb3N0Zml4ICAxMTAzOCAgMC4wICAwLjMgIDI3NDA0ICAxNTMyID8gICAgICAgIFMgICAgMTc6NTYgICAwOjAwIHBpY2t1cCAtbCAtdCB1bml4IC11IC1jCnBvc3RmaXggIDExMDM5ICAwLjAgIDAuMyAgMjc0NTYgIDE1NjQgPyAgICAgICAgUyAgICAxNzo1NiAgIDA6MDAgcW1nciAtbCAtdCB1bml4IC11CnJvb3QgICAgIDExMTcxICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgWiAgICAxNzo1OCAgIDA6MDAgW3BocF0gPGRlZnVuY3Q+CnJvb3QgICAgIDExMjYwICAwLjAgIDIuNyAyMzY5ODggMTM4NzYgPyAgICAgICAgUyAgICAxODowMiAgIDA6MDAgaDRkLXJwYy1zZXJ2ZXIgICAgICAgICAgICAgCnJvb3QgICAgIDExMjYyICAwLjAgIDAuMSAgIDQ0NDAgICA2NTIgPyAgICAgICAgUyAgICAxODowMiAgIDA6MDAgc2ggLWMgL3Zhci90bXAvMTQ1NjU5NjE1Ni01ZmEyMWIwNzExYjZkMmRhNGJmZDkzMmM3ZDJlZjhkYgpyb290ICAgICAxMTI2MyAgMC4wICAwLjIgIDE3OTUyICAxNDEyID8gICAgICAgIFMgICAgMTg6MDIgICAwOjAwIC9iaW4vYmFzaCAvdmFyL3RtcC8xNDU2NTk2MTU2LTVmYTIxYjA3MTFiNmQyZGE0YmZkOTMyYzdkMmVmOGRiCnJvb3QgICAgIDExMjY0ICAwLjAgIDAuMiAgMTU1NjQgIDExNTIgPyAgICAgICAgUiAgICAxODowMiAgIDA6MDAgcHMgLWF1eApyb290ICAgICAzMTcwMyAgMC4wICAwLjEgICA0NDQwICAgNjQ4ID8gICAgICAgIFNzICAgMTc6MzggICAwOjAwIC9iaW4vc2ggLWUgLWMgL3Vzci9iaW4vaDRkLXJwYy1zZXJ2ZXIgID4+IC92YXIvbG9nL2g0ZC9ycGMtc2VydmVyLmxvZyAvYmluL3NoCnJvb3QgICAgIDMxNzA0ICAwLjAgIDMuNSAyMzY1ODQgMTc2NDggPyAgICAgICAgUyAgICAxNzozOCAgIDA6MDAgaDRkLXJwYy1zZXJ2ZXIgICAgICAgICAgICAgCnJvb3QgICAgIDMyMDc0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgWiAgICAxNzo1MyAgIDA6MDAgW3BocF0gPGRlZnVuY3Q+Cg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-02-27T18:02:36+00:00",
                    "updatedAt": "2016-02-27T18:02:36+00:00"
                },
                "1b5dfb6ec70ae6d47a21c55ad944bcd6": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "1b5dfb6ec70ae6d47a21c55ad944bcd6",
                    "startDate": "2016-03-02T18:38:52+00:00",
                    "endDate": "2016-03-02T18:38:53+00:00",
                    "stdout": "VVNFUiAgICAgICBQSUQgJUNQVSAlTUVNICAgIFZTWiAgIFJTUyBUVFkgICAgICBTVEFUIFNUQVJUICAgVElNRSBDT01NQU5ECnJvb3QgICAgICAgICAxICAwLjAgIDAuNSAgMzM1ODQgIDI3NjQgPyAgICAgICAgU3MgICAxNzozMSAgIDA6MDAgL3NiaW4vaW5pdApyb290ICAgICAgICAgMiAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzEgICAwOjAwIFtrdGhyZWFkZF0Kcm9vdCAgICAgICAgIDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMCBba3NvZnRpcnFkLzBdCnJvb3QgICAgICAgICA0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2t3b3JrZXIvMDowXQpyb290ICAgICAgICAgNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtrd29ya2VyLzA6MEhdCnJvb3QgICAgICAgICA3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDIgW3JjdV9zY2hlZF0Kcm9vdCAgICAgICAgIDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMiBbcmN1b3MvMF0Kcm9vdCAgICAgICAgIDkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMCBbcmN1X2JoXQpyb290ICAgICAgICAxMCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzEgICAwOjAwIFtyY3VvYi8wXQpyb290ICAgICAgICAxMSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzEgICAwOjAwIFttaWdyYXRpb24vMF0Kcm9vdCAgICAgICAgMTIgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMCBbd2F0Y2hkb2cvMF0Kcm9vdCAgICAgICAgMTMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBba2hlbHBlcl0Kcm9vdCAgICAgICAgMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMCBba2RldnRtcGZzXQpyb290ICAgICAgICAxNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtuZXRuc10Kcm9vdCAgICAgICAgMTYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBbd3JpdGViYWNrXQpyb290ICAgICAgICAxNyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtraW50ZWdyaXR5ZF0Kcm9vdCAgICAgICAgMTggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBbYmlvc2V0XQpyb290ICAgICAgICAxOSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtrd29ya2VyL3UzOjBdCnJvb3QgICAgICAgIDIwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozMSAgIDA6MDAgW2tibG9ja2RdCnJvb3QgICAgICAgIDIxICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozMSAgIDA6MDAgW2F0YV9zZmZdCnJvb3QgICAgICAgIDIyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2todWJkXQpyb290ICAgICAgICAyMyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFttZF0Kcm9vdCAgICAgICAgMjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBbZGV2ZnJlcV93cV0Kcm9vdCAgICAgICAgMjUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMCBba3dvcmtlci8wOjFdCnJvb3QgICAgICAgIDI2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2todW5ndGFza2RdCnJvb3QgICAgICAgIDI3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2tzd2FwZDBdCnJvb3QgICAgICAgIDI4ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgU04gICAxNzozMSAgIDA6MDAgW2tzbWRdCnJvb3QgICAgICAgIDI5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2Zzbm90aWZ5X21hcmtdCnJvb3QgICAgICAgIDMwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2VjcnlwdGZzLWt0aHJlYV0Kcm9vdCAgICAgICAgMzEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBbY3J5cHRvXQpyb290ICAgICAgICA0MyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtrdGhyb3RsZF0Kcm9vdCAgICAgICAgNjMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBbZGVmZXJ3cV0Kcm9vdCAgICAgICAgNjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMxICAgMDowMCBbY2hhcmdlcl9tYW5hZ2VyXQpyb290ICAgICAgIDEwNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzEgICAwOjAwIFtzY3NpX2VoXzBdCnJvb3QgICAgICAgMTA2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozMSAgIDA6MDAgW2twc21vdXNlZF0Kcm9vdCAgICAgICAxMDcgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjMxICAgMDowMCBba3dvcmtlci91MjoyXQpyb290ICAgICAgIDEwOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzEgICAwOjAwIFtrd29ya2VyL3UyOjNdCnJvb3QgICAgICAgMTUzICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgW2piZDIvc2RhMS04XQpyb290ICAgICAgIDE1NCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtleHQ0LXJzdi1jb252ZXJdCnJvb3QgICAgICAgMzUzICAwLjAgIDAuMSAgMTk0NzIgICA1NDAgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgdXBzdGFydC11ZGV2LWJyaWRnZSAtLWRhZW1vbgpyb290ICAgICAgIDM1OCAgMC4wICAwLjIgIDQ5NjAwICAxMjU2ID8gICAgICAgIFNzICAgMTc6MzEgICAwOjAwIC9saWIvc3lzdGVtZC9zeXN0ZW1kLXVkZXZkIC0tZGFlbW9uCnJvb3QgICAgICAgMzg5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozMSAgIDA6MDAgW2lwcnRdCnJvb3QgICAgICAgNTA4ICAwLjAgIDAuMSAgMjM0MTYgICA5NDQgPyAgICAgICAgU3MgICAxNzozMSAgIDA6MDAgcnBjYmluZApzdGF0ZCAgICAgIDUyNSAgMC4wICAwLjIgIDIxNTQwICAxMTY0ID8gICAgICAgIFNzICAgMTc6MzEgICAwOjAwIHJwYy5zdGF0ZCAtTApyb290ICAgICAgIDUyOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzEgICAwOjAwIFtrd29ya2VyL3UzOjFdCnJvb3QgICAgICAgNTM5ICAwLjAgIDAuMSAgMTUyNTYgICA1NzIgPyAgICAgICAgUyAgICAxNzozMSAgIDA6MDAgdXBzdGFydC1zb2NrZXQtYnJpZGdlIC0tZGFlbW9uCnJvb3QgICAgICAgODEwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozMiAgIDA6MDAgW3JwY2lvZF0Kcm9vdCAgICAgICA4MjYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjMyICAgMDowMCBbbmZzaW9kXQptZXNzYWdlKyAgIDg0MiAgMC4wICAwLjIgIDM5MjEyICAxMDgwID8gICAgICAgIFNzICAgMTc6MzIgICAwOjAwIGRidXMtZGFlbW9uIC0tc3lzdGVtIC0tZm9yawpyb290ICAgICAgIDg2NSAgMC4wICAwLjAgIDI1NTQwICAgMzEyID8gICAgICAgIFNzICAgMTc6MzIgICAwOjAwIHJwYy5pZG1hcGQKcm9vdCAgICAgICA4OTAgIDAuMCAgMC4zICA0MzQ0OCAgMTU3MiA\/ICAgICAgICBTcyAgIDE3OjMyICAgMDowMCAvbGliL3N5c3RlbWQvc3lzdGVtZC1sb2dpbmQKc3lzbG9nICAgICA5MjIgIDAuMCAgMC4yIDI1NzkwOCAgMTI0NCA\/ICAgICAgICBTc2wgIDE3OjMyICAgMDowMCByc3lzbG9nZApyb290ICAgICAgIDk1OCAgMC4wICAwLjEgIDE1Mzk2ICAgNTY0ID8gICAgICAgIFMgICAgMTc6MzIgICAwOjAwIHVwc3RhcnQtZmlsZS1icmlkZ2UgLS1kYWVtb24Kcm9vdCAgICAgIDEwMTggIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHk0ICAgICBTcysgIDE3OjMyICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHk0CnJvb3QgICAgICAxMDIxICAwLjAgIDAuMSAgMTQ1MzYgICA4NzIgdHR5NSAgICAgU3MrICAxNzozMiAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5NQpyb290ICAgICAgMTAyNiAgMC4wICAwLjEgIDE0NTM2ICAgODY0IHR0eTIgICAgIFNzKyAgMTc6MzIgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTIKcm9vdCAgICAgIDEwMjcgIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHkzICAgICBTcysgIDE3OjMyICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHkzCnJvb3QgICAgICAxMDI5ICAwLjAgIDAuMSAgMTQ1MzYgICA4NjggdHR5NiAgICAgU3MrICAxNzozMiAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5Ngpyb290ICAgICAgMTA2NyAgMC4wICAwLjEgICA0MzY0ICAgNjIwID8gICAgICAgIFNzICAgMTc6MzIgICAwOjAwIGFjcGlkIC1jIC9ldGMvYWNwaS9ldmVudHMgLXMgL3Zhci9ydW4vYWNwaWQuc29ja2V0CnJvb3QgICAgICAxMDY4ICAwLjAgIDAuMSAgMjM2NTIgICA5ODggPyAgICAgICAgU3MgICAxNzozMiAgIDA6MDAgY3JvbgpkYWVtb24gICAgMTA2OSAgMC4wICAwLjAgIDE5MTM2ICAgMTYwID8gICAgICAgIFNzICAgMTc6MzIgICAwOjAwIGF0ZApyb290ICAgICAgMTA5OSAgMC4wICAwLjEgMjE2NjA4ICAgOTMyID8gICAgICAgIFNsICAgMTc6MzIgICAwOjAxIC91c3Ivc2Jpbi9WQm94U2VydmljZQpyb290ICAgICAgMTI1MCAgMC4wICA2LjcgMTgyNTM2IDMzNzg0ID8gICAgICAgIFNzbCAgMTc6MzIgICAwOjAwIC91c3IvYmluL3J1YnkgL3Vzci9iaW4vcHVwcGV0IGFnZW50CnJvb3QgICAgICAxMjgyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozMiAgIDA6MDAgW2thdWRpdGRdCnJvb3QgICAgICAxMzIwICAwLjAgIDYuOCAxMTI2ODggMzQ0NzIgPyAgICAgICAgU2wgICAxNzozMiAgIDA6MDAgcnVieSAvdXNyL2Jpbi9jaGVmLWNsaWVudCAtZCAtUCAvdmFyL3J1bi9jaGVmL2NsaWVudC5waWQgLWMgL2V0Yy9jaGVmL2NsaWVudC5yYiAtaSAxODAwIC1zIDIwIC1MIC92YXIvbG9nL2NoZWYvY2xpZW50LmxvZwpyb290ICAgICAgMTM2NiAgMC4wICAwLjEgIDE0NTM2ICAgODY4IHR0eTEgICAgIFNzKyAgMTc6MzIgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTEKcm9vdCAgICAgIDE4NzQgIDAuMCAgMC40ICAxMDIyMCAgMjI5NiA\/ICAgICAgICBTcyAgIDE3OjMyICAgMDowMCBkaGNsaWVudCAtMSAtdiAtcGYgL3J1bi9kaGNsaWVudC5ldGgwLnBpZCAtbGYgL3Zhci9saWIvZGhjcC9kaGNsaWVudC5ldGgwLmxlYXNlcyBldGgwCnJvb3QgICAgICAxOTQ4ICAwLjAgIDAuNCAgNjEzNjAgIDIzMDAgPyAgICAgICAgU3MgICAxNzozMiAgIDA6MDAgL3Vzci9zYmluL3NzaGQgLUQKcm9vdCAgICAgIDIxNzUgIDAuMCAgMC42IDEwNzY5MiAgMzM1MiA\/ICAgICAgICBTcyAgIDE3OjMyICAgMDowMCBzc2hkOiB2YWdyYW50IFtwcml2XQp2YWdyYW50ICAgMjIyOCAgMC4wICAwLjQgMTA3NjkyICAyMDg0ID8gICAgICAgIFMgICAgMTc6MzIgICAwOjAwIHNzaGQ6IHZhZ3JhbnRAcHRzLzAgCnZhZ3JhbnQgICAyMjI5ICAwLjAgIDAuNyAgMjE0MDQgIDM2NDQgcHRzLzAgICAgU3MgICAxNzozMiAgIDA6MDAgLWJhc2gKcm9vdCAgICAgIDIyNDUgIDAuMCAgMC4zICA2MzI0OCAgMTYyMCBwdHMvMCAgICBTICAgIDE3OjMyICAgMDowMCBzdSAtbApyb290ICAgICAgMjI1MCAgMC4wICAwLjcgIDIxMzI0ICAzNzMyIHB0cy8wICAgIFMrICAgMTc6MzIgICAwOjAwIC1zdQpudHAgICAgICAgMzA5OSAgMC4wICAwLjMgIDMzNTA0ICAxODk2ID8gICAgICAgIFNzICAgMTc6MzQgICAwOjAwIC91c3Ivc2Jpbi9udHBkIC1wIC92YXIvcnVuL250cGQucGlkIC1nIC11IDEwODoxMTMKcm9vdCAgICAgIDQ0MzAgIDAuMCAgMC44IDEwNzY5MiAgNDIyNCA\/ICAgICAgICBTcyAgIDE4OjMwICAgMDowMCBzc2hkOiB2YWdyYW50IFtwcml2XQp2YWdyYW50ICAgNDU0NiAgMC4wICAwLjQgMTA3NjkyICAyMTg0ID8gICAgICAgIFMgICAgMTg6MzAgICAwOjAwIHNzaGQ6IHZhZ3JhbnRAcHRzLzIgCnZhZ3JhbnQgICA0NTQ5ICAwLjAgIDAuNyAgMjE0MDAgIDM5NDAgcHRzLzIgICAgU3MgICAxODozMCAgIDA6MDAgLWJhc2gKcm9vdCAgICAgIDQ3ODEgIDAuMCAgMC4xICAgNDQ0MCAgIDY0NCA\/ICAgICAgICBTcyAgIDE3OjM0ICAgMDowMCAvYmluL3NoIC1lIC1jIC91c3IvYmluL2g0ZC13YXRjaGRvZyAgPj4gL3Zhci9sb2cvaDRkL3dhdGNoZG9nLmxvZyAvYmluL3NoCnJvb3QgICAgICA0NzgyICAwLjEgIDIuNSAyMzc0NTIgMTI4OTIgPyAgICAgICAgUyAgICAxNzozNCAgIDA6MDUgaDRkLXdhdGNoZG9nICAgICAgICAgICAgIApyb290ICAgICAgNDc5MCAgMC4wICAwLjEgICA0NDQwICAgNjQ4ID8gICAgICAgIFNzICAgMTc6MzQgICAwOjAwIC9iaW4vc2ggLWUgLWMgL3Vzci9iaW4vaDRkLW1ldHJpY3MgID4+IC92YXIvbG9nL2g0ZC9tZXRyaWNzLmxvZyAvYmluL3NoCnJvb3QgICAgICA0NzkxICAwLjEgIDIuMiAyMzI0MDAgMTE0MDggPyAgICAgICAgUyAgICAxNzozNCAgIDA6MDUgaDRkLW1ldHJpY3MgICAgICAgICAgICAgCnJvb3QgICAgICA1ODc5ICAwLjAgIDAuNiAgOTEyMTIgIDMyNDQgPyAgICAgICAgU3MgICAxNzozNSAgIDA6MDAgL3Vzci9zYmluL2FwYWNoZTIgLWsgc3RhcnQKd3d3LWRhdGEgIDU4ODIgIDAuMCAgMC41IDM4MDM4NCAgMjY1MiA\/ICAgICAgICBTbCAgIDE3OjM1ICAgMDowMSAvdXNyL3NiaW4vYXBhY2hlMiAtayBzdGFydAp3d3ctZGF0YSAgNTg4MyAgMC4wICAwLjUgMzgwMzg0ICAyNjUyID8gICAgICAgIFNsICAgMTc6MzUgICAwOjAxIC91c3Ivc2Jpbi9hcGFjaGUyIC1rIHN0YXJ0CnJvb3QgICAgIDMwMjczICAwLjAgIDAuMyAgNjMyNDggIDE4MzIgcHRzLzIgICAgUyAgICAxODozNiAgIDA6MDAgc3UgLWwKcm9vdCAgICAgMzAyNzQgIDAuMCAgMC43ICAyMTMyOCAgMzk0MCBwdHMvMiAgICBTKyAgIDE4OjM2ICAgMDowMCAtc3UKcm9vdCAgICAgMzAzNjIgIDAuMCAgMC4xICAgNDQ0MCAgIDY0NCA\/ICAgICAgICBTcyAgIDE4OjM4ICAgMDowMCAvYmluL3NoIC1lIC1jIC91c3IvYmluL2g0ZC1ycGMtc2VydmVyICA+PiAvdmFyL2xvZy9oNGQvcnBjLXNlcnZlci5sb2cgL2Jpbi9zaApyb290ICAgICAzMDM2MyAgMC4zICAzLjQgMjM4MzY0IDE3MjEyID8gICAgICAgIFMgICAgMTg6MzggICAwOjAwIGg0ZC1ycGMtc2VydmVyICAgICAgICAgICAgIApyb290ICAgICAzMDQyNCAgMi4wICAyLjYgMjM4ODEyIDEzNTEyID8gICAgICAgIFMgICAgMTg6MzggICAwOjAwIGg0ZC1ycGMtc2VydmVyICAgICAgICAgICAgIApyb290ICAgICAzMDQyNiAgMi4wICAyLjMgMjM3ODIwIDExODQ4ID8gICAgICAgIFMgICAgMTg6MzggICAwOjAwIGg0ZC1tZXRyaWNzICAgICAgICAgICAgIApyb290ICAgICAzMDQ0NiAgMC4wICAwLjEgICA0NDQwICAgNjQ0ID8gICAgICAgIFMgICAgMTg6MzkgICAwOjAwIHNoIC1jIC92YXIvdG1wLzE0NTY5NDM5MzktNWZhMjFiMDcxMWI2ZDJkYTRiZmQ5MzJjN2QyZWY4ZGIKcm9vdCAgICAgMzA0NDcgIDAuMCAgMC4yICAxNzk1NiAgMTQwOCA\/ICAgICAgICBTICAgIDE4OjM5ICAgMDowMCAvYmluL2Jhc2ggL3Zhci90bXAvMTQ1Njk0MzkzOS01ZmEyMWIwNzExYjZkMmRhNGJmZDkzMmM3ZDJlZjhkYgpyb290ICAgICAzMDQ0OCAgMC4wICAwLjIgIDE1NTY0ICAxMTY0ID8gICAgICAgIFIgICAgMTg6MzkgICAwOjAwIHBzIC1hdXgK",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T18:38:52+00:00",
                    "updatedAt": "2016-03-02T18:38:53+00:00"
                },
                "8b5d73eb916af90efb5c0878c0a19709": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "8b5d73eb916af90efb5c0878c0a19709",
                    "startDate": "2016-03-02T20:17:39+00:00",
                    "endDate": "2016-03-02T20:17:40+00:00",
                    "stdout": "VVNFUiAgICAgICBQSUQgJUNQVSAlTUVNICAgIFZTWiAgIFJTUyBUVFkgICAgICBTVEFUIFNUQVJUICAgVElNRSBDT01NQU5ECnJvb3QgICAgICAgICAxICAwLjAgIDAuNSAgMzM1ODQgIDI3NjQgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgL3NiaW4vaW5pdApyb290ICAgICAgICAgMiAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtrdGhyZWFkZF0Kcm9vdCAgICAgICAgIDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba3NvZnRpcnFkLzBdCnJvb3QgICAgICAgICA0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2t3b3JrZXIvMDowXQpyb290ICAgICAgICAgNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyLzA6MEhdCnJvb3QgICAgICAgICA3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDIgW3JjdV9zY2hlZF0Kcm9vdCAgICAgICAgIDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMiBbcmN1b3MvMF0Kcm9vdCAgICAgICAgIDkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBbcmN1X2JoXQpyb290ICAgICAgICAxMCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtyY3VvYi8wXQpyb290ICAgICAgICAxMSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFttaWdyYXRpb24vMF0Kcm9vdCAgICAgICAgMTIgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBbd2F0Y2hkb2cvMF0Kcm9vdCAgICAgICAgMTMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBba2hlbHBlcl0Kcm9vdCAgICAgICAgMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba2RldnRtcGZzXQpyb290ICAgICAgICAxNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtuZXRuc10Kcm9vdCAgICAgICAgMTYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbd3JpdGViYWNrXQpyb290ICAgICAgICAxNyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtraW50ZWdyaXR5ZF0Kcm9vdCAgICAgICAgMTggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbYmlvc2V0XQpyb290ICAgICAgICAxOSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UzOjBdCnJvb3QgICAgICAgIDIwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2tibG9ja2RdCnJvb3QgICAgICAgIDIxICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2F0YV9zZmZdCnJvb3QgICAgICAgIDIyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2todWJkXQpyb290ICAgICAgICAyMyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFttZF0Kcm9vdCAgICAgICAgMjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbZGV2ZnJlcV93cV0Kcm9vdCAgICAgICAgMjUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMiBba3dvcmtlci8wOjFdCnJvb3QgICAgICAgIDI2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2todW5ndGFza2RdCnJvb3QgICAgICAgIDI3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2tzd2FwZDBdCnJvb3QgICAgICAgIDI4ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgU04gICAxNzozOSAgIDA6MDAgW2tzbWRdCnJvb3QgICAgICAgIDI5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2Zzbm90aWZ5X21hcmtdCnJvb3QgICAgICAgIDMwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2VjcnlwdGZzLWt0aHJlYV0Kcm9vdCAgICAgICAgMzEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbY3J5cHRvXQpyb290ICAgICAgICA0MyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrdGhyb3RsZF0Kcm9vdCAgICAgICAgNjMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbZGVmZXJ3cV0Kcm9vdCAgICAgICAgNjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbY2hhcmdlcl9tYW5hZ2VyXQpyb290ICAgICAgIDEwNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtzY3NpX2VoXzBdCnJvb3QgICAgICAgMTA2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2twc21vdXNlZF0Kcm9vdCAgICAgICAxMDcgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba3dvcmtlci91MjoyXQpyb290ICAgICAgIDEwOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UyOjNdCnJvb3QgICAgICAgMTUzICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2piZDIvc2RhMS04XQpyb290ICAgICAgIDE1NCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtleHQ0LXJzdi1jb252ZXJdCnJvb3QgICAgICAgMzUzICAwLjAgIDAuMSAgMTk0NzIgICA1NDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgdXBzdGFydC11ZGV2LWJyaWRnZSAtLWRhZW1vbgpyb290ICAgICAgIDM1OCAgMC4wICAwLjIgIDQ5NjAwICAxMjU2ID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIC9saWIvc3lzdGVtZC9zeXN0ZW1kLXVkZXZkIC0tZGFlbW9uCnJvb3QgICAgICAgMzg5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2lwcnRdCnJvb3QgICAgICAgNTA4ICAwLjAgIDAuMSAgMjM0MTYgICA5NDQgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgcnBjYmluZApzdGF0ZCAgICAgIDUyNSAgMC4wICAwLjIgIDIxNTQwICAxMTY0ID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIHJwYy5zdGF0ZCAtTApyb290ICAgICAgIDUyOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UzOjFdCnJvb3QgICAgICAgNTM5ICAwLjAgIDAuMSAgMTUyNTYgICA1NzIgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgdXBzdGFydC1zb2NrZXQtYnJpZGdlIC0tZGFlbW9uCnJvb3QgICAgICAgODEwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW3JwY2lvZF0Kcm9vdCAgICAgICA4MjYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbbmZzaW9kXQptZXNzYWdlKyAgIDg0MiAgMC4wICAwLjIgIDM5MjEyICAxMDgwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGRidXMtZGFlbW9uIC0tc3lzdGVtIC0tZm9yawpyb290ICAgICAgIDg2NSAgMC4wICAwLjAgIDI1NTQwICAgMzEyID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIHJwYy5pZG1hcGQKcm9vdCAgICAgICA4OTAgIDAuMCAgMC4zICA0MzQ0OCAgMTU3MiA\/ICAgICAgICBTcyAgIDE3OjM5ICAgMDowMCAvbGliL3N5c3RlbWQvc3lzdGVtZC1sb2dpbmQKc3lzbG9nICAgICA5MjIgIDAuMCAgMC4yIDI1NzkwOCAgMTI0NCA\/ICAgICAgICBTc2wgIDE3OjM5ICAgMDowMCByc3lzbG9nZApyb290ICAgICAgIDk1OCAgMC4wICAwLjEgIDE1Mzk2ICAgNTY0ID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIHVwc3RhcnQtZmlsZS1icmlkZ2UgLS1kYWVtb24Kcm9vdCAgICAgIDEwMTggIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHk0ICAgICBTcysgIDE3OjM5ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHk0CnJvb3QgICAgICAxMDIxICAwLjAgIDAuMSAgMTQ1MzYgICA4NzIgdHR5NSAgICAgU3MrICAxNzozOSAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5NQpyb290ICAgICAgMTAyNiAgMC4wICAwLjEgIDE0NTM2ICAgODY0IHR0eTIgICAgIFNzKyAgMTc6MzkgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTIKcm9vdCAgICAgIDEwMjcgIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHkzICAgICBTcysgIDE3OjM5ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHkzCnJvb3QgICAgICAxMDI5ICAwLjAgIDAuMSAgMTQ1MzYgICA4NjggdHR5NiAgICAgU3MrICAxNzozOSAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5Ngpyb290ICAgICAgMTA2NyAgMC4wICAwLjEgICA0MzY0ICAgNjIwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGFjcGlkIC1jIC9ldGMvYWNwaS9ldmVudHMgLXMgL3Zhci9ydW4vYWNwaWQuc29ja2V0CnJvb3QgICAgICAxMDY4ICAwLjAgIDAuMSAgMjM2NTIgICA5OTIgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgY3JvbgpkYWVtb24gICAgMTA2OSAgMC4wICAwLjAgIDE5MTM2ICAgMTYwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGF0ZApyb290ICAgICAgMTA5OSAgMC4wICAwLjEgMjE2NjA4ICAgOTMyID8gICAgICAgIFNsICAgMTc6MzkgICAwOjAyIC91c3Ivc2Jpbi9WQm94U2VydmljZQpyb290ICAgICAgMTI1MCAgMC4wICA2LjcgMTgyNTM2IDMzNzg0ID8gICAgICAgIFNzbCAgMTc6MzkgICAwOjAwIC91c3IvYmluL3J1YnkgL3Vzci9iaW4vcHVwcGV0IGFnZW50CnJvb3QgICAgICAxMjgyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2thdWRpdGRdCnJvb3QgICAgICAxMzIwICAwLjAgIDYuOCAxMTI2ODggMzQ0NzIgPyAgICAgICAgU2wgICAxNzozOSAgIDA6MDAgcnVieSAvdXNyL2Jpbi9jaGVmLWNsaWVudCAtZCAtUCAvdmFyL3J1bi9jaGVmL2NsaWVudC5waWQgLWMgL2V0Yy9jaGVmL2NsaWVudC5yYiAtaSAxODAwIC1zIDIwIC1MIC92YXIvbG9nL2NoZWYvY2xpZW50LmxvZwpyb290ICAgICAgMTM2NiAgMC4wICAwLjEgIDE0NTM2ICAgODY4IHR0eTEgICAgIFNzKyAgMTc6MzkgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTEKcm9vdCAgICAgIDE4NzQgIDAuMCAgMC40ICAxMDIyMCAgMjI5NiA\/ICAgICAgICBTcyAgIDE3OjM5ICAgMDowMCBkaGNsaWVudCAtMSAtdiAtcGYgL3J1bi9kaGNsaWVudC5ldGgwLnBpZCAtbGYgL3Zhci9saWIvZGhjcC9kaGNsaWVudC5ldGgwLmxlYXNlcyBldGgwCnJvb3QgICAgICAxOTQ4ICAwLjAgIDAuNCAgNjEzNjAgIDIzMDAgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgL3Vzci9zYmluL3NzaGQgLUQKbnRwICAgICAgIDMwOTkgIDAuMCAgMC4zICAzMzUwNCAgMTkwMCA\/ICAgICAgICBTcyAgIDE3OjQxICAgMDowMCAvdXNyL3NiaW4vbnRwZCAtcCAvdmFyL3J1bi9udHBkLnBpZCAtZyAtdSAxMDg6MTEzCnJvb3QgICAgICA0NDMwICAwLjAgIDAuOCAxMDc2OTIgIDQyMjQgPyAgICAgICAgU3MgICAxODozOCAgIDA6MDAgc3NoZDogdmFncmFudCBbcHJpdl0KdmFncmFudCAgIDQ1NDYgIDAuMCAgMC40IDEwNzY5MiAgMjE4NCA\/ICAgICAgICBTICAgIDE4OjM4ICAgMDowMCBzc2hkOiB2YWdyYW50QHB0cy8yIAp2YWdyYW50ICAgNDU0OSAgMC4wICAwLjcgIDIxNDAwICAzOTQwIHB0cy8yICAgIFNzICAgMTg6MzggICAwOjAwIC1iYXNoCnJvb3QgICAgICA0NzgxICAwLjAgIDAuMSAgIDQ0NDAgICA2NDQgPyAgICAgICAgU3MgICAxNzo0MSAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtd2F0Y2hkb2cgID4+IC92YXIvbG9nL2g0ZC93YXRjaGRvZy5sb2cgL2Jpbi9zaApyb290ICAgICAgNDc4MiAgMC4xICAyLjUgMjM3NDUyIDEyODkyID8gICAgICAgIFMgICAgMTc6NDEgICAwOjA5IGg0ZC13YXRjaGRvZyAgICAgICAgICAgICAKcm9vdCAgICAgIDQ3OTAgIDAuMCAgMC4xICAgNDQ0MCAgIDY0OCA\/ICAgICAgICBTcyAgIDE3OjQxICAgMDowMCAvYmluL3NoIC1lIC1jIC91c3IvYmluL2g0ZC1tZXRyaWNzICA+PiAvdmFyL2xvZy9oNGQvbWV0cmljcy5sb2cgL2Jpbi9zaApyb290ICAgICAgNDc5MSAgMC4xICAyLjIgMjMyNDAwIDExNDA4ID8gICAgICAgIFMgICAgMTc6NDEgICAwOjA4IGg0ZC1tZXRyaWNzICAgICAgICAgICAgIApyb290ICAgICAgNTg3OSAgMC4wICAwLjYgIDkxMjEyICAzMjQ0ID8gICAgICAgIFNzICAgMTc6NDMgICAwOjAwIC91c3Ivc2Jpbi9hcGFjaGUyIC1rIHN0YXJ0Cnd3dy1kYXRhICA1ODgyICAwLjAgIDAuNSAzODAzODQgIDI2NTIgPyAgICAgICAgU2wgICAxNzo0MyAgIDA6MDIgL3Vzci9zYmluL2FwYWNoZTIgLWsgc3RhcnQKd3d3LWRhdGEgIDU4ODMgIDAuMCAgMC41IDM4MDM4NCAgMjY1MiA\/ICAgICAgICBTbCAgIDE3OjQzICAgMDowMiAvdXNyL3NiaW4vYXBhY2hlMiAtayBzdGFydApyb290ICAgICAzMDI3MyAgMC4wICAwLjMgIDYzMjQ4ICAxODMyIHB0cy8yICAgIFMgICAgMTg6NDQgICAwOjAwIHN1IC1sCnJvb3QgICAgIDMwMjc0ICAwLjAgIDAuNyAgMjEzMzYgIDM5NDggcHRzLzIgICAgUysgICAxODo0NCAgIDA6MDAgLXN1CnJvb3QgICAgIDMwMzYyICAwLjAgIDAuMSAgIDQ0NDAgICA2NDQgPyAgICAgICAgU3MgICAxODo0NiAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtcnBjLXNlcnZlciAgPj4gL3Zhci9sb2cvaDRkL3JwYy1zZXJ2ZXIubG9nIC9iaW4vc2gKcm9vdCAgICAgMzAzNjMgIDAuMCAgMy40IDIzODM2NCAxNzIyOCA\/ICAgICAgICBTICAgIDE4OjQ2ICAgMDowMCBoNGQtcnBjLXNlcnZlciAgICAgICAgICAgICAKcm9vdCAgICAgMzA0MjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ2ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1MDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ5ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1MjggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ5ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1OTkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjUzICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExMDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExNDAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2NzQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2ODAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2ODUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE3MTEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM2ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzI2MzUgIDAuMSAgMi42IDIzODgwMCAxMzUyMCA\/ICAgICAgICBTICAgIDIwOjA1ICAgMDowMCBoNGQtcnBjLXNlcnZlciAgICAgICAgICAgICAKcm9vdCAgICAgMzI2MzcgIDAuMCAgMC4xICAgNDQ0MCAgIDY0NCA\/ICAgICAgICBTICAgIDIwOjA1ICAgMDowMCBzaCAtYyAvdmFyL3RtcC8xNDU2OTQ5MTQzLTVmYTIxYjA3MTFiNmQyZGE0YmZkOTMyYzdkMmVmOGRiCnJvb3QgICAgIDMyNjM4ICAwLjAgIDAuMiAgMTc5NTYgIDE0MTYgPyAgICAgICAgUyAgICAyMDowNSAgIDA6MDAgL2Jpbi9iYXNoIC92YXIvdG1wLzE0NTY5NDkxNDMtNWZhMjFiMDcxMWI2ZDJkYTRiZmQ5MzJjN2QyZWY4ZGIKcm9vdCAgICAgMzI2MzkgIDAuMCAgMC4yICAxNTU2NCAgMTE2MCA\/ICAgICAgICBSICAgIDIwOjA1ICAgMDowMCBwcyAtYXV4Cg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T20:17:39+00:00",
                    "updatedAt": "2016-03-02T20:17:40+00:00"
                },
                "04d79dae519f17b62444647dd8f969ef": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "04d79dae519f17b62444647dd8f969ef",
                    "startDate": "2016-03-02T20:17:47+00:00",
                    "endDate": "2016-03-02T20:17:48+00:00",
                    "stdout": "VVNFUiAgICAgICBQSUQgJUNQVSAlTUVNICAgIFZTWiAgIFJTUyBUVFkgICAgICBTVEFUIFNUQVJUICAgVElNRSBDT01NQU5ECnJvb3QgICAgICAgICAxICAwLjAgIDAuNSAgMzM1ODQgIDI3NjQgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgL3NiaW4vaW5pdApyb290ICAgICAgICAgMiAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtrdGhyZWFkZF0Kcm9vdCAgICAgICAgIDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba3NvZnRpcnFkLzBdCnJvb3QgICAgICAgICA0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2t3b3JrZXIvMDowXQpyb290ICAgICAgICAgNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyLzA6MEhdCnJvb3QgICAgICAgICA3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDIgW3JjdV9zY2hlZF0Kcm9vdCAgICAgICAgIDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMiBbcmN1b3MvMF0Kcm9vdCAgICAgICAgIDkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBbcmN1X2JoXQpyb290ICAgICAgICAxMCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtyY3VvYi8wXQpyb290ICAgICAgICAxMSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFttaWdyYXRpb24vMF0Kcm9vdCAgICAgICAgMTIgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBbd2F0Y2hkb2cvMF0Kcm9vdCAgICAgICAgMTMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBba2hlbHBlcl0Kcm9vdCAgICAgICAgMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba2RldnRtcGZzXQpyb290ICAgICAgICAxNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtuZXRuc10Kcm9vdCAgICAgICAgMTYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbd3JpdGViYWNrXQpyb290ICAgICAgICAxNyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtraW50ZWdyaXR5ZF0Kcm9vdCAgICAgICAgMTggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbYmlvc2V0XQpyb290ICAgICAgICAxOSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UzOjBdCnJvb3QgICAgICAgIDIwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2tibG9ja2RdCnJvb3QgICAgICAgIDIxICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2F0YV9zZmZdCnJvb3QgICAgICAgIDIyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2todWJkXQpyb290ICAgICAgICAyMyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFttZF0Kcm9vdCAgICAgICAgMjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbZGV2ZnJlcV93cV0Kcm9vdCAgICAgICAgMjUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMiBba3dvcmtlci8wOjFdCnJvb3QgICAgICAgIDI2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2todW5ndGFza2RdCnJvb3QgICAgICAgIDI3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2tzd2FwZDBdCnJvb3QgICAgICAgIDI4ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgU04gICAxNzozOSAgIDA6MDAgW2tzbWRdCnJvb3QgICAgICAgIDI5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2Zzbm90aWZ5X21hcmtdCnJvb3QgICAgICAgIDMwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2VjcnlwdGZzLWt0aHJlYV0Kcm9vdCAgICAgICAgMzEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbY3J5cHRvXQpyb290ICAgICAgICA0MyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrdGhyb3RsZF0Kcm9vdCAgICAgICAgNjMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbZGVmZXJ3cV0Kcm9vdCAgICAgICAgNjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbY2hhcmdlcl9tYW5hZ2VyXQpyb290ICAgICAgIDEwNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtzY3NpX2VoXzBdCnJvb3QgICAgICAgMTA2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2twc21vdXNlZF0Kcm9vdCAgICAgICAxMDcgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba3dvcmtlci91MjoyXQpyb290ICAgICAgIDEwOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UyOjNdCnJvb3QgICAgICAgMTUzICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2piZDIvc2RhMS04XQpyb290ICAgICAgIDE1NCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtleHQ0LXJzdi1jb252ZXJdCnJvb3QgICAgICAgMzUzICAwLjAgIDAuMSAgMTk0NzIgICA1NDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgdXBzdGFydC11ZGV2LWJyaWRnZSAtLWRhZW1vbgpyb290ICAgICAgIDM1OCAgMC4wICAwLjIgIDQ5NjAwICAxMjU2ID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIC9saWIvc3lzdGVtZC9zeXN0ZW1kLXVkZXZkIC0tZGFlbW9uCnJvb3QgICAgICAgMzg5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2lwcnRdCnJvb3QgICAgICAgNTA4ICAwLjAgIDAuMSAgMjM0MTYgICA5NDQgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgcnBjYmluZApzdGF0ZCAgICAgIDUyNSAgMC4wICAwLjIgIDIxNTQwICAxMTY0ID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIHJwYy5zdGF0ZCAtTApyb290ICAgICAgIDUyOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UzOjFdCnJvb3QgICAgICAgNTM5ICAwLjAgIDAuMSAgMTUyNTYgICA1NzIgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgdXBzdGFydC1zb2NrZXQtYnJpZGdlIC0tZGFlbW9uCnJvb3QgICAgICAgODEwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW3JwY2lvZF0Kcm9vdCAgICAgICA4MjYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbbmZzaW9kXQptZXNzYWdlKyAgIDg0MiAgMC4wICAwLjIgIDM5MjEyICAxMDgwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGRidXMtZGFlbW9uIC0tc3lzdGVtIC0tZm9yawpyb290ICAgICAgIDg2NSAgMC4wICAwLjAgIDI1NTQwICAgMzEyID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIHJwYy5pZG1hcGQKcm9vdCAgICAgICA4OTAgIDAuMCAgMC4zICA0MzQ0OCAgMTU3MiA\/ICAgICAgICBTcyAgIDE3OjM5ICAgMDowMCAvbGliL3N5c3RlbWQvc3lzdGVtZC1sb2dpbmQKc3lzbG9nICAgICA5MjIgIDAuMCAgMC4yIDI1NzkwOCAgMTI0NCA\/ICAgICAgICBTc2wgIDE3OjM5ICAgMDowMCByc3lzbG9nZApyb290ICAgICAgIDk1OCAgMC4wICAwLjEgIDE1Mzk2ICAgNTY0ID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIHVwc3RhcnQtZmlsZS1icmlkZ2UgLS1kYWVtb24Kcm9vdCAgICAgIDEwMTggIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHk0ICAgICBTcysgIDE3OjM5ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHk0CnJvb3QgICAgICAxMDIxICAwLjAgIDAuMSAgMTQ1MzYgICA4NzIgdHR5NSAgICAgU3MrICAxNzozOSAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5NQpyb290ICAgICAgMTAyNiAgMC4wICAwLjEgIDE0NTM2ICAgODY0IHR0eTIgICAgIFNzKyAgMTc6MzkgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTIKcm9vdCAgICAgIDEwMjcgIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHkzICAgICBTcysgIDE3OjM5ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHkzCnJvb3QgICAgICAxMDI5ICAwLjAgIDAuMSAgMTQ1MzYgICA4NjggdHR5NiAgICAgU3MrICAxNzozOSAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5Ngpyb290ICAgICAgMTA2NyAgMC4wICAwLjEgICA0MzY0ICAgNjIwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGFjcGlkIC1jIC9ldGMvYWNwaS9ldmVudHMgLXMgL3Zhci9ydW4vYWNwaWQuc29ja2V0CnJvb3QgICAgICAxMDY4ICAwLjAgIDAuMSAgMjM2NTIgICA5OTIgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgY3JvbgpkYWVtb24gICAgMTA2OSAgMC4wICAwLjAgIDE5MTM2ICAgMTYwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGF0ZApyb290ICAgICAgMTA5OSAgMC4wICAwLjEgMjE2NjA4ICAgOTMyID8gICAgICAgIFNsICAgMTc6MzkgICAwOjAyIC91c3Ivc2Jpbi9WQm94U2VydmljZQpyb290ICAgICAgMTI1MCAgMC4wICA2LjcgMTgyNTM2IDMzNzg0ID8gICAgICAgIFNzbCAgMTc6MzkgICAwOjAwIC91c3IvYmluL3J1YnkgL3Vzci9iaW4vcHVwcGV0IGFnZW50CnJvb3QgICAgICAxMjgyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2thdWRpdGRdCnJvb3QgICAgICAxMzIwICAwLjAgIDYuOCAxMTI2ODggMzQ0NzIgPyAgICAgICAgU2wgICAxNzozOSAgIDA6MDAgcnVieSAvdXNyL2Jpbi9jaGVmLWNsaWVudCAtZCAtUCAvdmFyL3J1bi9jaGVmL2NsaWVudC5waWQgLWMgL2V0Yy9jaGVmL2NsaWVudC5yYiAtaSAxODAwIC1zIDIwIC1MIC92YXIvbG9nL2NoZWYvY2xpZW50LmxvZwpyb290ICAgICAgMTM2NiAgMC4wICAwLjEgIDE0NTM2ICAgODY4IHR0eTEgICAgIFNzKyAgMTc6MzkgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTEKcm9vdCAgICAgIDE4NzQgIDAuMCAgMC40ICAxMDIyMCAgMjI5NiA\/ICAgICAgICBTcyAgIDE3OjM5ICAgMDowMCBkaGNsaWVudCAtMSAtdiAtcGYgL3J1bi9kaGNsaWVudC5ldGgwLnBpZCAtbGYgL3Zhci9saWIvZGhjcC9kaGNsaWVudC5ldGgwLmxlYXNlcyBldGgwCnJvb3QgICAgICAxOTQ4ICAwLjAgIDAuNCAgNjEzNjAgIDIzMDAgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgL3Vzci9zYmluL3NzaGQgLUQKbnRwICAgICAgIDMwOTkgIDAuMCAgMC4zICAzMzUwNCAgMTkwMCA\/ICAgICAgICBTcyAgIDE3OjQxICAgMDowMCAvdXNyL3NiaW4vbnRwZCAtcCAvdmFyL3J1bi9udHBkLnBpZCAtZyAtdSAxMDg6MTEzCnJvb3QgICAgICA0NDMwICAwLjAgIDAuOCAxMDc2OTIgIDQyMjQgPyAgICAgICAgU3MgICAxODozOCAgIDA6MDAgc3NoZDogdmFncmFudCBbcHJpdl0KdmFncmFudCAgIDQ1NDYgIDAuMCAgMC40IDEwNzY5MiAgMjE4NCA\/ICAgICAgICBTICAgIDE4OjM4ICAgMDowMCBzc2hkOiB2YWdyYW50QHB0cy8yIAp2YWdyYW50ICAgNDU0OSAgMC4wICAwLjcgIDIxNDAwICAzOTQwIHB0cy8yICAgIFNzICAgMTg6MzggICAwOjAwIC1iYXNoCnJvb3QgICAgICA0NzgxICAwLjAgIDAuMSAgIDQ0NDAgICA2NDQgPyAgICAgICAgU3MgICAxNzo0MSAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtd2F0Y2hkb2cgID4+IC92YXIvbG9nL2g0ZC93YXRjaGRvZy5sb2cgL2Jpbi9zaApyb290ICAgICAgNDc4MiAgMC4xICAyLjUgMjM3NDUyIDEyODkyID8gICAgICAgIFMgICAgMTc6NDEgICAwOjA5IGg0ZC13YXRjaGRvZyAgICAgICAgICAgICAKcm9vdCAgICAgIDQ3OTAgIDAuMCAgMC4xICAgNDQ0MCAgIDY0OCA\/ICAgICAgICBTcyAgIDE3OjQxICAgMDowMCAvYmluL3NoIC1lIC1jIC91c3IvYmluL2g0ZC1tZXRyaWNzICA+PiAvdmFyL2xvZy9oNGQvbWV0cmljcy5sb2cgL2Jpbi9zaApyb290ICAgICAgNDc5MSAgMC4xICAyLjIgMjMyNDAwIDExNDA4ID8gICAgICAgIFMgICAgMTc6NDEgICAwOjA4IGg0ZC1tZXRyaWNzICAgICAgICAgICAgIApyb290ICAgICAgNTg3OSAgMC4wICAwLjYgIDkxMjEyICAzMjQ0ID8gICAgICAgIFNzICAgMTc6NDMgICAwOjAwIC91c3Ivc2Jpbi9hcGFjaGUyIC1rIHN0YXJ0Cnd3dy1kYXRhICA1ODgyICAwLjAgIDAuNSAzODAzODQgIDI2NTIgPyAgICAgICAgU2wgICAxNzo0MyAgIDA6MDIgL3Vzci9zYmluL2FwYWNoZTIgLWsgc3RhcnQKd3d3LWRhdGEgIDU4ODMgIDAuMCAgMC41IDM4MDM4NCAgMjY1MiA\/ICAgICAgICBTbCAgIDE3OjQzICAgMDowMiAvdXNyL3NiaW4vYXBhY2hlMiAtayBzdGFydApyb290ICAgICAzMDI3MyAgMC4wICAwLjMgIDYzMjQ4ICAxODMyIHB0cy8yICAgIFMgICAgMTg6NDQgICAwOjAwIHN1IC1sCnJvb3QgICAgIDMwMjc0ICAwLjAgIDAuNyAgMjEzMzYgIDM5NDggcHRzLzIgICAgUysgICAxODo0NCAgIDA6MDAgLXN1CnJvb3QgICAgIDMwMzYyICAwLjAgIDAuMSAgIDQ0NDAgICA2NDQgPyAgICAgICAgU3MgICAxODo0NiAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtcnBjLXNlcnZlciAgPj4gL3Zhci9sb2cvaDRkL3JwYy1zZXJ2ZXIubG9nIC9iaW4vc2gKcm9vdCAgICAgMzAzNjMgIDAuMCAgMy40IDIzODM2NCAxNzIyOCA\/ICAgICAgICBTICAgIDE4OjQ2ICAgMDowMCBoNGQtcnBjLXNlcnZlciAgICAgICAgICAgICAKcm9vdCAgICAgMzA0MjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ2ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1MDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ5ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1MjggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ5ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1OTkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjUzICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExMDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExNDAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2NzQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2ODAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2ODUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE3MTEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM2ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzI2MzUgIDAuMSAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDIwOjA1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzI2NDEgIDEuMCAgMi42IDIzODgwMCAxMzUxMiA\/ICAgICAgICBTICAgIDIwOjA1ICAgMDowMCBoNGQtcnBjLXNlcnZlciAgICAgICAgICAgICAKcm9vdCAgICAgMzI2NDMgIDAuMCAgMC4xICAgNDQ0MCAgIDY0OCA\/ICAgICAgICBTICAgIDIwOjA1ICAgMDowMCBzaCAtYyAvdmFyL3RtcC8xNDU2OTQ5MTU3LTVmYTIxYjA3MTFiNmQyZGE0YmZkOTMyYzdkMmVmOGRiCnJvb3QgICAgIDMyNjQ0ICAwLjAgIDAuMiAgMTc5NTYgIDE0MTYgPyAgICAgICAgUyAgICAyMDowNSAgIDA6MDAgL2Jpbi9iYXNoIC92YXIvdG1wLzE0NTY5NDkxNTctNWZhMjFiMDcxMWI2ZDJkYTRiZmQ5MzJjN2QyZWY4ZGIKcm9vdCAgICAgMzI2NDUgIDAuMCAgMC4yICAxNTU2NCAgMTE2MCA\/ICAgICAgICBSICAgIDIwOjA1ICAgMDowMCBwcyAtYXV4Cg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T20:17:47+00:00",
                    "updatedAt": "2016-03-02T20:17:48+00:00"
                },
                "1bf1552ce90a79ac0d901d60369ed256": {
                    "slave": "fi9CvJ-007",
                    "executionToken": "1bf1552ce90a79ac0d901d60369ed256",
                    "startDate": "2016-03-02T20:18:01+00:00",
                    "endDate": "2016-03-02T20:18:02+00:00",
                    "stdout": "VVNFUiAgICAgICBQSUQgJUNQVSAlTUVNICAgIFZTWiAgIFJTUyBUVFkgICAgICBTVEFUIFNUQVJUICAgVElNRSBDT01NQU5ECnJvb3QgICAgICAgICAxICAwLjAgIDAuNSAgMzM1ODQgIDI3NjQgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgL3NiaW4vaW5pdApyb290ICAgICAgICAgMiAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtrdGhyZWFkZF0Kcm9vdCAgICAgICAgIDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba3NvZnRpcnFkLzBdCnJvb3QgICAgICAgICA0ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2t3b3JrZXIvMDowXQpyb290ICAgICAgICAgNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyLzA6MEhdCnJvb3QgICAgICAgICA3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDIgW3JjdV9zY2hlZF0Kcm9vdCAgICAgICAgIDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMiBbcmN1b3MvMF0Kcm9vdCAgICAgICAgIDkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBbcmN1X2JoXQpyb290ICAgICAgICAxMCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtyY3VvYi8wXQpyb290ICAgICAgICAxMSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFttaWdyYXRpb24vMF0Kcm9vdCAgICAgICAgMTIgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBbd2F0Y2hkb2cvMF0Kcm9vdCAgICAgICAgMTMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBba2hlbHBlcl0Kcm9vdCAgICAgICAgMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba2RldnRtcGZzXQpyb290ICAgICAgICAxNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtuZXRuc10Kcm9vdCAgICAgICAgMTYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbd3JpdGViYWNrXQpyb290ICAgICAgICAxNyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtraW50ZWdyaXR5ZF0Kcm9vdCAgICAgICAgMTggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbYmlvc2V0XQpyb290ICAgICAgICAxOSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UzOjBdCnJvb3QgICAgICAgIDIwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2tibG9ja2RdCnJvb3QgICAgICAgIDIxICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2F0YV9zZmZdCnJvb3QgICAgICAgIDIyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2todWJkXQpyb290ICAgICAgICAyMyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFttZF0Kcm9vdCAgICAgICAgMjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbZGV2ZnJlcV93cV0Kcm9vdCAgICAgICAgMjUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMiBba3dvcmtlci8wOjFdCnJvb3QgICAgICAgIDI2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2todW5ndGFza2RdCnJvb3QgICAgICAgIDI3ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2tzd2FwZDBdCnJvb3QgICAgICAgIDI4ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgU04gICAxNzozOSAgIDA6MDAgW2tzbWRdCnJvb3QgICAgICAgIDI5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2Zzbm90aWZ5X21hcmtdCnJvb3QgICAgICAgIDMwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2VjcnlwdGZzLWt0aHJlYV0Kcm9vdCAgICAgICAgMzEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbY3J5cHRvXQpyb290ICAgICAgICA0MyAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrdGhyb3RsZF0Kcm9vdCAgICAgICAgNjMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbZGVmZXJ3cV0Kcm9vdCAgICAgICAgNjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbY2hhcmdlcl9tYW5hZ2VyXQpyb290ICAgICAgIDEwNSAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtzY3NpX2VoXzBdCnJvb3QgICAgICAgMTA2ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2twc21vdXNlZF0Kcm9vdCAgICAgICAxMDcgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTICAgIDE3OjM5ICAgMDowMCBba3dvcmtlci91MjoyXQpyb290ICAgICAgIDEwOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UyOjNdCnJvb3QgICAgICAgMTUzICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2piZDIvc2RhMS04XQpyb290ICAgICAgIDE1NCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtleHQ0LXJzdi1jb252ZXJdCnJvb3QgICAgICAgMzUzICAwLjAgIDAuMSAgMTk0NzIgICA1NDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgdXBzdGFydC11ZGV2LWJyaWRnZSAtLWRhZW1vbgpyb290ICAgICAgIDM1OCAgMC4wICAwLjIgIDQ5NjAwICAxMjU2ID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIC9saWIvc3lzdGVtZC9zeXN0ZW1kLXVkZXZkIC0tZGFlbW9uCnJvb3QgICAgICAgMzg5ICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW2lwcnRdCnJvb3QgICAgICAgNTA4ICAwLjAgIDAuMSAgMjM0MTYgICA5NDQgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgcnBjYmluZApzdGF0ZCAgICAgIDUyNSAgMC4wICAwLjIgIDIxNTQwICAxMTY0ID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIHJwYy5zdGF0ZCAtTApyb290ICAgICAgIDUyOCAgMC4wICAwLjAgICAgICAwICAgICAwID8gICAgICAgIFM8ICAgMTc6MzkgICAwOjAwIFtrd29ya2VyL3UzOjFdCnJvb3QgICAgICAgNTM5ICAwLjAgIDAuMSAgMTUyNTYgICA1NzIgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgdXBzdGFydC1zb2NrZXQtYnJpZGdlIC0tZGFlbW9uCnJvb3QgICAgICAgODEwICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUzwgICAxNzozOSAgIDA6MDAgW3JwY2lvZF0Kcm9vdCAgICAgICA4MjYgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBTPCAgIDE3OjM5ICAgMDowMCBbbmZzaW9kXQptZXNzYWdlKyAgIDg0MiAgMC4wICAwLjIgIDM5MjEyICAxMDgwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGRidXMtZGFlbW9uIC0tc3lzdGVtIC0tZm9yawpyb290ICAgICAgIDg2NSAgMC4wICAwLjAgIDI1NTQwICAgMzEyID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIHJwYy5pZG1hcGQKcm9vdCAgICAgICA4OTAgIDAuMCAgMC4zICA0MzQ0OCAgMTU3MiA\/ICAgICAgICBTcyAgIDE3OjM5ICAgMDowMCAvbGliL3N5c3RlbWQvc3lzdGVtZC1sb2dpbmQKc3lzbG9nICAgICA5MjIgIDAuMCAgMC4yIDI1NzkwOCAgMTI0NCA\/ICAgICAgICBTc2wgIDE3OjM5ICAgMDowMCByc3lzbG9nZApyb290ICAgICAgIDk1OCAgMC4wICAwLjEgIDE1Mzk2ICAgNTY0ID8gICAgICAgIFMgICAgMTc6MzkgICAwOjAwIHVwc3RhcnQtZmlsZS1icmlkZ2UgLS1kYWVtb24Kcm9vdCAgICAgIDEwMTggIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHk0ICAgICBTcysgIDE3OjM5ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHk0CnJvb3QgICAgICAxMDIxICAwLjAgIDAuMSAgMTQ1MzYgICA4NzIgdHR5NSAgICAgU3MrICAxNzozOSAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5NQpyb290ICAgICAgMTAyNiAgMC4wICAwLjEgIDE0NTM2ICAgODY0IHR0eTIgICAgIFNzKyAgMTc6MzkgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTIKcm9vdCAgICAgIDEwMjcgIDAuMCAgMC4xICAxNDUzNiAgIDg2NCB0dHkzICAgICBTcysgIDE3OjM5ICAgMDowMCAvc2Jpbi9nZXR0eSAtOCAzODQwMCB0dHkzCnJvb3QgICAgICAxMDI5ICAwLjAgIDAuMSAgMTQ1MzYgICA4NjggdHR5NiAgICAgU3MrICAxNzozOSAgIDA6MDAgL3NiaW4vZ2V0dHkgLTggMzg0MDAgdHR5Ngpyb290ICAgICAgMTA2NyAgMC4wICAwLjEgICA0MzY0ICAgNjIwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGFjcGlkIC1jIC9ldGMvYWNwaS9ldmVudHMgLXMgL3Zhci9ydW4vYWNwaWQuc29ja2V0CnJvb3QgICAgICAxMDY4ICAwLjAgIDAuMSAgMjM2NTIgICA5OTIgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgY3JvbgpkYWVtb24gICAgMTA2OSAgMC4wICAwLjAgIDE5MTM2ICAgMTYwID8gICAgICAgIFNzICAgMTc6MzkgICAwOjAwIGF0ZApyb290ICAgICAgMTA5OSAgMC4wICAwLjEgMjE2NjA4ICAgOTMyID8gICAgICAgIFNsICAgMTc6MzkgICAwOjAyIC91c3Ivc2Jpbi9WQm94U2VydmljZQpyb290ICAgICAgMTI1MCAgMC4wICA2LjcgMTgyNTM2IDMzNzg0ID8gICAgICAgIFNzbCAgMTc6MzkgICAwOjAwIC91c3IvYmluL3J1YnkgL3Vzci9iaW4vcHVwcGV0IGFnZW50CnJvb3QgICAgICAxMjgyICAwLjAgIDAuMCAgICAgIDAgICAgIDAgPyAgICAgICAgUyAgICAxNzozOSAgIDA6MDAgW2thdWRpdGRdCnJvb3QgICAgICAxMzIwICAwLjAgIDYuOCAxMTI2ODggMzQ0NzIgPyAgICAgICAgU2wgICAxNzozOSAgIDA6MDAgcnVieSAvdXNyL2Jpbi9jaGVmLWNsaWVudCAtZCAtUCAvdmFyL3J1bi9jaGVmL2NsaWVudC5waWQgLWMgL2V0Yy9jaGVmL2NsaWVudC5yYiAtaSAxODAwIC1zIDIwIC1MIC92YXIvbG9nL2NoZWYvY2xpZW50LmxvZwpyb290ICAgICAgMTM2NiAgMC4wICAwLjEgIDE0NTM2ICAgODY4IHR0eTEgICAgIFNzKyAgMTc6MzkgICAwOjAwIC9zYmluL2dldHR5IC04IDM4NDAwIHR0eTEKcm9vdCAgICAgIDE4NzQgIDAuMCAgMC40ICAxMDIyMCAgMjI5NiA\/ICAgICAgICBTcyAgIDE3OjM5ICAgMDowMCBkaGNsaWVudCAtMSAtdiAtcGYgL3J1bi9kaGNsaWVudC5ldGgwLnBpZCAtbGYgL3Zhci9saWIvZGhjcC9kaGNsaWVudC5ldGgwLmxlYXNlcyBldGgwCnJvb3QgICAgICAxOTQ4ICAwLjAgIDAuNCAgNjEzNjAgIDIzMDAgPyAgICAgICAgU3MgICAxNzozOSAgIDA6MDAgL3Vzci9zYmluL3NzaGQgLUQKbnRwICAgICAgIDMwOTkgIDAuMCAgMC4zICAzMzUwNCAgMTkwMCA\/ICAgICAgICBTcyAgIDE3OjQxICAgMDowMCAvdXNyL3NiaW4vbnRwZCAtcCAvdmFyL3J1bi9udHBkLnBpZCAtZyAtdSAxMDg6MTEzCnJvb3QgICAgICA0NDMwICAwLjAgIDAuOCAxMDc2OTIgIDQyMjQgPyAgICAgICAgU3MgICAxODozOCAgIDA6MDAgc3NoZDogdmFncmFudCBbcHJpdl0KdmFncmFudCAgIDQ1NDYgIDAuMCAgMC40IDEwNzY5MiAgMjE4NCA\/ICAgICAgICBTICAgIDE4OjM4ICAgMDowMCBzc2hkOiB2YWdyYW50QHB0cy8yIAp2YWdyYW50ICAgNDU0OSAgMC4wICAwLjcgIDIxNDAwICAzOTQwIHB0cy8yICAgIFNzICAgMTg6MzggICAwOjAwIC1iYXNoCnJvb3QgICAgICA0NzgxICAwLjAgIDAuMSAgIDQ0NDAgICA2NDQgPyAgICAgICAgU3MgICAxNzo0MSAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtd2F0Y2hkb2cgID4+IC92YXIvbG9nL2g0ZC93YXRjaGRvZy5sb2cgL2Jpbi9zaApyb290ICAgICAgNDc4MiAgMC4xICAyLjUgMjM3NDUyIDEyODkyID8gICAgICAgIFMgICAgMTc6NDEgICAwOjA5IGg0ZC13YXRjaGRvZyAgICAgICAgICAgICAKcm9vdCAgICAgIDQ3OTAgIDAuMCAgMC4xICAgNDQ0MCAgIDY0OCA\/ICAgICAgICBTcyAgIDE3OjQxICAgMDowMCAvYmluL3NoIC1lIC1jIC91c3IvYmluL2g0ZC1tZXRyaWNzICA+PiAvdmFyL2xvZy9oNGQvbWV0cmljcy5sb2cgL2Jpbi9zaApyb290ICAgICAgNDc5MSAgMC4xICAyLjIgMjMyNDAwIDExNDA4ID8gICAgICAgIFMgICAgMTc6NDEgICAwOjA4IGg0ZC1tZXRyaWNzICAgICAgICAgICAgIApyb290ICAgICAgNTg3OSAgMC4wICAwLjYgIDkxMjEyICAzMjQ0ID8gICAgICAgIFNzICAgMTc6NDMgICAwOjAwIC91c3Ivc2Jpbi9hcGFjaGUyIC1rIHN0YXJ0Cnd3dy1kYXRhICA1ODgyICAwLjAgIDAuNSAzODAzODQgIDI2NTIgPyAgICAgICAgU2wgICAxNzo0MyAgIDA6MDIgL3Vzci9zYmluL2FwYWNoZTIgLWsgc3RhcnQKd3d3LWRhdGEgIDU4ODMgIDAuMCAgMC41IDM4MDM4NCAgMjY1MiA\/ICAgICAgICBTbCAgIDE3OjQzICAgMDowMiAvdXNyL3NiaW4vYXBhY2hlMiAtayBzdGFydApyb290ICAgICAzMDI3MyAgMC4wICAwLjMgIDYzMjQ4ICAxODMyIHB0cy8yICAgIFMgICAgMTg6NDQgICAwOjAwIHN1IC1sCnJvb3QgICAgIDMwMjc0ICAwLjAgIDAuNyAgMjEzMzYgIDM5NDggcHRzLzIgICAgUysgICAxODo0NCAgIDA6MDAgLXN1CnJvb3QgICAgIDMwMzYyICAwLjAgIDAuMSAgIDQ0NDAgICA2NDQgPyAgICAgICAgU3MgICAxODo0NiAgIDA6MDAgL2Jpbi9zaCAtZSAtYyAvdXNyL2Jpbi9oNGQtcnBjLXNlcnZlciAgPj4gL3Zhci9sb2cvaDRkL3JwYy1zZXJ2ZXIubG9nIC9iaW4vc2gKcm9vdCAgICAgMzAzNjMgIDAuMCAgMy40IDIzODM2NCAxNzIyOCA\/ICAgICAgICBTICAgIDE4OjQ2ICAgMDowMCBoNGQtcnBjLXNlcnZlciAgICAgICAgICAgICAKcm9vdCAgICAgMzA0MjQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ2ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1MDMgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ5ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1MjggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjQ5ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzA1OTkgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE4OjUzICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExMDggIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExMTQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzExNDAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjExICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2NzQgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2ODAgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE2ODUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzE3MTEgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDE5OjM2ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzI2MzUgIDAuMCAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDIwOjA1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzI2NDEgIDAuMSAgMC4wICAgICAgMCAgICAgMCA\/ICAgICAgICBaICAgIDIwOjA1ICAgMDowMCBbcGhwXSA8ZGVmdW5jdD4Kcm9vdCAgICAgMzI2NjYgIDEuMCAgMi42IDIzODgwMCAxMzUxMiA\/ICAgICAgICBTICAgIDIwOjA2ICAgMDowMCBoNGQtcnBjLXNlcnZlciAgICAgICAgICAgICAKcm9vdCAgICAgMzI2NjggIDAuMCAgMC4xICAgNDQ0MCAgIDY0OCA\/ICAgICAgICBTICAgIDIwOjA2ICAgMDowMCBzaCAtYyAvdmFyL3RtcC8xNDU2OTQ5MTcxLTVmYTIxYjA3MTFiNmQyZGE0YmZkOTMyYzdkMmVmOGRiCnJvb3QgICAgIDMyNjY5ICAwLjAgIDAuMiAgMTc5NTYgIDE0MTIgPyAgICAgICAgUyAgICAyMDowNiAgIDA6MDAgL2Jpbi9iYXNoIC92YXIvdG1wLzE0NTY5NDkxNzEtNWZhMjFiMDcxMWI2ZDJkYTRiZmQ5MzJjN2QyZWY4ZGIKcm9vdCAgICAgMzI2NzAgIDAuMCAgMC4yICAxNTU2NCAgMTE1NiA\/ICAgICAgICBSICAgIDIwOjA2ICAgMDowMCBwcyAtYXV4Cg==",
                    "stderr": "",
                    "terminationCode": 0,
                    "status": "COMPLETED",
                    "createdAt": "2016-03-02T20:18:01+00:00",
                    "updatedAt": "2016-03-02T20:18:02+00:00"
                }
            }
        }
    }
}
```

Get user snippets execution queue.

### HTTP Request

`GET  /v1/snippets/execution-queue`


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
-d '{"token":"token","title":"title","code":"code","interpreter":"interpreter","visibility":"visibility","notes":"notes"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->updateSnippet($token,$title,$code,$interpreter,$visibility,$notes);
```

> The above command returns JSON structured like this:

```json
null
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
## Install recipes.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/install" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"lnqlqx-012","recipes":["apache"]}'
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
    "data": "9a4859dfc5ec48475f5cf3b02536216c"
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
