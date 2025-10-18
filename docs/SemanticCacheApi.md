# SemanticCacheApi

All URIs are relative to *https://app.useblackman.ai/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getConfig**](SemanticCacheApi.md#getConfig) | **GET** /v1/semantic-cache/config | Get semantic cache configuration for the current account |
| [**getStats**](SemanticCacheApi.md#getStats) | **GET** /v1/semantic-cache/stats | Get semantic cache statistics including hit rate and savings |
| [**invalidateAll**](SemanticCacheApi.md#invalidateAll) | **DELETE** /v1/semantic-cache/invalidate | Invalidate all cache entries for the current account |
| [**updateConfig**](SemanticCacheApi.md#updateConfig) | **PUT** /v1/semantic-cache/config | Update semantic cache configuration for the current account |


<a id="getConfig"></a>
# **getConfig**
> SemanticCacheConfig getConfig()

Get semantic cache configuration for the current account

### Example
```java
// Import classes:
import ai.blackman.client.ApiClient;
import ai.blackman.client.ApiException;
import ai.blackman.client.Configuration;
import ai.blackman.client.auth.*;
import ai.blackman.client.models.*;
import ai.blackman.client.api.SemanticCacheApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://app.useblackman.ai/v1");
    
    // Configure HTTP bearer authorization: BearerAuth
    HttpBearerAuth BearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("BearerAuth");
    BearerAuth.setBearerToken("BEARER TOKEN");

    SemanticCacheApi apiInstance = new SemanticCacheApi(defaultClient);
    try {
      SemanticCacheConfig result = apiInstance.getConfig();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SemanticCacheApi#getConfig");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**SemanticCacheConfig**](SemanticCacheConfig.md)

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Cache configuration retrieved successfully |  -  |
| **401** | Unauthorized |  -  |
| **500** | Internal server error |  -  |

<a id="getStats"></a>
# **getStats**
> SemanticCacheStats getStats()

Get semantic cache statistics including hit rate and savings

### Example
```java
// Import classes:
import ai.blackman.client.ApiClient;
import ai.blackman.client.ApiException;
import ai.blackman.client.Configuration;
import ai.blackman.client.auth.*;
import ai.blackman.client.models.*;
import ai.blackman.client.api.SemanticCacheApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://app.useblackman.ai/v1");
    
    // Configure HTTP bearer authorization: BearerAuth
    HttpBearerAuth BearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("BearerAuth");
    BearerAuth.setBearerToken("BEARER TOKEN");

    SemanticCacheApi apiInstance = new SemanticCacheApi(defaultClient);
    try {
      SemanticCacheStats result = apiInstance.getStats();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SemanticCacheApi#getStats");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**SemanticCacheStats**](SemanticCacheStats.md)

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Cache statistics retrieved successfully |  -  |
| **401** | Unauthorized |  -  |
| **500** | Internal server error |  -  |

<a id="invalidateAll"></a>
# **invalidateAll**
> InvalidateResponse invalidateAll()

Invalidate all cache entries for the current account

### Example
```java
// Import classes:
import ai.blackman.client.ApiClient;
import ai.blackman.client.ApiException;
import ai.blackman.client.Configuration;
import ai.blackman.client.auth.*;
import ai.blackman.client.models.*;
import ai.blackman.client.api.SemanticCacheApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://app.useblackman.ai/v1");
    
    // Configure HTTP bearer authorization: BearerAuth
    HttpBearerAuth BearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("BearerAuth");
    BearerAuth.setBearerToken("BEARER TOKEN");

    SemanticCacheApi apiInstance = new SemanticCacheApi(defaultClient);
    try {
      InvalidateResponse result = apiInstance.invalidateAll();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SemanticCacheApi#invalidateAll");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**InvalidateResponse**](InvalidateResponse.md)

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | All cache entries invalidated successfully |  -  |
| **401** | Unauthorized |  -  |
| **500** | Internal server error |  -  |
| **503** | Semantic cache not configured |  -  |

<a id="updateConfig"></a>
# **updateConfig**
> updateConfig(semanticCacheConfig)

Update semantic cache configuration for the current account

### Example
```java
// Import classes:
import ai.blackman.client.ApiClient;
import ai.blackman.client.ApiException;
import ai.blackman.client.Configuration;
import ai.blackman.client.auth.*;
import ai.blackman.client.models.*;
import ai.blackman.client.api.SemanticCacheApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://app.useblackman.ai/v1");
    
    // Configure HTTP bearer authorization: BearerAuth
    HttpBearerAuth BearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("BearerAuth");
    BearerAuth.setBearerToken("BEARER TOKEN");

    SemanticCacheApi apiInstance = new SemanticCacheApi(defaultClient);
    SemanticCacheConfig semanticCacheConfig = new SemanticCacheConfig(); // SemanticCacheConfig | 
    try {
      apiInstance.updateConfig(semanticCacheConfig);
    } catch (ApiException e) {
      System.err.println("Exception when calling SemanticCacheApi#updateConfig");
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
| **semanticCacheConfig** | [**SemanticCacheConfig**](SemanticCacheConfig.md)|  | |

### Return type

null (empty response body)

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Cache configuration updated successfully |  -  |
| **400** | Invalid configuration values |  -  |
| **401** | Unauthorized |  -  |
| **500** | Internal server error |  -  |

