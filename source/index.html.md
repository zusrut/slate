---
title: API Docs

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - directory
  - dialplan
  - configuration
  - rest

search: true
code_clipboard: true
---

# Introduction

Welcome to the CustomPbx API! You can use it to manipulate configs, dialplan and directory of FreeSwitch.
Here we have language bindings in Shell and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


<aside class="warning">
This is a draft and under development so could have changes in future.
</aside>

# Transport
> Request schema:

```json
{
    "event":"",
    "data":{}
}
```

> Response schema have one mandatory field:

```json
{
"MessageType": ""
}
```

```javascript
let exampleSocket = new WebSocket('https://HOST:PORT/ws', '');
```

API available with http POST requests or trough websocket transport.
Routes for websocket can be cofigured in CustomPbx conf file default: <code>https://HOST:PORT/ws</code>, POST route <code>https://HOST:PORT/api/v1</code>.

<aside class="notice">
Methods that manipulate with authentication tokens are available only with websocket transport.
</aside>

# Websocket Methods Only

### login

```javascript
exampleSocket.send('{"event":"login","data":{"login":"admin","password":"admin"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "login",
	"token": "asd3fvdg45fshj8dv33fsdgy6sdge2sdvstt",
	"user": {
		"id": 1,
		"login": "admin",
		"sip_id": {
			"Int64": 19,
			"Valid": true
		},
		"webrtc_lib": "sipjs",
		"ws": "wss://111.111.111.111:7443",
		"verto_ws": "",
		"stun": "",
		"avatar_format": "",
		"enabled": true,
		"lang": 0
	}
}
```

Generates new api token and returns logged user data.

##### Event value

`login`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
login | string | User name.
password | string | User password.

##### Errors

* Unknown user
* Wrong Login
* Cant set token

###Logout

```javascript
exampleSocket.send('{"event":"[Auth] Logout","data":{"token":"asd3fvdg45fshj8dv33fsdgy6sdge2sdvstt"}}');
```

> Returns JSON structured like this:

```json
{
    "MessageType": "[Auth] Logout"
}
```

Removes api token for user and unsubscribe from events.

##### Event value

`[Auth] Logout`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.

##### Errors

* Cant delete token


###relogin

```javascript
exampleSocket.send('{"event":"login","data":{"token":"asd3fvdg45fshj8dv33fsdgy6sdge2sdvstt"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "relogin",
	"token": "asd3fvdg45fshj8dv33fsdgy6sdge2sdvstt",
	"user": {
		"id": 1,
		"login": "admin",
		"sip_id": {
			"Int64": 19,
			"Valid": true
		},
		"webrtc_lib": "sipjs",
		"ws": "wss://111.111.111.111:7443",
		"verto_ws": "",
		"stun": "",
		"avatar_format": "",
		"enabled": true,
		"lang": 0
	}
}
```

Returning user data by token if exists.

##### Event value

`relogin`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.

##### Errors

* Unknown user
* Wrong Login
* Cant set token

###Dialplan Debug

```javascript
exampleSocket.send('{"event":"[Dialplan][Switch] Debug","data":{"token":"asd3fvdg45fshj8dv33fsdgy6sdge2sdvstt","enabled":true}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "[Dialplan][Switch] Debug",
	"enabled": true
}
```

> Example of event body:

```json
{
	"MessageType": "[Dialplan] Debug",
	"dialplan_debug": {
		"log": [
			"[CONDITION 105] (false) [unloop] ${unroll_loops}(_UNDEF_) =~ /^true$/ break=on-false \n",
			"[CONDITION 107] (true) [outside_call] EMPTY(_UNDEF_) =~ // break=on-false \n",
			"[CONDITION 108] (false) [call_debug] ${call_debug}(_UNDEF_) =~ /^true$/ break=never \n",
			"[CONDITION 109] (false) [public_extensions] destination_number(062100442922550325) =~ /^(10[01][0-9])$/ break=on-false \n",
			"[CONDITION 110] (false) [public_conference_extensions] destination_number(062100442922550325) =~ /^(3[5-8][01][0-9])$/ break=on-false \n",
			"[CONDITION 111] (false) [public_did] destination_number(062100442922550325) =~ /^(5551212)$/ break=on-false \n"
		],
		"actions": [
			{
				"id": 0,
				"enabled": false,
				"position": 0,
				"application": "set",
				"data": "outside_call=true",
				"inline": false
			},
			{
				"id": 0,
				"enabled": false,
				"position": 0,
				"application": "export",
				"data": "RFC2822_DATE=${strftime(%a, %d %b %Y %T %z)}",
				"inline": false
			}
		]
	}
}
```

Enabling or disabling dialplan events sending to websocket.

##### Event value

`[Dialplan][Switch] Debug`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
enabled | boolean | 

##### Errors

None.
###SubscriptionList

