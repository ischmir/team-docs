# Architecture and Tech Stack Documentation

## Introduction

This document provides an overview of the system architecture and the technologies used in the project. It explains the structure of the system, the rationale behind technology choices.

## System Architecture

The system is built using a modern web application architecture, consisting of the following components:

**Frontend:** Built with Vue.js for a dynamic and responsive user interface.

**Database:** Firestore for real-time data storage and synchronization.

**Authentication:** Firebase Authentication for secure user login.

**State Management:** Pinia for managing application state.

## Tech Stack

### Vite

- **Purpose:** A modern build tool that serves and bundles your frontend application
- **Why Chosen:** Offers fast development startup and hot module replacement (HMR), making it ideal for modern JavaScript frameworks like Vue.
- **Usage:** Used as the development server and build tool for the project. It handles compiling, bundling, and optimizing Vue components, styles (like Sass), and static assets.

### Vue.js

- **Purpose:** Frontend framework for building user interfaces.
- **Why Chosen:** Provides a reactive and component-based architecture, making it easy to build and maintain the UI.
- **Usage:** Used for creating the dashboard and data visualization components.

### Sass

- **Purpose:** CSS preprocessor for styling.
- **Why Chosen:** Enables modular and reusable styles with variables, nesting, mixins and partials.
- **Usage:** Used for styling the application with a consistent design system.

### Firebase / Firestore

- **Purpose:** Backend-as-a-Service (BaaS) for real-time database and authentication.
- **Why Chosen:** Simplifies backend development and provides real-time data synchronization.
- **Usage:** Used for storing user data and managing authentication.

### Pinia

- **Purpose:** State management library for Vue.js.
- **Why Chosen:** Lightweight and easy to integrate with Vue.js.
- **Usage:** Used for managing global application state.

### ESLint

- **Purpose:** Linter for identifying and fixing code issues.
- **Why Chosen:** Ensures code quality and consistency.
- **Usage:** Configured to enforce coding standards across the project.

### Snyk

- **Purpose:** Security tool for identifying vulnerabilities in dependencies.
- **Why Chosen:** Helps maintain a secure codebase.
- **Usage:** Integrated into the CI/CD pipeline to scan for vulnerabilities.

### SonarCloud/SonarQube

- **Purpose:** Tool for analysing the quality of the code base.
- **Why Chosen:** Scans code for bugs, vulnerability, code smells and duplicates.
- **Usage:** Integrates in CI/CD pipeline for secure code quality on every commit or pull request.

### Cypress

- **Purpose:** Tool for end to end testing
- **Why Chosen:** Tests the entire user journey in the browser as a real user would experience it.
- **Usage:** Tests that the entire application works correctly — for example, login flow, forms, or navigation.

### Jest

- **Purpose:** Tool for unit testing
- **Why Chosen:** Tests individual functions or components for correct functionality.
- **Usage:** Used to secure that the logic in e.g. functions works as expected.
