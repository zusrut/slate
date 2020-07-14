
## Directory

### Domains
#### Get Domains List

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains][Get] Domains","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains][Get] Domains","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains][Get] Domains",
  "domains": {
    "1": {
      "id": 1,
      "enabled": true,
      "name": "domain.com",
      "sip_regs_counter": 0
    },
    "2": {
      "id": 2,
      "enabled": true,
      "name": "test1",
      "sip_regs_counter": 0
    },
    "3": {
      "id": 3,
      "enabled": true,
      "name": "domain2",
      "sip_regs_counter": 0
    }
  }
}

```

Returns list of domains.

##### Event value

`[Domains][Get] Domains`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.


##### Errors






#### Import Domain from given XML

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"ImportXMLDomain","data":{"token":"dd64511448aed2ce2160fc091a79749d","file":"\r\n  <domain name=\"newDomain\">\r\n    <params>\r\n      <param name=\"jsonrpc-allowed-methods\" value=\"verto\"/>\r\n    </params>\r\n    <variables>\r\n      <variable name=\"record_stereo\" value=\"true\"/>\r\n    </variables>\r\n    <groups>\r\n    </groups>\r\n  </domain>"}}'
```
```javascript
exampleSocket.send('{"event":"ImportXMLDomain","data":{"token":"dd64511448aed2ce2160fc091a79749d","file":"\r\n  <domain name=\"newDomain\">\r\n    <params>\r\n      <param name=\"jsonrpc-allowed-methods\" value=\"verto\"/>\r\n    </params>\r\n    <variables>\r\n      <variable name=\"record_stereo\" value=\"true\"/>\r\n    </variables>\r\n    <groups>\r\n    </groups>\r\n  </domain>"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "ImportXMLDomain",
  "domains": {
    "10": {
      "id": 10,
      "enabled": true,
      "name": "new-domain",
      "sip_regs_counter": 0
    },
    "11": {
      "id": 11,
      "enabled": true,
      "name": "newDomain",
      "sip_regs_counter": 0
    },
    "8": {
      "id": 8,
      "enabled": true,
      "name": "domain.com",
      "sip_regs_counter": 0
    },
    "9": {
      "id": 9,
      "enabled": true,
      "name": "test1",
      "sip_regs_counter": 0
    }
  }
}

```

Imports domain from given XML - groups and users can be included..

##### Event value

`ImportXMLDomain`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 file | String | 


##### Errors

* empty data
* can't parse





#### Import Directory from FreeSwitch

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Directory][Import]","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```
```javascript
exampleSocket.send('{"event":"[Directory][Import]","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Directory][Import]"
}

```

Import Domains and full directory data from FreeSwitch.

##### Event value

`[Directory][Import]`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.


##### Errors






#### Add Domain

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains][Add] Domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","name":"new-domain"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains][Add] Domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","name":"new-domain"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains][Add] Domain",
  "domains": {
    "10": {
      "id": 10,
      "enabled": true,
      "name": "new-domain",
      "sip_regs_counter": 0
    }
  }
}

```

Adding new directory domain.

##### Event value

`[Domains][Add] Domain`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 name | String | 


##### Errors

* empty domain name
* domain name already exists





#### Rename Domain

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] Rename_domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":11,"name":"newDomain2"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] Rename_domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":11,"name":"newDomain2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] Rename_domain",
  "domains": {
    "11": {
      "id": 11,
      "enabled": true,
      "name": "newDomain2",
      "sip_regs_counter": 0
    }
  }
}

```

Changing directory domain name.

##### Event value

`[Domains] Rename_domain`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* empty domain name
* domain name already exists





#### Disable Domain

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains][Switch] Domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":10,"enabled":false}}'
```
```javascript
exampleSocket.send('{"event":"[Domains][Switch] Domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":10,"enabled":false}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains][Switch] Domain",
  "domains": {
    "10": {
      "id": 10,
      "enabled": false,
      "name": "new-domain",
      "sip_regs_counter": 0
    }
  }
}

```

Disable directory domain.

##### Event value