```javascript
exampleSocket.send('{"event":"SubscriptionList","data":{"token":"dd64511448aed2ce2160fc091a79749d","values":["[Config] Get_sofia_profiles"]}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "OK"
}
```

Enabling collect events trough websocket by name.

List of available events:

* \[Dashboard]
* \[Config] Get_sofia_profiles
* \[Config] Get_sofia_profile_gateways
* \[Config]\[Get] Modules
* \[Dialplan] Debug
* \[Users] Get_users
* SubscribeCallcenterAgents
* connection

##### Event value

`SubscriptionList`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
values | array(string) | List of subscriptions.

##### Errors

* cant subscribe!

###UnSubscribe

```javascript
exampleSocket.send('{"event":"[UnSubscribe]","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "OK"
}
```

##### Event value

`[UnSubscribe]`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
name | string | Name of event could be empty string to unsubscribe from all.

##### Errors

None.

###AddUserToken

```javascript
exampleSocket.send('{"event":"AddUserToken","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":1}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "AddUserToken",
	"tokens_list": [
		{
			"id": 25,
			"login": "",
			"token": "891ff2c6aea84e646a7303b2773876f7",
			"created": "2020-07-04 17:23:08.192",
			"purpose": "api"
		}
	],
	"id": 1
}
```

Creates new token for user for api purposes.

##### Event value

`AddUserToken`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
id | integer | User id to create token for.

##### Errors

* wrong id
* user not found
* Cant set token

###GetUserTokens

```javascript
exampleSocket.send('{"event":"GetUserTokens","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":1}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "GetUserTokens",
	"tokens_list": [
		{
			"id": 17,
			"login": "",
			"token": "b0391946307c03fa9ac870fe3647ce2b",
			"created": "2020-06-27 09:41:29.427",
			"purpose": "api"
		},
		{
			"id": 24,
			"login": "",
			"token": "dd64511448aed2ce2160fc091a79749d",
			"created": "2020-07-04 11:39:04.174",
			"purpose": "gui"
		}
	],
	"id": 1
}
```

Returns list of user's tokens by sent user id.

##### Event value

`GetUserTokens`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
id | integer | User id.

##### Errors

* wrong id
* user not found


###UserGetOwnTokens

```javascript
exampleSocket.send('{"event":"UserGetOwnTokens","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "GetUserTokens",
	"tokens_list": [
		{
			"id": 17,
			"login": "",
			"token": "b0391946307c03fa9ac870fe3647ce2b",
			"created": "2020-06-27 09:41:29.427",
			"purpose": "api"
		},
		{
			"id": 24,
			"login": "",
			"token": "dd64511448aed2ce2160fc091a79749d",
			"created": "2020-07-04 11:39:04.174",
			"purpose": "gui"
		}
	],
	"id": 1
}
```

Returns list of current user's tokens.

##### Event value

`UserGetOwnTokens`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.

##### Errors

None.

###RemoveUserToken

```javascript
exampleSocket.send('{"event":"RemoveUserToken","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":25}}');
```

> Returns JSON structured like this:

```json
{
	"event": "RemoveUserToken",
	"data": {
		"token": "dd64511448aed2ce2160fc091a79749d",
		"id": 25
	}
}
```

Deleting user token.

##### Event value

`RemoveUserToken`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
id | integer | User id.

##### Errors

* wrong id

# Websocket and POST Methods

## Custom Data

### Get Settings

```shell
curl -X POST "https://HOST:PORT/api/v1"
    -d '{"event":"get_settings","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```

```javascript
exampleSocket.send('{"event":"get_settings","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "settings",
	"settings": {
		"freeswitch": {
			"esl": {
				"host": "127.0.0.1",
				"port": 8021,
				"pass": "ClueCon",
				"timeout": 10,
				"collect_logs": 7
			}
		},
		"webserver": {
			"route": "/ws",
			"host": "188.188.188.188",
			"port": 8080,
			"stun_port": 3478,
			"cert_path": "/etc/freeswitch/tls/wss.pem",
			"key_path": "/etc/freeswitch/tls/wss.pem"
		},
		"xml_curl_server": {
			"route": "/conf/config",
			"host": "127.0.0.1",
			"port": 8080,
			"stun_port": 0,
			"cert_path": "/etc/freeswitch/tls/wss.pem",
			"key_path": "/etc/freeswitch/tls/wss.pem"
		},
		"database": {
			"name": "custompbx",
			"host": "127.0.0.1",
			"port": 5432,
			"user": "custompbx",
			"pass": "custompbx"
		}
	}
}
```

Getting default setting file content.

##### Event value

`get_settings`
`settings`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.

##### Errors


### Set Settings

