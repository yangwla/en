# describeNodeGroup


## Description
Search details of a single node group

## Request Method
GET

## Request Address
https://kubernetes.jdcloud-api.com/v1/regions/{regionId}/nodeGroups/{nodeGroupId}

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**nodeGroupId**|String|True| |ID of Node Group|

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
|**nodeGroup**|NodeGroup| |
### NodeGroup
|Name|Type|Description|
|---|---|---|
|**clusterId**|String|Cluster id|
|**nodeGroupId**|String|node group id|
|**name**|String|Name|
|**description**|String|Description|
|**nodeConfig**|NodeConfig|Information of Node|
|**version**|String|Version of node in k8s|
|**nodeNetwork**|NodeNetwork|Network Information of node|
|**currentCount**|Integer|Current Count of node(s)|
|**expectCount**|Integer|Expected Count of node(s)|
|**agId**|String|ag id of node group; instance under this node group can be searched by agid|
|**instanceTemplateId**|String|Instance Template Corresponding to ag id of node group|
|**state**|String|Status  [pending,running,resizing,reconciling,deleting,deleted,error,running_with_error(There are problems in some nodes)]|
|**updateTime**|String|Update Time|
|**stateMessage**|String|Status Change Reason|
|**autoRepair**|String|Whether to enable automatic repair|
|**createdTime**|String|Creation Time|
### NodeNetwork
|Name|Type|Description|
|---|---|---|
|**podSubnetId**|String|id of Pod Subnet|
|**nodeSubnetId**|String|id of node Subnet|
|**serviceSubnetId**|String|id of service Subnet|
|**servicePublicSubnetId**|String|Subnet id with public network access capacity for service associated LB|
|**nodeNetworkCidr**|String|cidr of node|
|**vpcId**|String|vpc id|
### NodeConfig
|Name|Type|Description|
|---|---|---|
|**instanceType**|String|Instance Type Family|
|**imageId**|String|Image Information|
|**systemDiskSize**|Integer|System disk size of cloud disk  unit (GB)|
|**systemDiskType**|String|System disk size of cloud disk [ssd,premium-hdd]|
|**labels**|LabelSpec[]|Information of Node|
### LabelSpec
|Name|Type|Description|
|---|---|---|
|**key**|String|key consists of two parts: prefix and name, name is compulsory while prefix is optional. prefix is separated from name with "/”. <br>name can use letters, figures and [-_.]. The length shall be less than 63. prefix: Follow DNS standard (For example: kubernetes.io/) and the length cannot exceed 253 <br>[Reference](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#syntax-and-character-set)    <br>|
|**value**|String|letters, figures, [-_.], and the length cannot exceed 63|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**429**|Quota exceeded|
|**500**|Internal server error|
|**503**|Service unavailable|
