# Firefly Framework - Parent POM

[![CI](https://github.com/fireflyframework/fireflyframework-parent/actions/workflows/ci.yml/badge.svg)](https://github.com/fireflyframework/fireflyframework-parent/actions/workflows/ci.yml)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21%2B-orange.svg)](https://openjdk.org)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green.svg)](https://spring.io/projects/spring-boot)

> Parent POM for the Firefly Framework providing centralized dependency management, plugin configuration, and build standards for all framework modules.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview

The Firefly Framework Parent POM serves as the foundational build configuration for all Firefly Framework modules. It centralizes dependency version management, plugin configurations, and build standards to ensure consistency across the entire framework ecosystem.

By inheriting from this parent POM, all Firefly modules automatically receive managed versions for Spring Boot 3.5.x, Spring Cloud 2025.0.x, database drivers, mapping libraries, testing frameworks, and build plugins. This eliminates version conflicts and simplifies dependency management across the framework.

The parent POM also configures annotation processors for Lombok, MapStruct, and Spring Boot Configuration Processor, along with Maven Enforcer rules requiring JDK 21+.

## Features

- Centralized dependency management for Spring Boot 3.5.x and Spring Cloud 2025.0.x
- Managed versions for PostgreSQL, R2DBC, and Flyway database migrations (multi-database support)
- Pre-configured annotation processors (Lombok, MapStruct, Spring Boot Configuration Processor)
- OpenAPI Generator plugin configuration for server/client code generation from API specs
- Maven Enforcer plugin requiring JDK 21+
- Testcontainers BOM for integration testing
- Resilience4j BOM for fault tolerance patterns
- gRPC 1.79.x and Protobuf 4.x version management
- AWS SDK 2.x, Spring Cloud Azure, and Spring Cloud GCP dependency management
- SpringDoc OpenAPI for reactive API documentation
- Release profile with source and Javadoc JAR generation
- Java 21 backward compatibility via `-Pjava21` Maven profile

## Requirements

- Java 21+
- Maven 3.9+

## Installation

Use this as a parent POM in your Firefly Framework module:

```xml
<parent>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-parent</artifactId>
    <version>26.02.04</version>
    <relativePath/>
</parent>
```

## Quick Start

Create a new Firefly Framework module by referencing the parent POM:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.fireflyframework</groupId>
        <artifactId>fireflyframework-parent</artifactId>
        <version>26.02.04</version>
        <relativePath/>
    </parent>

    <artifactId>my-firefly-module</artifactId>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-webflux</artifactId>
        </dependency>
    </dependencies>
</project>
```

All dependency versions are inherited automatically from the parent POM.

## Configuration

Key properties that can be overridden in child modules:

```xml
<properties>
    <!-- Java version (default: 25) -->
    <java.version>25</java.version>

    <!-- Base package for code generation -->
    <base.package>org.fireflyframework</base.package>

    <!-- OpenAPI generation settings -->
    <openapi.skip.validate>false</openapi.skip.validate>
    <openapi.use.tags>true</openapi.use.tags>
</properties>
```

Build with Java 21 compatibility:

```bash
mvn clean install -Pjava21
```

## Documentation

No additional documentation available for this project.

## Contributing

Contributions are welcome. Please read the [CONTRIBUTING.md](CONTRIBUTING.md) guide for details on our code of conduct, development process, and how to submit pull requests.

## License

Copyright 2024-2026 Firefly Software Solutions Inc.

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
