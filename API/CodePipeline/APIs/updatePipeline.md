# updatePipeline


## Description
Update the CodePipeline task

## Request Method
PUT

## Request Address
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline/{uuid}

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**uuid**|String|True| |uuid of CodePipeline Task|
|**regionId**|String|True| |Region ID|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**data**|PipelineParams|False| | |

### PipelineParams
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**name**|String|True| |CodePipeline Name|
|**content**|String|True| |The json Character String Defined by CodePipeline. It supports the method configuration for the user’s directly uploading the json configuration file due to configuration flexibility. So, it isn’t analyzed or reversely analyzed.|
|**method**|String|False| |When the creation method value is CREATE_DEMO, the CodePipeline demo is created|

## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|Name|Type|Description|
|---|---|---|
|**uuid**|String|uuid of CodePipeline Task|
|**result**|Boolean|true if the update succeeded|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
