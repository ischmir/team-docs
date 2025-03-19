# Changelog and Version Control

## Introduction

This document outlines the version control practices for the project and provides a changelog to track the history of changes. By following these guidelines, we ensure a consistent and organized workflow.

<!-- link to changelog -->

## Version Control Guidelines

### Branching Strategy

- **Main Branch:** Contains production-ready code.
- **Feature Branches:** Used for developing new features (e.g., `feature/feature-name`).
- **Bugfix Branches:** Used for fixing bugs (e.g., `bugfix/bug-name`).

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