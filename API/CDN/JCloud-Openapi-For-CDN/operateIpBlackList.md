# operateIpBlackList


## Description
Set ip blacklist status

## Request Method
PUT

## Request Address
https://cdn.jdcloud-api.com/v1/domain/{domain}/ipBlackList:operate

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**domain**|String|True| |User Domain|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**status**|String|False| |ip Blacklist Status Value [on,off]|


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
