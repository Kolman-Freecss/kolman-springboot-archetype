# Kolman SpringBoot Archetype

This is a SpringBoot project with a Hexagonal architecture.

It serve as a template for new projects.

## Index

- [Getting Started](#getting-started)
- [Tech stacks](#tech-stacks)
- [Architecture](#architecture)
- [Infrastructure](#infrastructure)
- [Troubleshoting](#troubleshoting)

## Getting Started

How to run the project:

1. Check the `.launchers` folder to see the different launchers.
2. Run Application.run.xml to start the application. (This will start the Springboot application)

## Tech stacks

- Java 22
- Springboot 3
- AOP
  - Aspect Oriented Programming. Used to log different parts of the application.
    - Example: Check the `com.kolmanfreecss.KolmanSpringBootArchetype.infrastructure.config.PerformanceAspect` class. It logs the performance of the Service layer.
- Spring Actuator
  - You can check the health of the application in the following URL: `http://localhost:8080/actuator` or just `http://localhost:8080/actuator/health`
- Springboot Webflux
  - Reactive programming. Async API to perform non-blocking operations in the main thread application.
- SpringBoot Config Processor
  - To generate the configuration file. (Its a helper to generate the configuration file).
- SpringBoot DevTools
  - To reload the application when a change is detected.
- Spring Data Redis (instead of Caffeine)
  - To cache data with Jedis (Redis client).

## Architecture

- Microservices.
- Hexagonal. 
  ```
  # Overview
  src
  ├── main
  │   ├── java
  │   │   └── com
  │   │       └── com.kolmanfreecss.KolmanSpringBootArchetype
  │   │           ├── application            # Contains application logic and use cases
  │   │           │   ├── dto                # Data Transfer Objects for data transfer
  │   │           │   ├── mapper             # Classes for mapping entities to DTOs and vice versa
  │   │           │   ├── exception           # Custom exceptions for application logic
  │   │           │   └── service             # Application services orchestrating business logic
  │   │           ├── domain                 # Contains domain entities and repositories
  │   │           │   ├── entity              # Domain entities representing core concepts
  │   │           │   ├── repository          # Interfaces for data access
  │   │           │   └── service             # Domain services encapsulating business rules
  │   │           ├── infrastructure          # Contains implementations of adapters and data access
  │   │           │   ├── repository          # Repository implementations (e.g., JPA)
  │   │           │   ├── configuration       # Configuration classes for persistence, security, etc.
  │   │           │   └── external            # Adapters for external services (APIs, messaging, etc.)
  │   │           └── web                    # Contains REST controllers and user interface
  │   │               ├── controller           # REST controllers handling incoming requests
  │   │               └── exception            # Exception handling for web layer
  │   └── resources
  │       └── application.properties   # Application configuration files
  └── test
      └── java
          └── com
              └── com.kolmanfreecss.KolmanSpringBootArchetype
                  ├── application     # Contains application logic and use cases
                  ...
                  ├── domain          # Contains domain entities and repositories
                  ...
                  ├── infrastructure   # Contains adapter implementations and data access
                  ...
  ```

## Infrastructure

- Docker
- Github Actions

## Troubleshoting


---

Shield: [![CC-BY-NC-ND 4.0][CC-BY-NC-ND-shield]][CC-BY-NC-ND]

This work is licensed under a [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License.][CC-BY-NC-ND]

[![CC-BY-NC-ND 4.0][CC-BY-NC-ND-image]][CC-BY-NC-ND]

[CC-BY-NC-ND-shield]: https://img.shields.io/badge/License-CC--BY--NC--ND--4.0-lightgrey
[CC-BY-NC-ND]: http://creativecommons.org/licenses/by-nc-nd/4.0/
[CC-BY-NC-ND-image]: https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png
