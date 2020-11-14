
## Dialplan


### Contexts



#### Disable/Enable static dialplan

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"DialplanChangeNotProceed","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","enabled":true}}'
```
```javascript
exampleSocket.send('{"event":"DialplanChangeNotProceed","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","enabled":true}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "DialplanChangeNotProceed",
  "dialplan_settings": {
    "no_proceed": true,
    "enable_debug": false
  }
}

```

Disable/Enable proceeding dialplan at custompbx side (generate xml with only actions from matched conditions or return full xml context).

##### Event value

`DialplanChangeNotProceed`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 enabled | Boolean | 


##### Errors





#### Get Contexts List"

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Get] Contexts","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb"}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Get] Contexts","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Get] Contexts",
  "dialplan_contexts": {
    "16": {
      "id": 16,
      "enabled": true,
      "name": "default"
    },
    "18": {
      "id": 18,
      "enabled": true,
      "name": "features"
    },
    "19": {
      "id": 19,
      "enabled": true,
      "name": "public"
    },
    "20": {
      "id": 20,
      "enabled": true,
      "name": "skinny-patterns"
    }
  }
}

```

Returns list of сontexts.

##### Event value

`[Dialplan][Get] Contexts`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.


##### Errors





#### Add Context

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Add] Context","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","name":"new-context"}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Add] Context","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","name":"new-context"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Add] Context",
  "dialplan_contexts": {
    "21": {
      "id": 21,
      "enabled": true,
      "name": "new-context"
    }
  }
}

```

.

##### Event value

`[Dialplan][Add] Context`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 name | String | 


##### Errors

* empty data
* db error




#### Rename Context

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Rename] Context","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":21,"name":"new-context-2"}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Rename] Context","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":21,"name":"new-context-2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Rename] Context",
  "dialplan_contexts": {
    "21": {
      "id": 21,
      "enabled": true,
      "name": "new-context-2"
    }
  }
}

```

.

##### Event value

`[Dialplan][Rename] Context`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* wrong id
* empty data
* context not found
* db error




#### Delete Context

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Delete] Context","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":21}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Delete] Context","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":21}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Delete] Context",
  "id": 21
}

```

.

##### Event value

`[Dialplan][Delete] Context`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* context not found
* db error




#### Get Extensions List

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Get] Extensions","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":19}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Get] Extensions","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":19}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Get] Extensions",
  "id": 19,
  "dialplan_extensions": [
    {
      "id": 375,
      "enabled": true,
      "position": 2,
      "name": "outside_call",
      "continue": "true"
    },
    {
      "id": 376,
      "enabled": true,
      "position": 3,
      "name": "call_debug",
      "continue": "true"
    },
    {
      "id": 378,
      "enabled": true,
      "position": 5,
      "name": "public_conference_extensions",
      "continue": ""
    },
    {
      "id": 377,
      "enabled": true,
      "position": 4,
      "name": "public_extensions",
      "continue": ""
    },
    {
      "id": 379,
      "enabled": true,
      "position": 6,
      "name": "public_did",
      "continue": ""
    },
    {
      "id": 374,
      "enabled": true,
      "position": 1,
      "name": "unloop",
      "continue": ""
    }
  ]
}

```

Get Extensions list of context.

##### Event value

`[Dialplan][Get] Extensions`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* context not found



### Extensions



#### Add Extension

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Add] Extension","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","name":"new-extension","id":19}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Add] Extension","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","name":"new-extension","id":19}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Add] Extension",
  "id": 19,
  "dialplan_extensions": [
    {
      "id": 386,
      "enabled": true,
      "position": 7,
      "name": "new-extension",
      "continue": ""
    }
  ]
}

```

.

##### Event value

`[Dialplan][Add] Extension`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 name | String | 
 id | Integer | Item ID.


##### Errors

* wrong id
* empty data
* context not found
* db error




#### Rename Extension

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Rename] Extension","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":386,"name":"new-extension-2"}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Rename] Extension","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":386,"name":"new-extension-2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Rename] Extension",
  "id": 19,
  "dialplan_extensions": [
    {
      "id": 386,
      "enabled": true,
      "position": 7,
      "name": "new-extension-2",
      "continue": ""
    }
  ]
}

```

