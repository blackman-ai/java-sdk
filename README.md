# Blackman AI Java SDK

Official Java client for [Blackman AI](https://www.useblackman.ai) - The AI API proxy that optimizes token usage to reduce costs.

## Features

- 🚀 Drop-in replacement for OpenAI, Anthropic, and other LLM APIs
- 💰 Automatic token optimization (save 20-40% on costs)
- 📊 Built-in analytics and cost tracking
- 🔒 Enterprise-grade security with SSO support
- ⚡ Low latency overhead (<50ms)
- 🎯 Semantic caching for repeated queries

## Installation

### Maven

```xml
<dependency>
    <groupId>ai.useblackman</groupId>
    <artifactId>client</artifactId>
    <version>0.0.5</version>
</dependency>
```

### Gradle

```groovy
implementation 'ai.blackman:client:0.0.5'
```

### Gradle (Kotlin DSL)

```kotlin
implementation("ai.blackman:client:0.0.5")
```

## Quick Start

```java
import ai.blackman.client.ApiClient;
import ai.blackman.client.api.CompletionsApi;
import ai.blackman.client.model.CompletionRequest;
import ai.blackman.client.model.CompletionResponse;
import ai.blackman.client.model.Message;

import java.util.List;

public class BlackmanExample {
    public static void main(String[] args) {
        // Configure client
        ApiClient client = new ApiClient();
        client.setBasePath("https://app.useblackman.ai");
        client.addDefaultHeader("Authorization", "Bearer sk_your_blackman_api_key");

        CompletionsApi api = new CompletionsApi(client);

        // Create completion request
        Message message = new Message()
            .role("user")
            .content("Explain quantum computing in simple terms");

        CompletionRequest request = new CompletionRequest()
            .provider("OpenAI")
            .model("gpt-4o")
            .messages(List.of(message));

        try {
            // Send request
            CompletionResponse response = api.completions(request);
            System.out.println(response.getChoices().get(0).getMessage().getContent());
            System.out.println("Tokens used: " + response.getUsage().getTotalTokens());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Authentication

Get your API key from the [Blackman AI Dashboard](https://app.useblackman.ai/settings/api-keys).

```java
ApiClient client = new ApiClient();
client.setBasePath("https://app.useblackman.ai");
client.addDefaultHeader("Authorization", "Bearer sk_your_blackman_api_key");
```

## Framework Integration

### Spring Boot

Create a configuration class to inject the Blackman client:

```java
import ai.blackman.client.ApiClient;
import ai.blackman.client.api.CompletionsApi;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class BlackmanConfig {

    @Value("${blackman.api.key}")
    private String apiKey;

    @Value("${blackman.api.base-url:https://app.useblackman.ai}")
    private String baseUrl;

    @Bean
    public ApiClient blackmanApiClient() {
        ApiClient client = new ApiClient();
        client.setBasePath(baseUrl);
        client.addDefaultHeader("Authorization", "Bearer " + apiKey);
        return client;
    }

    @Bean
    public CompletionsApi completionsApi(ApiClient apiClient) {
        return new CompletionsApi(apiClient);
    }
}
```

Then use it in your service:

```java
import ai.blackman.client.api.CompletionsApi;
import ai.blackman.client.model.CompletionRequest;
import ai.blackman.client.model.CompletionResponse;
import ai.blackman.client.model.Message;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class ChatService {

    private final CompletionsApi completionsApi;

    public ChatService(CompletionsApi completionsApi) {
        this.completionsApi = completionsApi;
    }

    public String chat(String userMessage) throws Exception {
        Message message = new Message()
            .role("user")
            .content(userMessage);

        CompletionRequest request = new CompletionRequest()
            .provider("OpenAI")
            .model("gpt-4o")
            .messages(List.of(message));

        CompletionResponse response = completionsApi.completions(request);
        return response.getChoices().get(0).getMessage().getContent();
    }
}
```

Configure in `application.properties`:

```properties
blackman.api.key=sk_your_blackman_api_key
blackman.api.base-url=https://app.useblackman.ai
```

### Reactive Spring WebFlux

For reactive applications, configure a WebClient-based approach:

```java
import org.springframework.web.reactive.function.client.WebClient;
import reactor.core.publisher.Mono;

@Service
public class ReactiveChatService {

    private final WebClient webClient;

    public ReactiveChatService(@Value("${blackman.api.key}") String apiKey) {
        this.webClient = WebClient.builder()
            .baseUrl("https://app.useblackman.ai")
            .defaultHeader("Authorization", "Bearer " + apiKey)
            .build();
    }

    public Mono<String> chat(String message) {
        return webClient.post()
            .uri("/v1/completions")
            .bodyValue(Map.of(
                "provider", "OpenAI",
                "model", "gpt-4o",
                "messages", List.of(Map.of("role", "user", "content", message))
            ))
            .retrieve()
            .bodyToMono(CompletionResponse.class)
            .map(response -> response.getChoices().get(0).getMessage().getContent());
    }
}
```

## Advanced Usage

### Custom Timeouts

```java
import okhttp3.OkHttpClient;
import java.util.concurrent.TimeUnit;

// Create custom OkHttpClient with timeouts
OkHttpClient httpClient = new OkHttpClient.Builder()
    .connectTimeout(30, TimeUnit.SECONDS)
    .readTimeout(60, TimeUnit.SECONDS)
    .writeTimeout(60, TimeUnit.SECONDS)
    .build();

ApiClient client = new ApiClient(httpClient);
client.setBasePath("https://app.useblackman.ai");
client.addDefaultHeader("Authorization", "Bearer sk_your_blackman_api_key");
```

### Error Handling

```java
import ai.blackman.client.ApiException;

try {
    CompletionResponse response = api.completions(request);
    System.out.println(response.getChoices().get(0).getMessage().getContent());
} catch (ApiException e) {
    System.err.println("Status code: " + e.getCode());
    System.err.println("Response body: " + e.getResponseBody());
    System.err.println("Response headers: " + e.getResponseHeaders());
    e.printStackTrace();
} catch (Exception e) {
    System.err.println("Unexpected error: " + e.getMessage());
    e.printStackTrace();
}
```

### Streaming Responses

```java
import java.util.concurrent.CompletableFuture;

// For streaming, use async approach
CompletableFuture.supplyAsync(() -> {
    try {
        return api.completions(request);
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}).thenAccept(response -> {
    // Process response
    System.out.println(response.getChoices().get(0).getMessage().getContent());
});
```

## Documentation

- [Full API Reference](https://app.useblackman.ai/docs)
- [Getting Started Guide](https://app.useblackman.ai/docs/getting-started)
- [Java Examples](https://github.com/blackman-ai/java-sdk/tree/main/examples)
- [JavaDoc](https://javadoc.io/doc/ai.blackman/client)

## Requirements

- Java 8 or higher
- Maven or Gradle

## Support

- 📧 Email: [support@blackman.ai](mailto:support@blackman.ai)
- 💬 Discord: [Join our community](https://discord.gg/blackman-ai)
- 🐛 Issues: [GitHub Issues](https://github.com/blackman-ai/java-sdk/issues)

## License

MIT © Blackman AI