`[Domains][Switch] Domain`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 enabled | Boolean | 


##### Errors

* domain not found
* domain not found
* can't change





#### Delete Domain

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] Del_domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":11}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] Del_domain","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":11}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] Del_domain",
  "id": 11
}

```

Remove directory domain with all belonging entities.

##### Event value

`[Domains] Del_domain`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* domain not found
* can't delete domain





#### Get Domain Details

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains][Get] Domain_details","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8}}'
```
```javascript
exampleSocket.send('{"event":"[Domains][Get] Domain_details","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains][Get] Domain_details",
  "domain_details": {
    "8": {
      "parameters": {
        "18": {
          "id": 18,
          "enabled": true,
          "name": "dial-string",
          "value": "{^^:sip_invite_domain=${dialed_domain}:presence_id=${dialed_user}@${dialed_domain}}${sofia_contact(*/${dialed_user}@${dialed_domain})},${verto_contact(${dialed_user}@${dialed_domain})}"
        },
        "19": {
          "id": 19,
          "enabled": true,
          "name": "jsonrpc-allowed-methods",
          "value": "verto"
        }
      },
      "variables": {
        "22": {
          "id": 22,
          "enabled": true,
          "name": "record_stereo",
          "value": "true"
        },
        "23": {
          "id": 23,
          "enabled": true,
          "name": "default_gateway",
          "value": "example.com"
        },
        "24": {
          "id": 24,
          "enabled": true,
          "name": "default_areacode",
          "value": "918"
        },
        "25": {
          "id": 25,
          "enabled": true,
          "name": "transfer_fallback_extension",
          "value": "operator"
        }
      }
    }
  }
}

```

Returns parameters and variables of domain.

##### Event value

`[Domains][Get] Domain_details`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* domain not found





#### Add Domain Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] New_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"index":0,"name":"param1","value":"value1"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] New_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"index":0,"name":"param1","value":"value1"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] New_domain_param",
  "domain_details": {
    "8": {
      "parameters": {
        "23": {
          "id": 23,
          "enabled": true,
          "name": "param1",
          "value": "value1"
        }
      }
    }
  }
}

```

Adding parameter to directory domain.

##### Event value

`[Domains] New_domain_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 index | Integer | 
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* param not found
* can't add





#### Update Domain Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] Update_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":23,"name":"param1","value":"value2"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] Update_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":23,"name":"param1","value":"value2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] Update_domain_param",
  "domain_details": {
    "8": {
      "parameters": {
        "23": {
          "id": 23,
          "enabled": true,
          "name": "param1",
          "value": "value2"
        }
      }
    }
  }
}

```

Changing directory domain parameter name or value or both.

##### Event value

`[Domains] Update_domain_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* param not found
* can't update





#### Disable Domain Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains][Switch] Domain parameter","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":23,"enabled":false}}'
```
```javascript
exampleSocket.send('{"event":"[Domains][Switch] Domain parameter","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":23,"enabled":false}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains][Switch] Domain parameter",
  "domain_details": {
    "8": {
      "parameters": {
        "23": {
          "id": 23,
          "enabled": false,
          "name": "param1",
          "value": "value2"
        }
      }
    }
  }
}

```

Disable directory domain parameter.

##### Event value

`[Domains][Switch] Domain parameter`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 enabled | Boolean | 


##### Errors

* parameter not found
* can't change





#### Delete Domain Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] Del_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":23}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] Del_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":23}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] Del_domain_param",
  "id": 23
}

```

Remove directory domain parameter.

##### Event value

`[Domains] Del_domain_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* can't delete





#### Add Domain Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] New_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"index":0,"name":"var1","value":"value1"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] New_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"index":0,"name":"var1","value":"value1"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] New_domain_var",
  "domain_details": {
    "8": {
      "variables": {
        "31": {
          "id": 31,
          "enabled": true,
          "name": "var1",
          "value": "value1"
        }
      }
    }
  }
}

```

Adding variable to directory domain.

##### Event value