.

##### Event value

`[Dialplan][Rename] Extension`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* wrong id
* empty data
* extension not found
* db error




#### Delete Extension

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Delete] Extension","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":386}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Delete] Extension","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":386}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Delete] Extension",
  "id": 19,
  "affected_id": 386
}

```

.

##### Event value

`[Dialplan][Delete] Extension`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* extension not found
* db error




#### Set Extension Continue

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Switch] Extension Continue","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":374,"value":"true"}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Switch] Extension Continue","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":374,"value":"true"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Switch] Extension Continue",
  "id": 19,
  "dialplan_extensions": [
    {
      "id": 374,
      "enabled": true,
      "position": 1,
      "name": "unloop",
      "continue": "true"
    }
  ]
}

```

.

##### Event value

`[Dialplan][Switch] Extension Continue`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 value | String | 


##### Errors

* wrong id
* extension not found
* wrong value
* db error



### Conditions



#### Get Conditions

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Get] Conditions","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":374}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Get] Conditions","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":374}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Get] Conditions",
  "id": 19,
  "dialplan_conditions": {
    "374": [
      {
        "id": 485,
        "enabled": true,
        "position": 1,
        "break": "",
        "field": "${unroll_loops}",
        "expression": "^true$",
        "hour": "",
        "mday": "",
        "mon": "",
        "mweek": "",
        "wday": "",
        "date_time": "",
        "time_of_day": "",
        "year": "",
        "minute": "",
        "week": "",
        "yday": "",
        "minday": "",
        "tz_offset": "",
        "dst": "",
        "regex": ""
      },
      {
        "id": 486,
        "enabled": true,
        "position": 2,
        "break": "",
        "field": "${sip_looped_call}",
        "expression": "^true$",
        "hour": "",
        "mday": "",
        "mon": "",
        "mweek": "",
        "wday": "",
        "date_time": "",
        "time_of_day": "",
        "year": "",
        "minute": "",
        "week": "",
        "yday": "",
        "minday": "",
        "tz_offset": "",
        "dst": "",
        "regex": ""
      }
    ]
  }
}

```

.

##### Event value

`[Dialplan][Get] Conditions`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* extension not found




#### Add Condition

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Add] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":374}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Add] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":374}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Add] Condition",
  "id": 19,
  "dialplan_conditions": {
    "374": [
      {
        "id": 499,
        "enabled": true,
        "position": 3,
        "break": "",
        "field": "",
        "expression": "",
        "hour": "",
        "mday": "",
        "mon": "",
        "mweek": "",
        "wday": "",
        "date_time": "",
        "time_of_day": "",
        "year": "",
        "minute": "",
        "week": "",
        "yday": "",
        "minday": "",
        "tz_offset": "",
        "dst": "",
        "regex": ""
      }
    ]
  }
}

```

.

##### Event value

`[Dialplan][Add] Condition`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* extension not found
* db error




#### Update Condition

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Update] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","condition":{"id":499,"enabled":true,"position":3,"break":"","field":"","expression":"","hour":"","mday":"","mon":"","mweek":"","wday":"","date_time":"","time_of_day":"","year":"","minute":"","week":"","yday":"","minday":"","tz_offset":"","dst":"","regex":"","regexes":[],"actions":[],"antiactions":[]}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Update] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","condition":{"id":499,"enabled":true,"position":3,"break":"","field":"","expression":"","hour":"","mday":"","mon":"","mweek":"","wday":"","date_time":"","time_of_day":"","year":"","minute":"","week":"","yday":"","minday":"","tz_offset":"","dst":"","regex":"","regexes":[],"actions":[],"antiactions":[]}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Update] Condition",
  "id": 19,
  "dialplan_conditions": {
    "374": [
      {
        "id": 499,
        "enabled": true,
        "position": 3,
        "break": "",
        "field": "",
        "expression": "",
        "hour": "",
        "mday": "",
        "mon": "",
        "mweek": "",
        "wday": "",
        "date_time": "",
        "time_of_day": "",
        "year": "",
        "minute": "",
        "week": "",
        "yday": "",
        "minday": "",
        "tz_offset": "",
        "dst": "",
        "regex": ""
      }
    ]
  }
}

