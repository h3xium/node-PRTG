 [![npm version](https://img.shields.io/npm/v/node-prtg.svg)](https://www.npmjs.com/package/node-prtg) [![npm downloads](https://img.shields.io/npm/dt/node-prtg.svg)](https://www.npmjs.com/package/node-prtg) [![Build Status](https://travis-ci.org/covenanttechnologysolutions/node-PRTG.svg?branch=master)](https://travis-ci.org/covenanttechnologysolutions/node-PRTG) [![Coverage Status](https://coveralls.io/repos/github/covenanttechnologysolutions/node-PRTG/badge.svg?branch=master)](https://coveralls.io/github/covenanttechnologysolutions/node-PRTG?branch=master)

# node-prtg
A Node.js module for interacting with the PRTG API. 

## Requirements

- PRTG 14.x+, earlier versions may work but have not been tested. 
- Node.js v6+

## Usage

```javascript

    const PRTG = require('node-prtg');
    
    const api = new PRTG({
            url: 'http://your.prtg.install.com',
            username: 'username',
            passhash: '123456789'
    });
    
    api.getSensor(1234)
      .then(sensor => { /*do something with result*/ }).catch(error => { /* handle errors */ });
```

## Classes

<dl>
<dt><a href="#PRTG">PRTG</a></dt>
<dd></dd>
</dl>

## Typedefs

<dl>
<dt><a href="#PRTGFilter">PRTGFilter</a> : <code>object</code></dt>
<dd></dd>
<dt><a href="#Sensor">Sensor</a> : <code>object</code></dt>
<dd></dd>
<dt><a href="#SensorColumns">SensorColumns</a> : <code>object</code></dt>
<dd></dd>
</dl>

<a name="PRTG"></a>

## PRTG
**Kind**: global class  

* [PRTG](#PRTG)
    * [new PRTG(options)](#new_PRTG_new)
    * [.getDefaults()](#PRTG+getDefaults) ⇒ <code>Object</code> \| <code>\*</code>
    * [.getStatus(str)](#PRTG+getStatus) ⇒ <code>string</code> \| <code>number</code>
    * [.api(path, query, [resultPath], [parse], [enableSanitize])](#PRTG+api) ⇒ <code>Promise</code> \| <code>object</code>
    * [.getSensor(objid)](#PRTG+getSensor) ⇒ [<code>Promise.&lt;Sensor&gt;</code>](#Sensor)
    * [.getDeviceSensors(objid, [columns])](#PRTG+getDeviceSensors) ⇒ <code>Promise.&lt;Array.&lt;Sensor&gt;&gt;</code>
    * [.getObjectProperty(objid, property)](#PRTG+getObjectProperty) ⇒ <code>Promise.&lt;Object&gt;</code>
    * [.getSensorStatusId(objid)](#PRTG+getSensorStatusId) ⇒ <code>Promise.&lt;String&gt;</code>
    * [.getDeviceStatusId(objid)](#PRTG+getDeviceStatusId) ⇒ <code>Promise.&lt;String&gt;</code>
    * [.getSensors([columns], [filter], [objid])](#PRTG+getSensors) ⇒ <code>Promise.&lt;Array.&lt;Sensor&gt;&gt;</code>
    * [.getDownOrAckSensors()](#PRTG+getDownOrAckSensors) ⇒ <code>Promise.&lt;Array.&lt;Sensor&gt;&gt;</code>
    * [.getSensorTree()](#PRTG+getSensorTree) ⇒ <code>Promise.&lt;Object&gt;</code>
    * [.pauseSensor(objectId, message)](#PRTG+pauseSensor) ⇒ <code>Promise</code> \| <code>Object</code>
    * [.resumeSensor(objectId)](#PRTG+resumeSensor) ⇒ <code>Promise</code> \| <code>Object</code>
    * [.pauseSensorDuration(objectId, message, minutes)](#PRTG+pauseSensorDuration) ⇒ <code>Promise</code> \| <code>Object</code>
    * [.acknowledgeSensor(objectId, message)](#PRTG+acknowledgeSensor) ⇒ <code>Promise</code> \| <code>Object</code>
    * [.acknowledgeSensorDuration(objectId, message, minutes)](#PRTG+acknowledgeSensorDuration) ⇒ <code>Promise</code> \| <code>Object</code>

<a name="new_PRTG_new"></a>

### new PRTG(options)

| Param | Description |
| --- | --- |
| options |  |
| options.username |  |
| options.passhash |  |
| options.url | Base URL of your PRTG installation, e.g. the API is accessible at <url>/API/ |

<a name="PRTG+getDefaults"></a>

### prtG.getDefaults() ⇒ <code>Object</code> \| <code>\*</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  
<a name="PRTG+getStatus"></a>

### prtG.getStatus(str) ⇒ <code>string</code> \| <code>number</code>
Return opposite mapping for status to status id

**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| str | 

<a name="PRTG+api"></a>

### prtG.api(path, query, [resultPath], [parse], [enableSanitize]) ⇒ <code>Promise</code> \| <code>object</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>string</code> |  |
| query | <code>object</code> |  |
| [resultPath] | <code>string</code> \| <code>Array.&lt;string&gt;</code> | See https://lodash.com/docs#get |
| [parse] | <code>function</code> | parse function that uses signature of fn(string, callback) with callback of fn(err, result) |
| [enableSanitize] | <code>boolean</code> | enable regex to replace invalid characters |

<a name="PRTG+getSensor"></a>

### prtG.getSensor(objid) ⇒ [<code>Promise.&lt;Sensor&gt;</code>](#Sensor)
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param | Description |
| --- | --- |
| objid | sensor's ID |

<a name="PRTG+getDeviceSensors"></a>

### prtG.getDeviceSensors(objid, [columns]) ⇒ <code>Promise.&lt;Array.&lt;Sensor&gt;&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param | Type | Description |
| --- | --- | --- |
| objid |  |  |
| [columns] | <code>string</code> \| <code>Array.&lt;string&gt;</code> | Defaults to 'objid,probe,group,device,sensor,lastvalue,type,name,tags,active,status,grpdev,message' |

<a name="PRTG+getObjectProperty"></a>

### prtG.getObjectProperty(objid, property) ⇒ <code>Promise.&lt;Object&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objid | 
| property | 

<a name="PRTG+getSensorStatusId"></a>

### prtG.getSensorStatusId(objid) ⇒ <code>Promise.&lt;String&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objid | 

<a name="PRTG+getDeviceStatusId"></a>

### prtG.getDeviceStatusId(objid) ⇒ <code>Promise.&lt;String&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objid | 

<a name="PRTG+getSensors"></a>

### prtG.getSensors([columns], [filter], [objid]) ⇒ <code>Promise.&lt;Array.&lt;Sensor&gt;&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param | Type | Description |
| --- | --- | --- |
| [columns] |  |  |
| [filter] | [<code>PRTGFilter</code>](#PRTGFilter) |  |
| [objid] | <code>string</code> \| <code>number</code> | filter set to this object (device/group/probe) |

<a name="PRTG+getDownOrAckSensors"></a>

### prtG.getDownOrAckSensors() ⇒ <code>Promise.&lt;Array.&lt;Sensor&gt;&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  
<a name="PRTG+getSensorTree"></a>

### prtG.getSensorTree() ⇒ <code>Promise.&lt;Object&gt;</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  
<a name="PRTG+pauseSensor"></a>

### prtG.pauseSensor(objectId, message) ⇒ <code>Promise</code> \| <code>Object</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objectId | 
| message | 

<a name="PRTG+resumeSensor"></a>

### prtG.resumeSensor(objectId) ⇒ <code>Promise</code> \| <code>Object</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objectId | 

<a name="PRTG+pauseSensorDuration"></a>

### prtG.pauseSensorDuration(objectId, message, minutes) ⇒ <code>Promise</code> \| <code>Object</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objectId | 
| message | 
| minutes | 

<a name="PRTG+acknowledgeSensor"></a>

### prtG.acknowledgeSensor(objectId, message) ⇒ <code>Promise</code> \| <code>Object</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objectId | 
| message | 

<a name="PRTG+acknowledgeSensorDuration"></a>

### prtG.acknowledgeSensorDuration(objectId, message, minutes) ⇒ <code>Promise</code> \| <code>Object</code>
**Kind**: instance method of [<code>PRTG</code>](#PRTG)  

| Param |
| --- |
| objectId | 
| message | 
| minutes | 

<a name="PRTGFilter"></a>

## PRTGFilter : <code>object</code>
**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| [filter_drel] | <code>string</code> | Only include records younger than this setting (for content='messages' and content='tickets' only).                                          Possible values: today, yesterday, 7days, 30days, 12months, forever |
| [filter_status] | <code>Array.&lt;string&gt;</code> \| <code>string</code> | Only include sensors with a specific status (for content='sensors' only). Using multiple filter_status fields performs a logical OR.                              See types PRTG.DEFAULTS.status. |
| [filter_tags] | <code>Array.&lt;string&gt;</code> \| <code>string</code> | Only include sensors with a specific tag (for content="sensors" only).                                          Using multiple filter_tag fields performs a logical OR.                                          Possible values: @tag(tagname) |
| [filter_xyz] | <code>string</code> \| <code>Array.&lt;string&gt;</code> | filter_xyz where xyz is any column name used in the columns parameter;                                          Substrings: use filter_xyz=@sub(substring1,substring2);                                          Values not equal/above/below: use filter_xyz=@neq(value), filter_xyz=@above(value), filter_xyz=@below(value) |
| [sortby] | <code>string</code> | Sorts the data.  If this parameter is omitted, the table will be sorted based on the first column.  Add a leading '-' to reverse.                                          Possible values: any column name used in the columns parameter.  (sortby=name, sortby=lastvalue, sortby=-lastvalue) |

<a name="Sensor"></a>

## Sensor : <code>object</code>
**Kind**: global typedef  
**Properties**

| Name | Type |
| --- | --- |
| name | <code>string</code> | 
| sensortype | <code>string</code> | 
| interval | <code>string</code> | 
| probename | <code>string</code> | 
| probegroupname | <code>string</code> | 
| parentdevicename | <code>string</code> | 
| parentdeviceid | <code>string</code> | 
| lastvalue | <code>string</code> | 
| lastmessage | <code>string</code> | 
| favorite | <code>string</code> | 
| statustext | <code>string</code> | 
| statusid | <code>string</code> | 
| lastup | <code>string</code> | 
| lastdown | <code>string</code> | 
| lastcheck | <code>string</code> | 
| uptime | <code>string</code> | 
| uptimetime | <code>string</code> | 
| downtime | <code>string</code> | 
| downtimetime | <code>string</code> | 
| updowntotal | <code>string</code> | 
| updownsince | <code>string</code> | 

<a name="SensorColumns"></a>

## SensorColumns : <code>object</code>
**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| objid | <code>number</code> |  |
| type | <code>string</code> |  |
| name | <code>string</code> |  |
| tags |  |  |
| active |  |  |
| downtime |  |  |
| downtimetime |  |  |
| downtimesince |  |  |
| uptime |  |  |
| uptimetime |  |  |
| uptimesince |  |  |
| knowntime |  |  |
| cumsince |  |  |
| sensor |  |  |
| interval |  |  |
| lastcheck |  |  |
| lastup |  |  |
| lastdown |  |  |
| device |  |  |
| group |  |  |
| probe |  |  |
| grpdev |  |  |
| notifiesx |  |  |
| intervalx |  |  |
| access |  |  |
| dependency |  |  |
| probegroupdevice |  |  |
| status |  |  |
| message |  |  |
| priority |  |  |
| lastvalue |  |  |
| upsens |  |  |
| downsens |  |  |
| partialdownsens |  |  |
| warnsens |  |  |
| pausedsens |  |  |
| unusualsens |  |  |
| undefinedsens |  |  |
| totalsens |  |  |
| favorite |  |  |
| minigraph |  |  |
| comments |  |  |
| basetype |  | ?? |
| baselink |  | ?? |
| parentid |  | ?? |