`[Domains] New_domain_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 index | Integer | 
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* domain not found
* can't add





#### Update Domain Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] Update_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":31,"name":"var1","value":"value2"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] Update_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":31,"name":"var1","value":"value2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] Update_domain_var",
  "domain_details": {
    "8": {
      "variables": {
        "31": {
          "id": 31,
          "enabled": true,
          "name": "var1",
          "value": "value2"
        }
      }
    }
  }
}

```

Changing directory domain variable name or value or both.

##### Event value

`[Domains] Update_domain_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* variable not found
* can't add





#### Disable Domain Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains][Switch] Domain variable","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":31,"enabled":false}}'
```
```javascript
exampleSocket.send('{"event":"[Domains][Switch] Domain variable","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":31,"enabled":false}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains][Switch] Domain variable",
  "domain_details": {
    "8": {
      "variables": {
        "31": {
          "id": 31,
          "enabled": false,
          "name": "var1",
          "value": "value2"
        }
      }
    }
  }
}

```

Disable directory domain variable.

##### Event value

`[Domains][Switch] Domain variable`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 enabled | Boolean | 


##### Errors

* wrong id
* empty data
* variable not found
* can't add





#### Delete Domain Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Domains] Del_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":31}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] Del_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":31}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Domains] Del_domain_var",
  "id": 31
}

```

Remove directory domain variable.

##### Event value

`[Domains] Del_domain_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* can't delete

### Users


