# Firefly Framework - Parent POM

The parent POM for all Firefly Framework modules. It centralizes dependency management, plugin configuration, and build conventions so that individual modules inherit a consistent, production-ready baseline without duplicating configuration.

## Purpose

When a Firefly Framework module (or a downstream application) declares `fireflyframework-parent` as its parent, it inherits:

- **Dependency version alignment** across Spring Boot, Spring Cloud, database drivers, serialization libraries, resilience utilities, and testing frameworks.
- **Plugin configuration** for compilation, testing, packaging, source/javadoc generation, and OpenAPI code generation.
- **Annotation processor wiring** for Lombok, MapStruct, and Spring Boot Configuration Processor.
- **Consistent compiler settings** targeting Java 25 (default, Java 21+ compatible) with `-parameters` for reflection-friendly bytecode.
- **Java 21 backward compatibility** via `-Pjava21` Maven profile.

## Managed Versions

### Runtime

| Dependency | Version |
|---|---|
| Spring Boot | 3.5.9 |
| Spring Cloud | 2025.0.1 |
| Java | 25 (default, 21+ compatible) |
| SpringDoc OpenAPI | 2.8.15 |
| Resilience4j | 2.3.0 |
| MapStruct | 1.6.3 |
| Lombok | 1.18.42 |
| Logstash Logback Encoder | 8.1 |

### Database

| Dependency | Version |
|---|---|
| PostgreSQL Driver | 42.7.8 |
| R2DBC PostgreSQL | 1.0.9.RELEASE |
| Flyway | 11.7.2 |

### Communication

| Dependency | Version |
|---|---|
| gRPC | 1.79.0 |
| Protobuf | 4.33.5 |
| OpenAPI Generator | 7.19.0 |
| Swagger Annotations | 2.2.42 |

### Cloud Providers

| Dependency | Version |
|---|---|
| AWS SDK | 2.41.24 |
| Spring Cloud AWS | 3.4.2 |
| Spring Cloud Azure | 5.24.1 |
| Spring Cloud GCP | 6.5.4 |

### Testing

| Dependency | Version |
|---|---|
| Testcontainers | 1.21.4 |
| Surefire Plugin | 3.5.4 |
| Failsafe Plugin | 3.5.4 |

## Usage

### As a Parent POM (Recommended)

Declare `fireflyframework-parent` as the parent of your module or application:

```xml
<parent>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-parent</artifactId>
    <version>1.0.0-SNAPSHOT</version>
    <relativePath/>
</parent>
```

This gives your project all managed dependency versions, plugin configurations, and annotation processor wiring out of the box.

### If You Already Have a Parent

If your project already has a different parent POM and cannot inherit from `fireflyframework-parent`, use the [fireflyframework-bom](https://github.com/fireflyframework/fireflyframework-bom) instead for dependency version management.

## Plugin Configuration

The parent POM configures the following plugins in `pluginManagement`:

| Plugin | Purpose |
|---|---|
| `spring-boot-maven-plugin` | Packaging Spring Boot applications (excludes Lombok from fat JAR) |
| `maven-compiler-plugin` | Java 25 (default) compilation with Lombok + MapStruct + Spring Boot Configuration Processor |
| `maven-source-plugin` | Attaches source JARs to build artifacts |
| `maven-javadoc-plugin` | Generates and attaches Javadoc JARs |
| `maven-surefire-plugin` | Unit test execution |
| `maven-failsafe-plugin` | Integration test execution |
| `openapi-generator-maven-plugin` | Server/client code generation from OpenAPI specifications |
| `maven-deploy-plugin` | Artifact deployment to Maven repositories |

## License

Apache License 2.0

Copyright 2024-2026 Firefly Software Solutions Inc.
