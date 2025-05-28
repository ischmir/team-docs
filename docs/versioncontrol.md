# Changelog and Version Control

## Introduction

This document outlines the version control practices for the project and provides a changelog to track the history of changes. By following these guidelines, we ensure a consistent and organized workflow.

<!-- link to changelog -->

## Version Control Guidelines

### Branching Strategy

#### Naming Conventions

- **Main Branch:** Contains production-ready code.
- **Feature Branches:** Used for developing new features (e.g., `feature/feature-name`).
- **Bugfix Branches:** Used for fixing bugs (e.g., `bugfix/bug-description`).
- **Documentation:** Used for writing documentation (e.g., `docs/update-section-name`).
- **Refactor:** Used for refactoring code  (e.g., `refactor/component-or-scope`).
- **Test:** Used for testing code (e.g., `test/test-name-component-or-scope`).
- **Chore:** Used for maintenance tasks (e.g., `chore/task-name-component-or-scope`).

### Commit Message Conventions

- Use semantic commit messages:
  - `feat:` for new features.
  - `fix:` for bug fixes.
  - `docs:` for documentation updates.
  - `refactor:` for code refactoring.
  - `test:` for adding or updating tests.
  - `chore:` for maintenance tasks.

### Pull Request Process

1. Create a pull request for merging feature/bugfix branches into the main branch.
2. Request a code review from at least one team member.
3. Ensure all tests pass before merging.

## Changelog

### v1.0.0 - 2025-03-18

- Initial release of the project.
- Added core features:
  - User authentication.
  - Dashboard with data visualization.
  - API integration.

### v1.1.0 - 2025-03-25

- Added new features:
  - Dark mode support.
  - Export data functionality.
- Fixed bugs:
  - Resolved issue with login form validation.

## Best Practices

- Commit frequently with meaningful messages.
- Avoid committing sensitive data (e.g., API keys, passwords).
- Keep your feature branch up-to-date with the main branch.
- Resolve merge conflicts promptly.