```shell
curl -X POST "https://HOST:PORT/api/v1"
    -d '{{"event":"set_settings","data":{"token":"dd64511448aed2ce2160fc091a79749d","payload":{"freeswitch":{"esl":{"host":"127.0.0.1","port":8021,"pass":"ClueCon","timeout":101,"collect_logs":7}},"webserver":{"route":"/ws","host":"188.188.188.188","port":8080,"stun_port":3478,"cert_path":"/etc/freeswitch/tls/wss.pem","key_path":"/etc/freeswitch/tls/wss.pem"},"xml_curl_server":{"route":"/conf/config","host":"127.0.0.1","port":8080,"stun_port":0,"cert_path":"/etc/freeswitch/tls/wss.pem","key_path":"/etc/freeswitch/tls/wss.pem"},"database":{"name":"custompbx","host":"127.0.0.1","port":5432,"user":"custompbx","pass":"custompbx"}},"type":"[Settings] Set"}}}'
```

```javascript
exampleSocket.send('{"event":"set_settings","data":{"token":"dd64511448aed2ce2160fc091a79749d","payload":{"freeswitch":{"esl":{"host":"127.0.0.1","port":8021,"pass":"ClueCon","timeout":101,"collect_logs":7}},"webserver":{"route":"/ws","host":"188.188.188.188","port":8080,"stun_port":3478,"cert_path":"/etc/freeswitch/tls/wss.pem","key_path":"/etc/freeswitch/tls/wss.pem"},"xml_curl_server":{"route":"/conf/config","host":"127.0.0.1","port":8080,"stun_port":0,"cert_path":"/etc/freeswitch/tls/wss.pem","key_path":"/etc/freeswitch/tls/wss.pem"},"database":{"name":"custompbx","host":"127.0.0.1","port":5432,"user":"custompbx","pass":"custompbx"}},"type":"[Settings] Set"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "settings",
	"settings": {
		"freeswitch": {
			"esl": {
				"host": "127.0.0.1",
				"port": 8021,
				"pass": "ClueCon",
				"timeout": 10,
				"collect_logs": 7
			}
		},
		"webserver": {
			"route": "/ws",
			"host": "188.188.188.188",
			"port": 8080,
			"stun_port": 3478,
			"cert_path": "/etc/freeswitch/tls/wss.pem",
			"key_path": "/etc/freeswitch/tls/wss.pem"
		},
		"xml_curl_server": {
			"route": "/conf/config",
			"host": "127.0.0.1",
			"port": 8080,
			"stun_port": 0,
			"cert_path": "/etc/freeswitch/tls/wss.pem",
			"key_path": "/etc/freeswitch/tls/wss.pem"
		},
		"database": {
			"name": "custompbx",
			"host": "127.0.0.1",
			"port": 5432,
			"user": "custompbx",
			"pass": "custompbx"
		}
	}
}
```

Updating default setting file content.

##### Event value

`set_settings`
`settings`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.
payload | string | json object of settings.

##### Errors

* empty data
* can't save

### Get Dashboard Data

```shell
curl -X POST "https://HOST:PORT/api/v1"
    -d '{"event":"[Dashboard]", "data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```

```javascript
exampleSocket.send('{"event":"[Dashboard]", "data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```

> Returns JSON structured like this:

```json
{
	"MessageType": "[Dashboard]",
	"dashboard_data": {
		"timestamp": "2020-07-07T18:23:12.732291139Z",
		"hostname": "debian-01",
		"os": "linux",
		"platform": "debian",
		"cpu_model": "Intel Core Processor (Broadwell, IBRS)",
		"cpu_frequency": 2199.994,
		"dynamic_metrics": {
			"total_memory": 1032409088,
			"free_memory": 72151040,
			"percentage_used_memory": 63.959960801894847,
			"total_disc_space": 26288107520,
			"free_disk_space": 14397915136,
			"percentage_disk_usage": 42.244677320241468,
			"core_utilization": [
				5.940594060490095
			]
		},
		"domain_sip_regs": {
			"188.188.188.188": 0,
			"domain.com": 0
		},
		"calls_counter": {
			"answered": 0,
			"total": 0
		},
		"sofia_profiles": [
			{
				"id": 1,
				"enabled": true,
				"name": "external-ipv6",
				"started": false,
				"state": "",
				"uri": ""
			},
			{
				"id": 2,
				"enabled": true,
				"name": "external",
				"started": false,
				"state": "",
				"uri": ""
			},
			{
				"id": 3,
				"enabled": true,
				"name": "internal-ipv6",
				"started": false,
				"state": "",
				"uri": ""
			},
			{
				"id": 4,
				"enabled": true,
				"name": "internal",
				"started": false,
				"state": "",
				"uri": ""
			}
		],
		"sofia_gateways": [
			{
				"id": 1,
				"enabled": true,
				"name": "asterlink.com",
				"started": false,
				"state": ""
			}
		]
	}
}
```

Getting dashboard data.

##### Event value

`[Dashboard]`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | string | User auth token.

##### Errors

