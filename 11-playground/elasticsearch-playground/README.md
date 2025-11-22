# Elasticsearch Playground

This project is up to date with **Java 25** and **Spring Boot 4.x**. Please check the [pom.xml](./pom.xml) for the dependencies.

## 📌 Testcontainers Configuration

Please use the updated Testcontainers configuration for Elasticsearch [here](./src/test/java/com/vinsguru/playground/TestcontainersConfiguration.java):

```java
@TestConfiguration(proxyBeanMethods = false)
class TestcontainersConfiguration {

    @Bean
    @ServiceConnection
    ElasticsearchContainer elasticsearchContainer() {
        return new ElasticsearchContainer(
                DockerImageName.parse("docker.elastic.co/elasticsearch/elasticsearch:9.0.2"))
                .withEnv("xpack.security.enabled", "false")
                .withEnv("xpack.security.http.ssl.enabled", "false");
    }
}
```

## 🚨 Breaking Changes - Jackson Package Change

### **Spring Boot 3.x**

```java
import com.fasterxml.jackson.core.type.TypeReference;
import com.fasterxml.jackson.databind.ObjectMapper;
```

### **Spring Boot 4.x**

```java
import tools.jackson.core.type.TypeReference;
import tools.jackson.databind.ObjectMapper;
```

Please let me know via Q/A section if you have face issues.
