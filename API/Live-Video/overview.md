# Live-Video


## Introduction
Related APIs of Live Video


### Version
v1


## API
|Interface name|Request mehod|Function description|
|---|---|---|
|**addCustomLiveStreamRecordTemplate**|POST|Add live record template|
|**addCustomLiveStreamSnapshotTemplate**|POST|Add live snapshot template|
|**addCustomLiveStreamTranscodeTemplate**|POST|Add customized transcoding template|
|**addCustomLiveStreamWatermarkTemplate**|POST|Add live watermark template|
|**addLiveApp**|POST|Add live APP|
|**addLiveDomain**|POST|Add live domain|
|**addLiveRecordTask**|POST|Add recording point print task</br>  \- You can call this interface to accurately extract the part you need in the recorded file</br>|
|**addLiveRestartDomain**|PUT|Add restart domain|
|**addLiveStreamAppRecord**|POST|Add APP record configuration|
|**addLiveStreamAppSnapshot**|POST|Add APP live snapshot configuration|
|**addLiveStreamAppTranscode**|POST|Add APP transcoding configuration|
|**addLiveStreamAppWatermark**|POST|Add APP watermark configuration|
|**addLiveStreamDomainRecord**|POST|Add domain record configuration|
|**addLiveStreamDomainSnapshot**|POST|Add domain live snapshot configuration|
|**addLiveStreamDomainTranscode**|POST|Add domain transcoding configuration|
|**addLiveStreamDomainWatermark**|POST|Add domain watermark configuration|
|**closeLiveRestart**|PUT|Close restart|
|**closeLiveTimeshift**|PUT|Close timeshift|
|**deleteCustomLiveStreamRecordTemplate**|DELETE|Delete user customized record template|
|**deleteCustomLiveStreamSnapshotTemplate**|DELETE|Delete user customized live snapshot template|
|**deleteCustomLiveStreamTranscodeTemplate**|DELETE|Delete user customized transcoding template|
|**deleteCustomLiveStreamWatermarkTemplate**|DELETE|Delete user customized watermark template|
|**deleteLiveApp**|DELETE|Delete APP|
|**deleteLiveDomain**|DELETE|Delete live domain|
|**deleteLiveStreamAppRecord**|DELETE|Delete APP record configuration|
|**deleteLiveStreamAppSnapshot**|DELETE|Delete APP snapshot configuration|
|**deleteLiveStreamAppTranscode**|DELETE|Delete APP transcoding configuration|
|**deleteLiveStreamAppWatermark**|DELETE|Delete APP watermark configuration|
|**deleteLiveStreamDomainRecord**|DELETE|Delete domain record configuration|
|**deleteLiveStreamDomainSnapshot**|DELETE|Delete domain snapshot configuration|
|**deleteLiveStreamDomainTranscode**|DELETE|Delete domain transcoding configuration|
|**deleteLiveStreamDomainWatermark**|DELETE|Delete domain watermark configuration|
|**deleteLiveStreamNotifyConfig**|DELETE|Delete live streaming status notification|
|**deleteLiveStreamRecordNotifyConfig**|DELETE|Delete record callback configuration|
|**deleteLiveStreamSnapshotNotifyConfig**|DELETE|Delete snapshot callback configuration|
|**describeCustomLiveStreamRecordConfig**|GET|Search record configuration|
|**describeCustomLiveStreamRecordTemplates**|GET|Search record template list|
|**describeCustomLiveStreamSnapshotConfig**|GET|Search live snapshot configuration|
|**describeCustomLiveStreamSnapshotTemplates**|GET|Search live snapshot template list|
|**describeCustomLiveStreamTranscodeTemplate**|GET|Search user customized transcoding template details|
|**describeCustomLiveStreamTranscodeTemplates**|GET|Search user customized transcoding template list|
|**describeCustomLiveStreamWatermarkConfig**|GET|Search watermark configuration|
|**describeCustomLiveStreamWatermarkTemplates**|GET|Search watermark template list|
|**describeLiveApp**|GET|Search APP list under the domain|
|**describeLiveDomainDetail**|GET|Search the relevant information of specified domain|
|**describeLiveDomains**|GET|Search domain list|
|**describeLivePlayAuthKey**|GET|Search play authentication KEY|
|**describeLivePornData**|GET|Search live porn identification number data|
|**describeLiveRecordData**|GET|Search live recording duration data|
|**describeLiveRestartConfigs**|GET|Search restart configuration|
|**describeLiveSnapshotData**|GET|Search live snapshot number data|
|**describeLiveStreamNotifyConfig**|GET|Search live streaming status notification|
|**describeLiveStreamOnlineList**|GET|View all stream information that is being pushed under the domain|
|**describeLiveStreamPublishList**|GET|View pushing streaming record under the domain|
|**describeLiveStreamRecordNotifyConfig**|GET|Search record callback configuration|
|**describeLiveStreamSnapshotNotifyConfig**|GET|Search snapshot callback configuration|
|**describeLiveStreamTranscodeConfig**|GET|Search transcoding template configuration|
|**describeLiveTimeshiftConfigs**|GET|Search timeshift configuration|
|**forbidLiveStream**|PUT|Ban live streaming pushing|
|**openLiveRestart**|PUT|Open restart|
|**openLiveTimeshift**|PUT|Open timeshift|
|**resumeLiveStream**|PUT|Recover live streaming pushing|
|**setLivePlayAuthKey**|POST|Set play authentication KEY|
|**setLiveStreamNotifyConfig**|POST|Set pushing streaming callback configuration|
|**setLiveStreamRecordNotifyConfig**|POST|Set record callback notification|
|**setLiveStreamSnapshotNotifyConfig**|POST|Set snapshot callback notification|
|**startLiveApp**|PUT|Enable APP|
|**startLiveDomain**|PUT|Start domain|
|**stopLiveApp**|PUT|Disable APP|
|**stopLiveDomain**|PUT|Disable domain|
