
# Introduction #

Welcome to the JD Cloud Developer Java Tools Kit (Java SDK). With JD Cloud Java SDK, you can access the services provided by JD Cloud without complex programming. 

To facilitate the understanding of some concepts and parameters in the SDK, it's recommended to review the Getting Started to the OpenAPI before using the SDK. To understand the specific parameters and meanings of each API, refer to the program comments or documentation for specific product lines under OpenAPI&SDK.


# Environment Preparation #

1. The JD Cloud Java SDK is applicable to jdk7 and above versions.

2. Before calling JD Cloud open API, it's necessary to apply for accesskey and secretKey Key Pair (AK/SK) in advance in Account Management of JD Cloud User Center. AK/ SK information shall be kept properly and if lost, it is likely to allow illegal users to use this information to operate your resources on the cloud, resulting in data or property losses.



# SDK Usage Method #

If you use Apache Maven to manage a Java project, you only need to add a corresponding dependency item in the pom.xml file of the project, as follows:
```
<!-- SDK of corresponding product line -->
<dependency>
    <groupId>com.jdcloud.sdk</groupId>
    <artifactId>vm</artifactId>
    <version>1.2.0</version>
</dependency>
```

You can also download the SDK source code yourself. The source code address is [Java SDK](https://github.com/jdcloud-api/jdcloud-sdk-java).

With any of the problems in the SDK use, you are welcomed to communicate at the [SDK Usage Problem Feedback Page](https://github.com/jdcloud-api/jdcloud-sdk-java/issues) for the Github project.

**Note:** 

- JD Cloud does not provide other downloading ways, please be sure to use the above-mentioned official download method.

- The latest version number provided by JD Cloud product shall be used as the version number. For example: The latest version number used by VM in the example can be searched in API [Update History](../../API/Virtual-Machines/ChangeLog.md).

- Each cloud product has its own Client. When API of this product is called, the Client of such product will be used. For example: When VmClient of Virtual Machines is used, only APIs of Virtual Machines (Vm) can be called; when AgClient of Availability Group is used, only APIs of Availability Group (Ag) can be called.


 

# Call SDK #

The calling of the Java SDK is mainly divided into four steps:

 1. Set accessKey and secretKey

 2. Create Client

 3. Set Request Parameters

 4. Response to implementation requests

The following is an example of a call to query details for individual VM Instance

```Java
	import com.jdcloud.sdk.JdcloudSdkException;
	import com.jdcloud.sdk.auth.CredentialsProvider;
	import com.jdcloud.sdk.auth.StaticCredentialsProvider;
	import com.jdcloud.sdk.http.HttpRequestConfig;
	import com.jdcloud.sdk.http.Protocol;
	import com.jdcloud.sdk.service.vm.client.VmClient;
	import com.jdcloud.sdk.service.vm.model.*;
	
	public class VmClientExample {

	    public static void main(String[] args) {
	        // 1. Set accessKey and secretKey
	        String accessKeyId = "{accessKey}";
	        String secretAccessKey = "{secretKey}";
	        CredentialsProvider credentialsProvider = new StaticCredentialsProvider(accessKeyId, secretAccessKey);

	        // 2. Creating XXXClient
	        VmClient vmClient = VmClient.builder()
	                .credentialsProvider(credentialsProvider)
	                . httpRequestConfig(new HttpRequestConfig.Builder().protocol(Protocol.HTTPS).build()) //HTTPS by default
	                .build();

	        // 3. Set Request Parameters
	        DescribeInstanceRequest request = new DescribeInstanceRequest();
	        request.regionId("cn-north-1");
	        request.instanceId("i-c0se9uju");

	        // 4. Execution Requests
	        try {
	            DescribeInstanceResponse response = vmClient.describeInstance(request);

	            // Return business error
	            if(response.getError() != null) {
	                // Call the API to return business errors, error handling
	                System.out.println(response.getRequestId() + " failed: " + response.getError().getMessage());
	                return;
	            }
	            DescribeInstanceResult result = response.getResult();
	            // 5. Normally return the result and carry out follow-up processing using the returned data
 	       }catch (JdcloudSdkException jse) {
	            // Calling API failed, error handling
 	       }
	    }
	}
```

If you need to set up an additional header, for example, call an interface that opens the MFA operation protection, you need to pass x-jdcloud-security-token, as follows:
```
	 vmClient.setCustomHeader("x-jdcloud-security-token", "xxxx"); 
	
```