```

.

##### Event value

`[Dialplan][Update] Condition`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 condition":{"id | Integer | 
 enabled | Boolean | 
 position | Integer | 
 break | String | 
 field | String | 
 expression | String | 
 hour | String | 
 mday | String | 
 mon | String | 
 mweek | String | 
 wday | String | 
 date_time | String | 
 time_of_day | String | 
 year | String | 
 minute | String | 
 week | String | 
 yday | String | 
 minday | String | 
 tz_offset | String | 
 dst | String | 
 regex | String | 
 regexes | Array | 
 actions | Array | 
 antiactions | Array | 


##### Errors

* condition not found
* can't update




#### Disable Condition

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Switch] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","condition":{"id":499,"enabled":false,"position":3,"break":"","field":"","expression":"","hour":"","mday":"","mon":"","mweek":"","wday":"","date_time":"","time_of_day":"","year":"","minute":"","week":"","yday":"","minday":"","tz_offset":"","dst":"","regex":"","regexes":[],"actions":[],"antiactions":[]}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Switch] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","condition":{"id":499,"enabled":false,"position":3,"break":"","field":"","expression":"","hour":"","mday":"","mon":"","mweek":"","wday":"","date_time":"","time_of_day":"","year":"","minute":"","week":"","yday":"","minday":"","tz_offset":"","dst":"","regex":"","regexes":[],"actions":[],"antiactions":[]}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Switch] Condition",
  "id": 19,
  "dialplan_conditions": {
    "374": [
      {
        "id": 499,
        "enabled": false,
        "position": 3,
        "break": "",
        "field": "",
        "expression": "",
        "hour": "",
        "mday": "",
        "mon": "",
        "mweek": "",
        "wday": "",
        "date_time": "",
        "time_of_day": "",
        "year": "",
        "minute": "",
        "week": "",
        "yday": "",
        "minday": "",
        "tz_offset": "",
        "dst": "",
        "regex": ""
      }
    ]
  }
}

```

.

##### Event value

`[Dialplan][Switch] Condition`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 condition":{"id | Integer | 
 enabled | Boolean | 
 position | Integer | 
 break | String | 
 field | String | 
 expression | String | 
 hour | String | 
 mday | String | 
 mon | String | 
 mweek | String | 
 wday | String | 
 date_time | String | 
 time_of_day | String | 
 year | String | 
 minute | String | 
 week | String | 
 yday | String | 
 minday | String | 
 tz_offset | String | 
 dst | String | 
 regex | String | 
 regexes | Array | 
 actions | Array | 
 antiactions | Array | 


##### Errors

* condition not found
* can't update




#### Delete Condition

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Delete] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","condition":{"id":499,"enabled":false,"position":3,"break":"","field":"","expression":"","hour":"","mday":"","mon":"","mweek":"","wday":"","date_time":"","time_of_day":"","year":"","minute":"","week":"","yday":"","minday":"","tz_offset":"","dst":"","regex":"","regexes":[],"actions":[],"antiactions":[]}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Delete] Condition","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","condition":{"id":499,"enabled":false,"position":3,"break":"","field":"","expression":"","hour":"","mday":"","mon":"","mweek":"","wday":"","date_time":"","time_of_day":"","year":"","minute":"","week":"","yday":"","minday":"","tz_offset":"","dst":"","regex":"","regexes":[],"actions":[],"antiactions":[]}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Delete] Condition",
  "id": 19,
  "dialplan_conditions": {
    "374": [
      {
        "id": 499,
        "enabled": false,
        "position": 3,
        "break": "",
        "field": "",
        "expression": "",
        "hour": "",
        "mday": "",
        "mon": "",
        "mweek": "",
        "wday": "",
        "date_time": "",
        "time_of_day": "",
        "year": "",
        "minute": "",
        "week": "",
        "yday": "",
        "minday": "",
        "tz_offset": "",
        "dst": "",
        "regex": ""
      }
    ]
  }
}