#### Get Users

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Get_users","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Get_users","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Get_users",
  "domains": {
    "10": {
      "id": 10,
      "enabled": false,
      "name": "new-domain",
      "sip_regs_counter": 0
    },
    "8": {
      "id": 8,
      "enabled": true,
      "name": "domain.com",
      "sip_regs_counter": 0
    },
    "9": {
      "id": 9,
      "enabled": true,
      "name": "test1",
      "sip_regs_counter": 0
    }
  },
  "directory_users": {
    "8": {
      "56": {
        "id": 56,
        "enabled": true,
        "name": "1000",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false,
        "cc_agent": 230
      },
      "57": {
        "id": 57,
        "enabled": true,
        "name": "1001",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "58": {
        "id": 58,
        "enabled": true,
        "name": "1002",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "59": {
        "id": 59,
        "enabled": true,
        "name": "1003",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "60": {
        "id": 60,
        "enabled": true,
        "name": "1004",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "61": {
        "id": 61,
        "enabled": true,
        "name": "1005",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "62": {
        "id": 62,
        "enabled": true,
        "name": "1006",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "63": {
        "id": 63,
        "enabled": true,
        "name": "1007",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "64": {
        "id": 64,
        "enabled": true,
        "name": "1008",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "65": {
        "id": 65,
        "enabled": true,
        "name": "1009",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "66": {
        "id": 66,
        "enabled": true,
        "name": "1010",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "67": {
        "id": 67,
        "enabled": true,
        "name": "1011",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "68": {
        "id": 68,
        "enabled": true,
        "name": "1012",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "69": {
        "id": 69,
        "enabled": true,
        "name": "1013",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "70": {
        "id": 70,
        "enabled": true,
        "name": "1014",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "71": {
        "id": 71,
        "enabled": true,
        "name": "1015",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "72": {
        "id": 72,
        "enabled": true,
        "name": "1016",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "73": {
        "id": 73,
        "enabled": true,
        "name": "1017",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "74": {
        "id": 74,
        "enabled": true,
        "name": "1018",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "75": {
        "id": 75,
        "enabled": true,
        "name": "1019",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "76": {
        "id": 76,
        "enabled": true,
        "name": "brian",
        "cache": 5000,
        "cidr": "192.0.2.0/24",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "77": {
        "id": 77,
        "enabled": true,
        "name": "default",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "78": {
        "id": 78,
        "enabled": true,
        "name": "example.com",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "79": {
        "id": 79,
        "enabled": true,
        "name": "SEP001120AABBCC",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      }
    },
    "9": {
      "100": {
        "id": 100,
        "enabled": true,
        "name": "brian",
        "cache": 5000,
        "cidr": "192.0.2.0/24",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "101": {
        "id": 101,
        "enabled": true,
        "name": "default",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "102": {
        "id": 102,
        "enabled": true,
        "name": "example.com",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "103": {
        "id": 103,
        "enabled": true,
        "name": "SEP001120AABBCC",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "80": {
        "id": 80,
        "enabled": true,
        "name": "1000",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "81": {
        "id": 81,
        "enabled": true,
        "name": "1001",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "82": {
        "id": 82,
        "enabled": true,
        "name": "1002",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "83": {
        "id": 83,
        "enabled": true,
        "name": "1003",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "84": {
        "id": 84,
        "enabled": true,
        "name": "1004",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "85": {
        "id": 85,
        "enabled": true,
        "name": "1005",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "86": {
        "id": 86,
        "enabled": true,
        "name": "1006",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "87": {
        "id": 87,
        "enabled": true,
        "name": "1007",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "88": {
        "id": 88,
        "enabled": true,
        "name": "1008",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "89": {
        "id": 89,
        "enabled": true,
        "name": "1009",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "90": {
        "id": 90,
        "enabled": true,
        "name": "1010",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "91": {
        "id": 91,
        "enabled": true,
        "name": "1011",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "92": {
        "id": 92,
        "enabled": true,
        "name": "1012",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "93": {
        "id": 93,
        "enabled": true,
        "name": "1013",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "94": {
        "id": 94,
        "enabled": true,
        "name": "1014",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "95": {
        "id": 95,
        "enabled": true,
        "name": "1015",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "96": {
        "id": 96,
        "enabled": true,
        "name": "1016",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "97": {
        "id": 97,
        "enabled": true,
        "name": "1017",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "98": {
        "id": 98,
        "enabled": true,
        "name": "1018",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "99": {
        "id": 99,
        "enabled": true,
        "name": "1019",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      }
    }
  }
}

```

Get directory users of domain.

##### Event value

`[Users] Get_users`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.


##### Errors






#### Get User Details

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Get_user_details","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Get_user_details","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Get_user_details",
  "user_details": {
    "56": {
      "parameters": {
        "91": {
          "id": 91,
          "enabled": true,
          "name": "password",
          "value": "5555"
        },
        "92": {
          "id": 92,
          "enabled": true,
          "name": "vm-password",
          "value": "1000"
        }
      },
      "variables": {
        "362": {
          "id": 362,
          "enabled": true,
          "name": "toll_allow",
          "value": "domestic,international,local"
        },
        "363": {
          "id": 363,
          "enabled": true,
          "name": "accountcode",
          "value": "1000"
        },
        "364": {
          "id": 364,
          "enabled": true,
          "name": "user_context",
          "value": "default"
        },
        "365": {
          "id": 365,
          "enabled": true,
          "name": "effective_caller_id_name",
          "value": "Extension 1000"
        },
        "366": {
          "id": 366,
          "enabled": true,
          "name": "effective_caller_id_number",
          "value": "1000"
        },
        "367": {
          "id": 367,
          "enabled": true,
          "name": "outbound_caller_id_name",
          "value": "FreeSWITCH"
        },
        "368": {
          "id": 368,
          "enabled": true,
          "name": "outbound_caller_id_number",
          "value": "0000000000"
        },
        "369": {
          "id": 369,
          "enabled": true,
          "name": "callgroup",
          "value": "techsupport"
        }
      },
      "cache": 5000,
      "cidr": ""
    }
  }
}

```

Get directory user data(except gateways).

##### Event value

`[Users] Get_user_details`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* user not found





#### Add User Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Add_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"index":0,"name":"param1","value":"val1"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Add_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"index":0,"name":"param1","value":"val1"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Add_user_param",
  "user_details": {
    "56": {
      "parameters": {
        "179": {
          "id": 179,
          "enabled": true,
          "name": "param1",
          "value": "val1"
        }
      },
      "cache": 0,
      "cidr": ""
    }
  }
}

```

Add new directory user parameter.

##### Event value

`[Users] Add_user_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 index | Integer | 
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* user not found
* can't add





#### Update User Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Update_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":179,"name":"param1","value":"val2"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Update_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":179,"name":"param1","value":"val2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Update_user_param",
  "user_details": {
    "56": {
      "parameters": {
        "179": {
          "id": 179,
          "enabled": true,
          "name": "param1",
          "value": "val2"
        }
      },
      "cache": 0,
      "cidr": ""
    }
  }
}

```

Changing directory user parameter name or value or both.

##### Event value

`[Users] Update_user_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* parameter not found
* can't update





#### Disable User Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users][Switch] User parameter","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":179,"enabled":false}}'
```
```javascript
exampleSocket.send('{"event":"[Users][Switch] User parameter","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":179,"enabled":false}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users][Switch] User parameter",
  "user_details": {
    "56": {
      "parameters": {
        "179": {
          "id": 179,
          "enabled": false,
          "name": "param1",
          "value": "val2"
        }
      },
      "cache": 0,
      "cidr": ""
    }
  }
}

```

Disable directory user parameter.

##### Event value

`[Users][Switch] User parameter`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 enabled | Boolean | 


##### Errors

* wrong id
* parameter not found
* can't change





#### Delete User Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Del_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":179}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Del_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":179}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Del_user_param",
  "id": 179
}

```

Delete directory user parameter.

##### Event value

`[Users] Del_user_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* parameter not found
* can't change





#### Add User Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Add_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"index":0,"name":"var1","value":"val1"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Add_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"index":0,"name":"var1","value":"val1"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Add_user_var",
  "user_details": {
    "56": {
      "variables": {
        "698": {
          "id": 698,
          "enabled": true,
          "name": "var1",
          "value": "val1"
        }
      },
      "cache": 0,
      "cidr": ""
    }
  }
}

```

Add new directory user variable.

##### Event value

`[Users] Add_user_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 index | Integer | 
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* user not found
* can't add





#### Update User Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Update_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":698,"name":"var1","value":"val2"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Update_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":698,"name":"var1","value":"val2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Update_user_var",
  "user_details": {
    "56": {
      "variables": {
        "698": {
          "id": 698,
          "enabled": true,
          "name": "var1",
          "value": "val2"
        }
      },
      "cache": 0,
      "cidr": ""
    }
  }
}

```

Changing directory user parameter name or value or both.

##### Event value

`[Users] Update_user_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* parameter not found
* can't update





#### Disable User Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users][Switch] User variable","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":698,"enabled":false}}'
```
```javascript
exampleSocket.send('{"event":"[Users][Switch] User variable","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":698,"enabled":false}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users][Switch] User variable",
  "user_details": {
    "56": {
      "variables": {
        "698": {
          "id": 698,
          "enabled": false,
          "name": "var1",
          "value": "val2"
        }
      },
      "cache": 0,
      "cidr": ""
    }
  }
}

```

Delete directory user variable.

##### Event value

`[Users][Switch] User variable`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 enabled | Boolean | 


##### Errors

* wrong id
* variable not found
* can't change





#### Delete User Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Del_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":698}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Del_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":698}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Del_user_var",
  "id": 698
}

```

Delete directory user variable.

##### Event value

`[Users] Del_user_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* variable not found
* can't change





#### Update User Cache

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Update_user_cache","data":{"token":"dd64511448aed2ce2160fc091a79749d","value":"5000","id":56}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Update_user_cache","data":{"token":"dd64511448aed2ce2160fc091a79749d","value":"5000","id":56}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Update_user_cache",
  "item": {
    "id": 56,
    "value": "5000"
  }
}

```

Update directory user cache value.

##### Event value

`[Users] Update_user_cache`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 value | String | 
 id | Integer | Item ID.


##### Errors

* wrong id
* empty data
* wrong data
* can't add





#### Update User Cidr

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Update_user_cidr","data":{"token":"dd64511448aed2ce2160fc091a79749d","value":"127.0.0.01","id":56}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Update_user_cidr","data":{"token":"dd64511448aed2ce2160fc091a79749d","value":"127.0.0.01","id":56}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Update_user_cidr",
  "item": {
    "id": 56,
    "value": "127.0.0.01"
  }
}

```

Update directory user cidr value.

##### Event value

`[Users] Update_user_cidr`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 value | String | 
 id | Integer | Item ID.


##### Errors

* wrong id
* empty data





#### Add User

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Add_new_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","name":"5000","id":8,"bulk":10}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Add_new_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","name":"5000","id":8,"bulk":10}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Add_new_user",
  "directory_users": {
    "8": {
      "105": {
        "id": 105,
        "enabled": true,
        "name": "5000",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "106": {
        "id": 106,
        "enabled": true,
        "name": "5001",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "107": {
        "id": 107,
        "enabled": true,
        "name": "5002",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "108": {
        "id": 108,
        "enabled": true,
        "name": "5003",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "109": {
        "id": 109,
        "enabled": true,
        "name": "5004",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "110": {
        "id": 110,
        "enabled": true,
        "name": "5005",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "111": {
        "id": 111,
        "enabled": true,
        "name": "5006",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "112": {
        "id": 112,
        "enabled": true,
        "name": "5007",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "113": {
        "id": 113,
        "enabled": true,
        "name": "5008",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "114": {
        "id": 114,
        "enabled": true,
        "name": "5009",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      }
    }
  },
  "total": 10
}

```

Add new directory user. Could be add up to 100 at once by <code>bulk</code> parameter new names will be generated sequently..

##### Event value

`[Users] Add_new_user`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 name | String | 
 id | Integer | Item ID.
 bulk | Integer | [Optional]Amount of items.


##### Errors

* wrong id
* empty data
* domain not found
* to many at once





#### Rename User

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Update_user_name","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"name":"1022"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Update_user_name","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"name":"1022"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Update_user_name",
  "item": {
    "id": 56,
    "name": "1022"
  },
  "id": 8
}

```

Change directory user name(id attr).

##### Event value

`[Users] Update_user_name`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* user not found
* empty data
* user not found





#### Delete User

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Del_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Del_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Del_user",
  "item": {
    "id": 56
  },
  "id": 8
}

```

Remove directory user.

##### Event value

`[Users] Del_user`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* user not found
* can't delete user





#### Import User

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"ImportXMLDomainUser","data":{"token":"dd64511448aed2ce2160fc091a79749d","file":"<user id=\"1400\">\r\n    <params>\r\n      <param name=\"password\" value=\"$${default_password}\"/>\r\n      <param name=\"vm-password\" value=\"1000\"/>\r\n    </params>\r\n    <variables>\r\n      <variable name=\"toll_allow\" value=\"domestic,international,local\"/>\r\n      <variable name=\"accountcode\" value=\"1000\"/>\r\n      <variable name=\"user_context\" value=\"default\"/>\r\n      <variable name=\"effective_caller_id_name\" value=\"Extension 1000\"/>\r\n      <variable name=\"effective_caller_id_number\" value=\"1000\"/>\r\n      <variable name=\"outbound_caller_id_name\" value=\"$${outbound_caller_name}\"/>\r\n      <variable name=\"outbound_caller_id_number\" value=\"$${outbound_caller_id}\"/>\r\n      <variable name=\"callgroup\" value=\"techsupport\"/>\r\n    </variables>\r\n  </user>","id":8}}'
```
```javascript
exampleSocket.send('{"event":"ImportXMLDomainUser","data":{"token":"dd64511448aed2ce2160fc091a79749d","file":"<user id=\"1400\">\r\n    <params>\r\n      <param name=\"password\" value=\"$${default_password}\"/>\r\n      <param name=\"vm-password\" value=\"1000\"/>\r\n    </params>\r\n    <variables>\r\n      <variable name=\"toll_allow\" value=\"domestic,international,local\"/>\r\n      <variable name=\"accountcode\" value=\"1000\"/>\r\n      <variable name=\"user_context\" value=\"default\"/>\r\n      <variable name=\"effective_caller_id_name\" value=\"Extension 1000\"/>\r\n      <variable name=\"effective_caller_id_number\" value=\"1000\"/>\r\n      <variable name=\"outbound_caller_id_name\" value=\"$${outbound_caller_name}\"/>\r\n      <variable name=\"outbound_caller_id_number\" value=\"$${outbound_caller_id}\"/>\r\n      <variable name=\"callgroup\" value=\"techsupport\"/>\r\n    </variables>\r\n  </user>","id":8}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "ImportXMLDomainUser",
  "directory_users": {
    "8": {
      "104": {
        "id": 104,
        "enabled": true,
        "name": "4000",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "105": {
        "id": 105,
        "enabled": true,
        "name": "5000",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "106": {
        "id": 106,
        "enabled": true,
        "name": "5001",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "107": {
        "id": 107,
        "enabled": true,
        "name": "5002",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "108": {
        "id": 108,
        "enabled": true,
        "name": "5003",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "109": {
        "id": 109,
        "enabled": true,
        "name": "5004",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "110": {
        "id": 110,
        "enabled": true,
        "name": "5005",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "111": {
        "id": 111,
        "enabled": true,
        "name": "5006",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "112": {
        "id": 112,
        "enabled": true,
        "name": "5007",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "113": {
        "id": 113,
        "enabled": true,
        "name": "5008",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "114": {
        "id": 114,
        "enabled": true,
        "name": "5009",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "115": {
        "id": 115,
        "enabled": true,
        "name": "6000",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "116": {
        "id": 116,
        "enabled": true,
        "name": "1400",
        "cache": 0,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "56": {
        "id": 56,
        "enabled": true,
        "name": "1000",
        "cache": 5000,
        "cidr": "127.0.0.01",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false,
        "cc_agent": 230
      },
      "57": {
        "id": 57,
        "enabled": true,
        "name": "1001",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "58": {
        "id": 58,
        "enabled": true,
        "name": "1002",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "59": {
        "id": 59,
        "enabled": true,
        "name": "1003",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "60": {
        "id": 60,
        "enabled": true,
        "name": "1004",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "61": {
        "id": 61,
        "enabled": true,
        "name": "1005",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "62": {
        "id": 62,
        "enabled": true,
        "name": "1006",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "63": {
        "id": 63,
        "enabled": true,
        "name": "1007",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "64": {
        "id": 64,
        "enabled": true,
        "name": "1008",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "65": {
        "id": 65,
        "enabled": true,
        "name": "1009",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "66": {
        "id": 66,
        "enabled": true,
        "name": "1010",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "67": {
        "id": 67,
        "enabled": true,
        "name": "1011",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "68": {
        "id": 68,
        "enabled": true,
        "name": "1012",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "69": {
        "id": 69,
        "enabled": true,
        "name": "1013",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "70": {
        "id": 70,
        "enabled": true,
        "name": "1014",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "71": {
        "id": 71,
        "enabled": true,
        "name": "1015",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "72": {
        "id": 72,
        "enabled": true,
        "name": "1016",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "73": {
        "id": 73,
        "enabled": true,
        "name": "1017",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "74": {
        "id": 74,
        "enabled": true,
        "name": "1018",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "75": {
        "id": 75,
        "enabled": true,
        "name": "1019",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "76": {
        "id": 76,
        "enabled": true,
        "name": "brian",
        "cache": 5000,
        "cidr": "192.0.2.0/24",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "77": {
        "id": 77,
        "enabled": true,
        "name": "default",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "78": {
        "id": 78,
        "enabled": true,
        "name": "example.com",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      },
      "79": {
        "id": 79,
        "enabled": true,
        "name": "SEP001120AABBCC",
        "cache": 5000,
        "cidr": "",
        "call_date": 0,
        "in_call": false,
        "talking": false,
        "last_uuid": "",
        "call_direction": "",
        "sip_register": false,
        "verto_register": false
      }
    }
  }
}

```

Import directory user from given xml. Cold bi provided many users at once.

##### Event value

`ImportXMLDomainUser`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 file | String | 
 id | Integer | Item ID.


##### Errors

* wrong id
* empty data
* domain not found





#### 

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d ''
```
```javascript
exampleSocket.send('');
```


> Returns JSON structured like this:

```json


```

.

##### Event value

``

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------


##### Errors

### Groups

### Gateways
