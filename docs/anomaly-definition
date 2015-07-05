# Alarm Definitions
Operations for working with alarm definitions.

## Create Alarm Definition
Create an alarm definition.

### POST /v2.0/alarm-definitions

#### Headers
* X-Auth-Token (string, required) - Keystone auth token
* Accept (string) - application/json

#### Path Parameters
None.

#### Query Parameters
None.

#### Request Body
Consists of an alarm definition. An alarm has the following properties:

* name (string(255), required) - A unique name of the alarm. Note, the name must be unique.
* description (string(255), optional) -  A description of an alarm.
* expression (string, required) - An alarm expression.
* match_by ([string], optional) - The metric dimensions to use to create unique alarms
* severity (string, optional) - Severity of an alarm. Must be either `LOW`, `MEDIUM`, `HIGH` or `CRITICAL`. Default is `LOW`.
* alarm_actions ([string(50)], optional) - Array of notification method IDs that are invoked when the alarm transitions to the `ALARM` state.
* ok_actions ([string(50)], optional) - Array of notification method IDs that are invoked when the alarm transitions to the `OK` state.
* undetermined_actions ([string(50)], optional) - Array of notification method IDs that are invoked when the alarm transitions to the `UNDETERMINED` state.

#### Request Examples
```
POST /v2.0/alarm-definitions HTTP/1.1
Host: 192.168.10.4:8080
Content-Type: application/json
X-Auth-Token: 2b8882ba2ec44295bf300aecb2caa4f7
Cache-Control: no-cache

{  
   "name":"Average CPU percent greater than 10",
   "description":"The average CPU percent is greater than 10",
   "expression":"(avg(cpu,user_perc{hostname=devstack}) > 10)",
   "match_by":[
     "hostname"
   ],
   "severity":"LOW",
   "ok_actions":[  
     "c60ec47e-5038-4bf1-9f95-4046c6e9a759"
   ],
   "alarm_actions":[  
     "c60ec47e-5038-4bf1-9f95-4046c6e9a759"
   ],
   "undetermined_actions":[  
     "c60ec47e-5038-4bf1-9f95-4046c6e9a759"
   ]
}
```
