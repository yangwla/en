# queryHttpHeader


## Description
Search http header

## Request Method
GET

## Request Address
https://cdn.jdcloud-api.com/v1/domain/{domain}/httpHeader

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**domain**|String|True| |User Domain|

## Request Parameter
None


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|Name|Type|Description|
|---|---|---|
|**domain**|String| |
|**headers**|QueryHttpHeaderResp[]| |
### QueryHttpHeaderResp
|Name|Type|Description|
|---|---|---|
|**headerType**|String| |
|**headerName**|String| |
|**headerValue**|String| |
|**headerOp**|String| |

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
