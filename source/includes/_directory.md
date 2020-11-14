
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

Disable/enable directory domain.

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
	 -d '{"event":"[Domains] New_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"name":"param1","value":"value1"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] New_domain_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"name":"param1","value":"value1"}}');
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

Disable/enable directory domain parameter.

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
	 -d '{"event":"[Domains] New_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"name":"var1","value":"value1"}}'
```
```javascript
exampleSocket.send('{"event":"[Domains] New_domain_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"name":"var1","value":"value1"}}');
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

Disable/enable directory domain variable.

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
    "117": {
      "parameters": {
        "182": {
          "id": 182,
          "enabled": true,
          "name": "password",
          "value": "5555"
        },
        "183": {
          "id": 183,
          "enabled": true,
          "name": "vm-password",
          "value": "1000"
        },
        "270": {
          "id": 270,
          "enabled": true,
          "name": "xc",
          "value": "xc"
        }
      },
      "variables": {
        "1043": {
          "id": 1043,
          "enabled": true,
          "name": "recog",
          "value": "true"
        },
        "707": {
          "id": 707,
          "enabled": true,
          "name": "toll_allow",
          "value": "domestic,international,local"
        },
        "708": {
          "id": 708,
          "enabled": true,
          "name": "accountcode",
          "value": "1000"
        },
        "709": {
          "id": 709,
          "enabled": true,
          "name": "user_context",
          "value": "default"
        },
        "710": {
          "id": 710,
          "enabled": true,
          "name": "effective_caller_id_name",
          "value": "Extension 1000"
        },
        "711": {
          "id": 711,
          "enabled": true,
          "name": "effective_caller_id_number",
          "value": "1000"
        },
        "712": {
          "id": 712,
          "enabled": true,
          "name": "outbound_caller_id_name",
          "value": "FreeSWITCH"
        },
        "713": {
          "id": 713,
          "enabled": true,
          "name": "outbound_caller_id_number",
          "value": "0000000000"
        },
        "714": {
          "id": 714,
          "enabled": true,
          "name": "callgroup",
          "value": "techsupport"
        }
      },
      "cache": 5000,
      "cidr": "333",
      "number_alias": ""
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
	 -d '{"event":"[Users] Add_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"name":"param1","value":"val1"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Add_user_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"name":"param1","value":"val1"}}');
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

Disable/enable directory user parameter.

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
	 -d '{"event":"[Users] Add_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"name":"var1","value":"val1"}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Add_user_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":56,"name":"var1","value":"val1"}}');
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

Disable/enable directory user variable.

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




#### Update User Number Alias

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Users] Update_user_number_alias","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","value":"user1","id":117}}'
```
```javascript
exampleSocket.send('{"event":"[Users] Update_user_number_alias","data":{"token":"185f2b5b4dbf7a456e6d6f9cb62805cb","value":"user1","id":117}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Users] Update_user_number_alias",
  "item": {
    "id": 117,
    "value": "user1"
  }
}

```

Update directory user number alias value.

##### Event value

`[Users] Update_user_number_alias`

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



### Groups



#### Get Groups

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Get_groups","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Get_groups","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Get_groups",
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
  "list": {
    "8": {
      "10": "default",
      "11": "sales",
      "12": "billing",
      "13": "support"
    },
    "9": {
      "14": "default",
      "15": "sales",
      "16": "billing",
      "17": "support"
    }
  }
}

```

Get directory groups.

##### Event value

`[Groups] Get_groups`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.


##### Errors





#### Get Group Users

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Get_group_users","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":10}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Get_group_users","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":10}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Get_group_users",
  "list": {
    "8": {
      "104": "4000",
      "105": "5000",
      "106": "5001",
      "107": "5002",
      "108": "5003",
      "109": "5004",
      "110": "5005",
      "111": "5006",
      "112": "5007",
      "113": "5008",
      "114": "5009",
      "115": "6000",
      "116": "1400",
      "57": "1001",
      "58": "1002",
      "59": "1003",
      "60": "1004",
      "61": "1005",
      "62": "1006",
      "63": "1007",
      "64": "1008",
      "65": "1009",
      "66": "1010",
      "67": "1011",
      "68": "1012",
      "69": "1013",
      "70": "1014",
      "71": "1015",
      "72": "1016",
      "73": "1017",
      "74": "1018",
      "75": "1019",
      "76": "brian",
      "77": "default",
      "78": "example.com",
      "79": "SEP001120AABBCC"
    }
  },
  "group_users": {
    "10": {
      "92": {
        "id": 92,
        "enabled": true,
        "user_id": 104,
        "name": "4000",
        "type": "pointer"
      },
      "93": {
        "id": 93,
        "enabled": true,
        "user_id": 107,
        "name": "5002",
        "type": "pointer"
      }
    }
  }
}

