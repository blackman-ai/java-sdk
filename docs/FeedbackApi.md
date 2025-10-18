# FeedbackApi

All URIs are relative to *https://app.useblackman.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**submitFeedback**](FeedbackApi.md#submitFeedback) | **POST** /v1/feedback | Submit feedback for a completion response |


<a id="submitFeedback"></a>
# **submitFeedback**
> SubmitFeedbackResponse submitFeedback(submitFeedbackRequest)

Submit feedback for a completion response

### Example
```java
// Import classes:
import ai.blackman.client.ApiClient;
import ai.blackman.client.ApiException;
import ai.blackman.client.Configuration;
import ai.blackman.client.auth.*;
import ai.blackman.client.models.*;
import ai.blackman.client.api.FeedbackApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://app.useblackman.ai/v1");
    
    // Configure HTTP bearer authorization: BearerAuth
    HttpBearerAuth BearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("BearerAuth");
    BearerAuth.setBearerToken("BEARER TOKEN");

    FeedbackApi apiInstance = new FeedbackApi(defaultClient);
    SubmitFeedbackRequest submitFeedbackRequest = new SubmitFeedbackRequest(); // SubmitFeedbackRequest | 
    try {
      SubmitFeedbackResponse result = apiInstance.submitFeedback(submitFeedbackRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FeedbackApi#submitFeedback");
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
| **submitFeedbackRequest** | [**SubmitFeedbackRequest**](SubmitFeedbackRequest.md)|  | |

### Return type

[**SubmitFeedbackResponse**](SubmitFeedbackResponse.md)

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Feedback submitted successfully |  -  |
| **401** | Unauthorized |  -  |
| **500** | Internal server error |  -  |

