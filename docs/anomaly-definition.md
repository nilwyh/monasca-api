# Anomaly Definitions
Operations for working with anomaly definitions.

## Create anomaly Definition
Create an anomaly definition.

### POST /v2.0/anomaly-definitions

#### Headers
* X-Auth-Token (string, required) - Keystone auth token
* Accept (string) - application/json

#### Path Parameters
None.

#### Query Parameters
None.

#### Request Body
Consists of an anomaly definition. An anomaly has the following properties:

* name (string(255), required) - A unique name of the anomaly. Note, the name must be unique.
* description (string(255), optional) -  A description of an anomaly.
* expression (string, required) - An anomaly expression.
* match_by ([string], optional) - The metric dimensions to use to create unique anomalys
* severity (string, optional) - Severity of an anomaly. Must be either `LOW`, `MEDIUM`, `HIGH` or `CRITICAL`. Default is `LOW`.
* anomaly_actions ([string(50)], optional) - Array of notification method IDs that are invoked when the anomaly transitions to the `anomaly` state.
* ok_actions ([string(50)], optional) - Array of notification method IDs that are invoked when the anomaly transitions to the `OK` state.
* undetermined_actions ([string(50)], optional) - Array of notification method IDs that are invoked when the anomaly transitions to the `UNDETERMINED` state.

#### Request Examples
```
POST /v2.0/anomaly-definitions HTTP/1.1
Host: 192.168.10.4:8080
Content-Type: application/json
X-Auth-Token: 2b8882ba2ec44295bf300aecb2caa4f7
Cache-Control: no-cache

{  
   "name":"CPU percentage anomaly",
   "description":"The CPU percent metrics indicate anomaly",
   "expression":"KS(cpu.usage{key1=value1,key2=value2},600,3600)",
   "match_by":[
     "hostname"
   ],
   "severity":"LOW",
   "ok_actions":[  
     "c60ec47e-5038-4bf1-9f95-4046c6e9a759"
   ],
   "anomaly_actions":[  
     "c60ec47e-5038-4bf1-9f95-4046c6e9a759"
   ],
   "undetermined_actions":[  
     "c60ec47e-5038-4bf1-9f95-4046c6e9a759"
   ]
}
```
