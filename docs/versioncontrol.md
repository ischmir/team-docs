# Versioncontrol

## Introduction

This document outlines the versioncontrol practices for the project. By following these guidelines for branching and commits, we ensure a consistent and organized workflow.

## Version Control Guidelines
We use **Git** for version control, with **GitHub** as our hosting platform. 
This allows for efficient collaboration, history tracking, and integration with CI/CD pipelines.

### Branching Strategy

We use **GitHub Flow** as our branching strategy to ensure a structured and conflict-free collaboration process.

#### Workflow

- All new work is done in **feature branches**, created from the `main` branch.
- When a feature is complete, a **pull request (PR)** is opened to merge the changes into `main`.
- Each PR must undergo:
  - **Code review** by at least one team member.
  - **Automated status checks** (e.g., build, linting, tests).
- Only when all checks pass and the code is approved, it can be merged.
- The `main` branch always contains stable, deploy-ready code.

#### GitHub Branch Protection Rules

To safeguard our codebase and enforce quality control, we apply the following rules to the `main` branch:

- **Restrict deletions:** Prevents accidental deletion of the `main` branch.
- **Require pull request before merging:** Direct commits to `main` are blocked.
- **Require status checks to pass:** Ensures code meets quality standards before merging.
- **Block force pushes:** Protects commit history from being overwritten.

These rules are tightly integrated into our CI/CD pipeline and help maintain a high standard of code quality across the team.


#### Naming Conventions

- **Main Branch:** Contains production-ready code.
- **Feature Branches:** Used for developing new features (e.g., `feature/feature-name`).
- **Bugfix Branches:** Used for fixing bugs (e.g., `bugfix/bug-description`).
- **Documentation:** Used for writing documentation (e.g., `docs/update-section-name`).
- **Refactor:** Used for refactoring code  (e.g., `refactor/component-or-scope`).
- **Test:** Used for testing code (e.g., `test/test-name-component-or-scope`).
- **Chore:** Used for maintenance tasks (e.g., `chore/task-name-component-or-scope`).

## Commits

- Github commit messages should be present tense!
- Messages should be short and describe what they do, max 50 characters.
- Commit messages can be multi-line, but ALWAYS start with a one-line description.
- Use semantic commit messages:

### Examples of good and bad commit messages

#### DO

- ✅ "`feat:` for new features e.g. drag and drop feature"
- ✅ "`fix:` for bug fixes e.g. typo in dashboard title"
- ✅ "`docs:` for documentation updates e.g. branching strategy"
- ✅ "`refactor:` for code refactoring e.g. login code for clarity"
- ✅ "`hotfix:` for bugfixes on main e.g. no example given"
- ✅ "`test:` for adding or updating tests"
- ✅ "`chore:` for maintenance tasks."

#### DON'T

- ❌ "fix typo"
- ❌ "update Update login code"
- ❌ "Updates member report, we should discuss if this is rigth next week"
- ❌ Fixed a bug
- ❌ Update stuff

### Pull Request Process

1. Create a pull request for merging feature/bugfix branches into the main branch.
2. Request a code review from at least one team member.
3. Ensure all tests pass before merging.

## Best Practices

- Commit frequently with meaningful messages.
- Avoid committing sensitive data (e.g., API keys, passwords).
- Keep your feature branch up-to-date with the main branch.
- Resolve merge conflicts promptly.