```

Get list of members of group and list of possible members.

##### Event value

`[Groups] Get_group_users`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* group not found




#### Add Group

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Add_new_group","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"name":"new-group"}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Add_new_group","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":8,"name":"new-group"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Add_new_group",
  "items": {
    "18": "new-group"
  },
  "id": 8
}

```

Add new directory group.

##### Event value

`[Groups] Add_new_group`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* wrong id
* empty data
* domain not found




#### Rename Group

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Update_group_name","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":18,"name":"new-group2"}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Update_group_name","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":18,"name":"new-group2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Update_group_name",
  "item": {
    "id": 18,
    "name": "new-group2"
  },
  "id": 8
}

```

Change directory group name.

##### Event value

`[Groups] Update_group_name`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* group not found
* empty data
* group not found




#### Delete Group

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Del_group","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":18}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Del_group","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":18}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Del_group",
  "item": {
    "id": 18
  },
  "id": 8
}

```

Delete directory group.

##### Event value

`[Groups] Del_group`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* group not found
* can't delete group




#### Add User to Group

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Add_group_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","value":"57","id":10}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Add_group_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","value":"57","id":10}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Add_group_user",
  "group_users": {
    "10": {
      "94": {
        "id": 94,
        "enabled": true,
        "user_id": 57,
        "name": "1001",
        "type": "pointer"
      }
    }
  },
  "id": 10
}

```

Add directory user to directory group.

##### Event value

`[Groups] Add_group_user`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 value | String | 
 id | Integer | Item ID.


##### Errors

* wrong group id
* wrong user id
* group not found
* user not found




#### Remove User From Group

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Groups] Del_group_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":94}}'
```
```javascript
exampleSocket.send('{"event":"[Groups] Del_group_user","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":94}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Groups] Del_group_user",
  "id": 10,
  "affected_id": 94
}

```

Delete directory user from directory group.

##### Event value

`[Groups] Del_group_user`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* user not found



### Gateways



