# Firefly Framework - Parent POM

The parent POM for all Firefly Framework modules. It centralizes dependency management, plugin configuration, and build conventions so that individual modules inherit a consistent, production-ready baseline without duplicating configuration.

## Purpose

When a Firefly Framework module (or a downstream application) declares `fireflyframework-parent` as its parent, it inherits:

- **Dependency version alignment** across Spring Boot, Spring Cloud, database drivers, serialization libraries, resilience utilities, and testing frameworks.
- **Plugin configuration** for compilation, testing, packaging, source/javadoc generation, and OpenAPI code generation.
- **Annotation processor wiring** for Lombok, MapStruct, and Spring Boot Configuration Processor.
- **Consistent compiler settings** targeting Java 21 with `-parameters` for reflection-friendly bytecode.

## Managed Versions

### Runtime

| Dependency | Version |
|---|---|
| Spring Boot | 3.5.9 |
| Spring Cloud | 2025.0.1 |
| Java | 21 |
| SpringDoc OpenAPI | 2.8.6 |
| Resilience4j | 2.3.0 |
| MapStruct | 1.6.3 |
| Lombok | 1.18.38 |
| Logstash Logback Encoder | 8.0 |

### Database

| Dependency | Version |
|---|---|
| PostgreSQL Driver | 42.7.4 |
| R2DBC PostgreSQL | 1.0.7.RELEASE |
| Flyway | 10.22.0 |

### Communication

| Dependency | Version |
|---|---|
| gRPC | 1.68.2 |
| Protobuf | 3.25.5 |
| OpenAPI Generator | 7.10.0 |
| Swagger Annotations | 2.2.30 |

### Cloud Providers

| Dependency | Version |
|---|---|
| AWS SDK | 2.31.32 |
| Spring Cloud AWS | 3.3.0 |
| Spring Cloud Azure | 5.22.0 |
| Spring Cloud GCP | 6.1.1 |

### Testing

| Dependency | Version |
|---|---|
| Testcontainers | 1.20.4 |
| Surefire Plugin | 3.5.2 |
| Failsafe Plugin | 3.5.2 |

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
| `maven-compiler-plugin` | Java 21 compilation with Lombok + MapStruct + Spring Boot Configuration Processor |
| `maven-source-plugin` | Attaches source JARs to build artifacts |
| `maven-javadoc-plugin` | Generates and attaches Javadoc JARs |
| `maven-surefire-plugin` | Unit test execution |
| `maven-failsafe-plugin` | Integration test execution |
| `openapi-generator-maven-plugin` | Server/client code generation from OpenAPI specifications |
| `maven-deploy-plugin` | Artifact deployment to Maven repositories |

## License

Apache License 2.0

Copyright 2024-2026 Firefly Software Solutions Inc.
