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

## Get snippet by token.
```shell
curl "https://api.hosting4devs.com/v1/snippet/:token" \
-X GET \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->getSnippetByToken($token);
```

> The above command returns JSON structured like this:

```json
null
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
null
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
null
```

Get user snippets execution queue.

### HTTP Request

`GET  /v1/snippets/execution-queue`


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
## Execute a snippet with the given token.
```shell
curl "https://api.hosting4devs.com/v1/server/:server/snippet/:token" \
-X PUT \
-u apiUser:apiPassword \
-H "Content-Type: application/json"\
-d '{"server":"server","token":"token"}'
```

```php
/** @var $client \H4D\ApiClient\Client */
$response = $client->executeSnippet($server,$token);
```

> The above command returns JSON structured like this:

```json
null
```

Execute a snippet with the given token.

### HTTP Request

`PUT  /v1/server/:server/snippet/:token`

### URL parameters

Parameter | Required | Description | Type | Values | Default value
--------- | -------- | ----------- | ---- | ------ | --------------
server | true | Server API ID | string | - | -
token | true | Snippet token | string | - | -