#### Get User's Gateway

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Get_users_gateways","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Get_users_gateways","data":{"token":"dd64511448aed2ce2160fc091a79749d"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Get_users_gateways",
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
      "104": {
        "id": 104,
        "enabled": true,
        "name": "4000",
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
      "105": {
        "id": 105,
        "enabled": true,
        "name": "5000",
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
      "106": {
        "id": 106,
        "enabled": true,
        "name": "5001",
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
      "107": {
        "id": 107,
        "enabled": true,
        "name": "5002",
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
      "108": {
        "id": 108,
        "enabled": true,
        "name": "5003",
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
      "109": {
        "id": 109,
        "enabled": true,
        "name": "5004",
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
      "110": {
        "id": 110,
        "enabled": true,
        "name": "5005",
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
      "111": {
        "id": 111,
        "enabled": true,
        "name": "5006",
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
      "112": {
        "id": 112,
        "enabled": true,
        "name": "5007",
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
      "113": {
        "id": 113,
        "enabled": true,
        "name": "5008",
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
      "114": {
        "id": 114,
        "enabled": true,
        "name": "5009",
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
      "115": {
        "id": 115,
        "enabled": true,
        "name": "6000",
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
      "116": {
        "id": 116,
        "enabled": true,
        "name": "1400",
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
      }
    }
  },
  "user_gateways": {
    "8": {
      "78": {
        "4": {
          "id": 4,
          "enabled": true,
          "name": "example.com"
        }
      }
    },
    "9": {
      "102": {
        "5": {
          "id": 5,
          "enabled": true,
          "name": "example.com"
        }
      }
    }
  }
}

```

Get list of directory user's gateways.

##### Event value

`[Gateways] Get_users_gateways`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.


##### Errors





#### Add User's Gateway

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Add_new_user_gateway","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":57,"name":"new"}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Add_new_user_gateway","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":57,"name":"new"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Add_new_user_gateway",
  "item": {
    "id": 6,
    "name": "new"
  },
  "id": 8,
  "affected_id": 57
}

```

Add directory user's gateway.

##### Event value

`[Gateways] Add_new_user_gateway`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* wrong id
* empty data
* domain not found




#### Rename User's Gateway

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Update_user_gateway_name","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":6,"name":"new2"}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Update_user_gateway_name","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":6,"name":"new2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Update_user_gateway_name",
  "item": {
    "id": 6,
    "name": "new2"
  },
  "id": 8,
  "affected_id": 57
}

```

Change directory user gateway name.

##### Event value

`[Gateways] Update_user_gateway_name`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 name | String | 


##### Errors

* gateway not found
* empty data
* gateway not found




#### Delete User's Gateway

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Del_user_gateway","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":6}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Del_user_gateway","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":6}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Del_user_gateway",
  "item": {
    "id": 6
  },
  "id": 8,
  "affected_id": 57
}

```

Delete directory user gateway.

##### Event value

`[Gateways] Del_user_gateway`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* gateway not found
* can't delete gateway




#### Get User's Gateway Details

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Get_user_gateways_details","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":4}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Get_user_gateways_details","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":4}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Get_user_gateways_details",
  "gateway_details": {
    "4": {
      "parameters": {
        "25": {
          "id": 25,
          "enabled": true,
          "name": "username",
          "value": "joeuser"
        },
        "26": {
          "id": 26,
          "enabled": true,
          "name": "password",
          "value": "jbjvh3h2y3ug3i2h2u3pi32ug3oi3iu3gpu22iu"
        },
        "27": {
          "id": 27,
          "enabled": true,
          "name": "from-user",
          "value": "joeuser"
        },
        "28": {
          "id": 28,
          "enabled": true,
          "name": "from-domain",
          "value": "example.com"
        },
        "29": {
          "id": 29,
          "enabled": true,
          "name": "expire-seconds",
          "value": "600"
        },
        "30": {
          "id": 30,
          "enabled": true,
          "name": "register",
          "value": "false"
        },
        "31": {
          "id": 31,
          "enabled": true,
          "name": "retry-seconds",
          "value": "30"
        },
        "32": {
          "id": 32,
          "enabled": true,
          "name": "extension",
          "value": "5000"
        },
        "33": {
          "id": 33,
          "enabled": true,
          "name": "context",
          "value": "public"
        }
      }
    }
  }
}

```

Get list of users gateway parameters and variables.

##### Event value

`[Gateways] Get_user_gateways_details`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* gateway not found




#### Add User's Gateway Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Add_user_gateway_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":4,"name":"param1","value":"val1"}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Add_user_gateway_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":4,"name":"param1","value":"val1"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Add_user_gateway_param",
  "item": {
    "id": 48,
    "name": "param1",
    "value": "val1",
    "enabled": true
  }
}

```

Add new directory user's gateway parameter.

##### Event value

`[Gateways] Add_user_gateway_param`

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
* user gateway not found
* can't add




#### Update User's Gateway Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Update_user_gateway_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":48,"name":"param1","value":"val2"}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Update_user_gateway_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":48,"name":"param1","value":"val2"}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Update_user_gateway_param",
  "gateway_details": {
    "4": {
      "parameters": {
        "48": {
          "id": 48,
          "enabled": true,
          "name": "param1",
          "value": "val2"
        }
      }
    }
  }
}

```

Update directory user gateway parameter name or value or both.

##### Event value

`[Gateways] Update_user_gateway_param`

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




#### Disable User's Gateway Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways][Switch] Param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":48,"enabled":false}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways][Switch] Param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":48,"enabled":false}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways][Switch] Param",
  "gateway_details": {
    "4": {
      "parameters": {
        "48": {
          "id": 48,
          "enabled": false,
          "name": "param1",
          "value": "val2"
        }
      }
    }
  }
}

```

Disable/enable directory user's gateway parameter.

##### Event value

`[Gateways][Switch] Param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 enabled | Boolean | 


##### Errors

* no id
* parameter not found
* empty data
* can't change




#### Delete User's Gateway Parameter

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Del_user_gateway_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":48}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Del_user_gateway_param","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":48}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Del_user_gateway_param",
  "id": 48
}

```

Delete directory user's gateway parameter.

##### Event value

`[Gateways] Del_user_gateway_param`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.


##### Errors

* wrong id
* can't delete




#### Add User's Gateway Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Add_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":4,"index":0,"variable":{"enabled":true,"name":"var1","value":"val1"}}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Add_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","id":4,"index":0,"variable":{"enabled":true,"name":"var1","value":"val1"}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Add_user_gateway_var",
  "gateway_details": {
    "4": {
      "variables": {
        "1": {
          "id": 1,
          "enabled": true,
          "name": "var1",
          "value": "val1",
          "direction": ""
        }
      }
    }
  }
}

```

Add directory user gateway variable.

##### Event value

`[Gateways] Add_user_gateway_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 id | Integer | Item ID.
 index | Integer | 
 variable":{"enabled | Boolean | 
 name | String | 
 value | String | 


##### Errors

* wrong id
* empty data
* gateway not found




#### Update User's Gateway Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Update_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","variable":{"id":1,"enabled":true,"name":"var1","value":"val1","direction":"inbound"}}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Update_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","variable":{"id":1,"enabled":true,"name":"var1","value":"val1","direction":"inbound"}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Update_user_gateway_var",
  "gateway_details": {
    "4": {
      "variables": {
        "1": {
          "id": 1,
          "enabled": true,
          "name": "var1",
          "value": "val1",
          "direction": "inbound"
        }
      }
    }
  }
}

```

Update directory user gateway variable name or value or direction or all three.

##### Event value

`[Gateways] Update_user_gateway_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 variable":{"id | Integer | 
 enabled | Boolean | 
 name | String | 
 value | String | 
 direction | String | 


##### Errors

* empty data
* variable not found
* can't update




#### Disable User's Gateway Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Switch_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","variable":{"id":1,"enabled":false,"name":"var1","value":"val1","direction":"inbound"}}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Switch_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","variable":{"id":1,"enabled":false,"name":"var1","value":"val1","direction":"inbound"}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Switch_user_gateway_var",
  "gateway_details": {
    "4": {
      "variables": {
        "1": {
          "id": 1,
          "enabled": false,
          "name": "var1",
          "value": "val1",
          "direction": "inbound"
        }
      }
    }
  }
}

```

Disable/enable directory user's gateway variable.

##### Event value

`[Gateways] Switch_user_gateway_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 variable":{"id | Integer | 
 enabled | Boolean | 
 name | String | 
 value | String | 
 direction | String | 


##### Errors

* empty data
* variable not found
* can't change




#### Delete User's Gateway Variable

```shell
curl -X POST "https://HOST:PORT/api/v1"
	 -d '{"event":"[Gateways] Del_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","variable":{"id":1,"enabled":false,"name":"var1","value":"val1","direction":"inbound"}}}'
```
```javascript
exampleSocket.send('{"event":"[Gateways] Del_user_gateway_var","data":{"token":"dd64511448aed2ce2160fc091a79749d","variable":{"id":1,"enabled":false,"name":"var1","value":"val1","direction":"inbound"}}}');
```


> Returns JSON structured like this:

```json
{
  "MessageType": "[Gateways] Del_user_gateway_var",
  "gateway_details": {
    "4": {
      "variables": {
        "1": {
          "id": 1,
          "enabled": false,
          "name": "var1",
          "value": "val1",
          "direction": "inbound"
        }
      }
    }
  }
}

```

Delete directory user's gateway variable.

##### Event value

`[Gateways] Del_user_gateway_var`

##### Data Parameters

Parameter | Type | Description
--------- | ------- | -----------
 token | String | User auth token.
 variable":{"id | Integer | 
 enabled | Boolean | 
 name | String | 
 value | String | 
 direction | String | 


##### Errors

* empty data
* variable not found
* can't delete


