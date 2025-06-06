# Test and Analysis

## Introduction
Ensuring code quality, performance, and reliability is a critical part of the development lifecycle. This section outlines the tools and strategies used in our project to test, analyze, and monitor the application at various levels.

We employ a combination of **unit testing**, **end-to-end (E2E) testing**, **code quality analysis**, and **performance monitoring** to ensure the application functions correctly and efficiently.

## Unit Test Frameworks and Tools

- **Unit Testing** is handled through frameworks such as **Jest**, allowing us to test individual functions and components in isolation.

## Jest

- **Jest** is used for unit testing JavaScript and TypeScript code. It provides fast test execution, built-in mocking, snapshot testing, and code coverage reports. Jest is integrated into our CI/CD pipeline to catch regressions early.

[Unit Testing](unitTesting.md)

## End-to-End (E2E) Teststrategies

### Cypress

- **Cypress** is used for **end-to-end (E2E) testing**, simulating real user interactions to validate that the entire system behaves as expected.

[End-to-End Testing](endToEndTesting.md)

## Static Code Analysis

- **Snyk** is used to detect and manage security vulnerabilities in project dependencies. It integrates into the development and CI/CD process to continuously scan for known threats and suggest appropriate fixes.

### SonarQube
- **SonarQube** is integrated into our workflow to analyze code for quality, maintainability, bugs, and vulnerabilities.

[Static Code Analysis](staticCodeAnalysis.md)

## APM (Application Performance Monitoring)
- We also assess the application's performance using **Application Performance Monitoring (APM)** tools and track **benchmarks** to identify and optimize slow or resource-intensive operations.

### Performance and benchmarks
- **New relic** is used to monitor application performance and run benchmarks. It provides detailed insights into response times, system throughput, and resource usage, helping us identify and resolve performance bottlenecks efficiently.
- *Note: New Relic is not active on the production environment. It is currently only integrated into the dedicated `udviklingsmiljø` branch for testing and performance analysis during development.*
