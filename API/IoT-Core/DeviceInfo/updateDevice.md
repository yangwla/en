# updateDevice


## Description
Modify Device Details

## Request Method
POST

## Request Address
https://iotcore.jdcloud-api.com/v2/regions/{regionId}/instances/{instanceId}/device/{deviceId}:update

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**instanceId**|String|True| |Instance ID of Device|
|**regionId**|String|True| |Instance Region of Device|
|**deviceId**|String|True| |Device Id|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**model**|String|False| |Device Model|
|**manufacturer**|String|False| |Device Manufacturer|
|**description**|String|False| |Device Description|


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|Name|Type|Description|
|---|---|---|
|**device**|DeviceVO|Equipment Details|
### DeviceVO
|Name|Type|Description|
|---|---|---|
|**deviceId**|String|Device ID|
|**deviceName**|String|Device Name|
|**parentId**|String|Parent Device Id|
|**deviceType**|String|Device Type, identical to product type, 0-Ordinary Device, 1-Gateway, 2-Edge|
|**status**|Integer|Device Status, 0-Nonactivated, 1-Actived and Off-line, 2-Actived and On-line|
|**productKey**|String|Product Key|
|**identifier**|String|Device Identifier|
|**secret**|String|Device Secrete Key|
|**description**|String|Device Description|
|**activatedTime**|Long|Activation Time|
|**lastConnectedTime**|Long|Last Connection Time|
|**createdTime**|Long|Registration Time|
|**updatedTime**|Long|Modification Time|
|**productName**|String|Product Name|
|**model**|String|Device Model|
|**manufacturer**|String|Device Manufacturer|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
