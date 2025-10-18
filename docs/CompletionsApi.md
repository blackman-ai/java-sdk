# CompletionsApi

All URIs are relative to *https://app.useblackman.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**completions**](CompletionsApi.md#completions) | **POST** /v1/completions |  |


<a id="completions"></a>
# **completions**
> CompletionResponse completions(completionRequest, xProviderApiKey)



### Example
```java
// Import classes:
import ai.useblackman.client.ApiClient;
import ai.useblackman.client.ApiException;
import ai.useblackman.client.Configuration;
import ai.useblackman.client.auth.*;
import ai.useblackman.client.models.*;
import ai.useblackman.client.api.CompletionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://app.useblackman.ai/v1");
    
    // Configure HTTP bearer authorization: BearerAuth
    HttpBearerAuth BearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("BearerAuth");
    BearerAuth.setBearerToken("BEARER TOKEN");

    CompletionsApi apiInstance = new CompletionsApi(defaultClient);
    CompletionRequest completionRequest = new CompletionRequest(); // CompletionRequest | 
    String xProviderApiKey = "xProviderApiKey_example"; // String | Optional provider API key to override stored or system keys
    try {
      CompletionResponse result = apiInstance.completions(completionRequest, xProviderApiKey);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling CompletionsApi#completions");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **completionRequest** | [**CompletionRequest**](CompletionRequest.md)|  | |
| **xProviderApiKey** | **String**| Optional provider API key to override stored or system keys | [optional] |

### Return type

[**CompletionResponse**](CompletionResponse.md)

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | AI completion response |  -  |
| **401** | Unauthorized - missing or invalid authentication token |  -  |
| **402** | Payment required - no active subscription |  -  |
| **500** | Provider error |  -  |
| **503** | Service unavailable - provider API key not configured |  -  |