```

.

##### Event value

`[Dialplan][Delete] Condition`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 condition":{"id | Integer | 
 enabled | Boolean | 
 position | Integer | 
 break | String | 
 field | String | 
 expression | String | 
 hour | String | 
 mday | String | 
 mon | String | 
 mweek | String | 
 wday | String | 
 date_time | String | 
 time_of_day | String | 
 year | String | 
 minute | String | 
 week | String | 
 yday | String | 
 minday | String | 
 tz_offset | String | 
 dst | String | 
 regex | String | 
 regexes | Array | 
 actions | Array | 
 antiactions | Array | 


##### Errors

* condition not found
* can't update




#### Get Extension Data

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Get] Extension details","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":486}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Get] Extension details","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":486}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Get] Extension details",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "486": {
      "actions": [
        {
          "id": 1176,
          "enabled": true,
          "position": 1,
          "application": "deflect",
          "data": "${destination_number}",
          "inline": false
        }
      ],
      "antiactions": [],
      "regexes": []
    }
  }
}

```

Get extension data, actions and antiactions.

##### Event value

`[Dialplan][Get] Extension details`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* condition not found



### Actions



#### Add Action

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Add] Action","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":500,"action":{"application":"name","data":"value","inline":false}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Add] Action","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":500,"action":{"application":"name","data":"value","inline":false}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Add] Action",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "500": {
      "actions": [
        {
          "id": 1192,
          "enabled": true,
          "position": 1,
          "application": "name",
          "data": "value",
          "inline": false
        }
      ]
    }
  }
}

```

.

##### Event value

`[Dialplan][Add] Action`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 action":{"application | String | 
 data | String | 
 inline | Boolean | 


##### Errors

* wrong id
* empty data
* condition not found
* db error




#### Disable/Enable Action

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Switch] Action","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","action":{"id":1192, "enabled":false}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Switch] Action","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","action":{"id":1192, "enabled":false}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Switch] Action",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "500": {
      "actions": [
        {
          "id": 1192,
          "enabled": false,
          "position": 1,
          "application": "name",
          "data": "value",
          "inline": false
        }
      ]
    }
  }
}

```

.

##### Event value

`[Dialplan][Switch] Action`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 action":{"id | Integer | 
 enabled | Boolean | 


##### Errors

* action not found
* can't update




#### Delete Action

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Delete] Action","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","action":{"id":1192}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Delete] Action","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","action":{"id":1192}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Delete] Action",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "500": {
      "actions": []
    }
  }
}

```

.

##### Event value

`[Dialplan][Delete] Action`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 action":{"id | Integer | 


##### Errors

* action not found
* can't update



### Antiactions



#### Add Antiaction

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Add] Antiaction","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":500,"antiaction":{"application":"name","data":"value"}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Add] Antiaction","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","id":500,"antiaction":{"application":"name","data":"value"}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Add] Antiaction",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "500": {
      "antiactions": [
        {
          "id": 33,
          "enabled": true,
          "position": 1,
          "application": "name",
          "data": "value"
        }
      ]
    }
  }
}

```

.

##### Event value

`[Dialplan][Add] Antiaction`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 antiaction":{"application | String | 
 data | String | 


##### Errors

* wrong id
* empty data
* condition not found
* db error




#### Disable/Enable Antiaction

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Switch] Antiaction","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","antiaction":{"id":33,"enabled":false}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Switch] Antiaction","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","antiaction":{"id":33,"enabled":false}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Switch] Antiaction",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "500": {
      "antiactions": [
        {
          "id": 33,
          "enabled": false,
          "position": 1,
          "application": "name",
          "data": "value"
        }
      ]
    }
  }
}

```

.

##### Event value

`[Dialplan][Switch] Antiaction`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 antiaction":{"id | Integer | 
 enabled | Boolean | 


##### Errors

* antiAction not found
* can't update




#### Delete Antiaction

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Dialplan][Delete] Antiaction","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","antiaction":{"id":33}}}'
```
```javascript
exampleSocket.send('{"event":"[Dialplan][Delete] Antiaction","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","antiaction":{"id":33}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Dialplan][Delete] Antiaction",
  "id": 19,
  "affected_id": 374,
  "dialplan_details": {
    "500": {
      "antiactions": []
    }
  }
}

```

.

##### Event value

`[Dialplan][Delete] Antiaction`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 antiaction":{"id | Integer | 


##### Errors

* antiAction not found
* can't delete


