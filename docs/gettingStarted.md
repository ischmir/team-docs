# Getting Started

## Introduction

Welcome to the team. This page will tell you everything you need to know when getting started. This guide will walk you through the prerequisites needed, how to install them, setting up your development enviroment, how to run et locally and common troubleshooting errors.
after this guide you will be all set and ready to code.

## Prerequisites

Before you start you will need to have the following technologies installed. But don't worry we will guide you through the installation.

- Git – We use GitHub for version control. Make sure you have a GitHub account and Git installed on your machine.

- Node.js – Enables running JavaScript outside the browser and powers many development tools.

- Vite – A fast and modern build tool that provides a smooth and efficient development experience.

- Vue – We use Vue 3 with the Composition API as our frontend framework.

- Sass – A CSS preprocessor that helps write more maintainable and flexible stylesheets.

- Pinia – Our state management library for managing app-wide reactive data in Vue.

- ESLint – Ensures consistent code style and helps catch errors early by linting your codebase.

- SonarCloud/SonarQube – A cloud-based tool to analyze code quality, detect bugs, vulnerabilities, and code smells.

- Snyk – Scans project dependencies for known security vulnerabilities.

- Cypress – Used for end-to-end testing to verify the application works as expected from a user’s perspective.

- Jest – Used for unit testing to verify individual functions and components behave correctly.

- vite-svg-loader – Allows importing SVG files as Vue components, making it easier to work with SVG graphics in your app.

- vue-router – The official router for Vue.js, enabling navigation and routing in the web application.

- firebase – Google’s platform for backend services like authentication, database, and hosting used in the app.

- start-server-and-test – A utility that starts your development server and runs tests automatically once the server is ready.

- vite-plugin-vue-devtools – A plugin that integrates Vue Devtools into Vite for easier debugging during development.

## Installation
This guide will help you install all the necessary tools and dependencies required for the project.

### ⚙️ Global Prerequisites

These tools must be installed **globally on your machine**.

#### Git

We use GitHub for version control.  
Make sure you have a GitHub account and Git installed.

**Install Git**

- Download from [git-scm.com](https://git-scm.com/downloads)
- Verify installation:

```bash
git --version
```

#### Node.js (includes npm)

Node.js allows you to run JavaScript outside the browser and is required for installing project dependencies.

Install Node.js (LTS recommended):

Download from nodejs.org

Verify installation:

```bash
node --version
npm --version
```

## 📦 Install Project Dependencies

Once Git and Node.js are installed:

**Clone the repository:**

```bash
git clone https://github.com/your-org/your-project.git
cd your-project
Install all dependencies:
```

```bash
npm install
```

This will automatically install all required packages listed in package.json, including:

- Git  
- Node.js  
- Vite  
- Vue  
- Sass  
- Pinia  
- ESLint  
- SonarCloud/SonarQube  
- Snyk  
- Cypress  
- Jest  
- vite-svg-loader  
- vue-router  
- firebase  
- start-server-and-test  
- vite-plugin-vue-devtools  

No need to install these manually — npm install handles everything.

## Running the Project

### Start the Development Server

```bash
npm run dev
The app will be available at: http://localhost:5173 (or another port if already in use).
```

### Run Tests

**End-to-End (E2E) Tests with Cypress:**

```bash
npm run test:e2e
```

 
[Click here to read more about End-to-End tests](endToEndTesting.md)

**Unit Tests with Jest or Cypress Component Testing:**

```bash
npm run test:unit
```

**Lint the Codebase**

```bash
npm run lint
```

## Troubleshooting
If you are having trouble reach out to a team member for help.