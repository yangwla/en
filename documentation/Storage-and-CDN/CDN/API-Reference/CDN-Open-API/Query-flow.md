# **Traffic Query**

## **1. Description**

Traffic Query

Description

* The traffic value range of granularity in five minutes is the value in the preceding five minutes from current time point, e.g.: For data at the time point of 13:25, the time range of value is the data from 13:20 to 13:25;

## **2. Request Parameter**

| **Name**   | **Type** | **Compulsory or Not ** | **Description**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | Yes           | JD User Name pin                                                |
| signature  | String   | Yes           | User Signature, verify user's identity information through md5 method to ensure information security.</br> md5=date+username+secret key SecretKey; date: format is yyyymmdd; username: JD user name pin secret key: agreed between the Parties;</br> example: such as current date 2016-10-23, user pin: jcloud_00, user secret key SecretKey: e7a31b1c5ea0efa9aa2f29c6559f7d61, then the signature is MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | Yes           | Domain name to be queried, support query of multiple domain names, parameter example "www.a.com,www.b.com"  When domain is empty, it queries the total bandwidth of all domain names under this username  |
| start_time | String   | Yes           | Time Format: yyyy-mm-dd hh:mi Reference Example 2016-12-14 07:00; the time span for query cannot be greater than 31 days  |
| end_time   | String   | No            | Not a compulsory parameter; if no parameter is uploaded, it is current time by default                             |


## **3. Return Parameter**

| **Name** | **Description**                       |
| -------- | ------------------------------ |
| status   | Result status 0, refresh successful, others failure|
| msg      | Note Information                       |
| data     | Return Data                       |


## **4. Call Example**

- ### **Request Address**

https://opencdn.jcloud.com/api/flow

- ### **Request Example**

```
https://opencdn.jcloud.com/api/flow
{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :"www.a.com,www.b.com",
    "start_time" :"2016-12-14 07:00",
    "end_time" :"2016-12-14 12:59"
 }
```

- ### **Return Instructions**

•        Json Format

```
{
"status": 0,//0 means this request succeeded
"data": [
{
"domain": "DOMAIN",//Queried domain name, do not include http://
"data": [
[
TS, //Time Stamp
FLOW,//Traffic, Unit: MB
HIT_FLOW//Hit Traffic, Unit: MB
],
],
},
]
}
```

- ### **Return Example**

```
{
  "status": 0,
  "msg": "Successful",
  "data": [
    {
      "domain": "www.a.com",
      "data": [
        [
          1480989960,
      1,
          1
        ],
        [
          1480990860,
      901,
          901
        ]
      ]
    },
    {
      "domain": "www.b.com",
      "data": [
        [
          1480989960,
      100,
          100
        ],
        [
          1480990860,
      1001,
          1000
        ]
      ]
    }
  ]
}
```
