# modifyInstanceDiskAttribute


## Description
Modify the attributes of the data disks attached to the VM, including whether to delete data disk with the VM.


## Request method
POST

## Request address
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceDiskAttribute

|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**instanceId**|String|True| |VM ID|

## Request parameter
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**dataDisks**|InstanceDiskAttribute[]|False| |Cloud Disk List|

### InstanceDiskAttribute
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**diskId**|String|False| |Cloud Disk ID|
|**autoDelete**|Boolean|False| |Delete this disk with the VM automatically when the machine is deleted. The default value is false, which cannot be changed by local.<br>This parameter does not take effect if the billing methond of the data disk in the VM is a monthly package.<br>This parameter does not take effect if the data disk in the VM is a shared data disk.<br>|

## Response parameter
None


## Response code
|Return code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
