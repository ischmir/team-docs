# Git Workflow
- Make small incremental changes
- Commit Frequently

## Continuous Integration / Deployment

We use **GitHub Actions** to automate testing and deployment through a streamlined **CI/CD pipeline**. Every code change is verified, previewed, and deployed with minimal friction — ensuring stability, speed, and quality.

### Workflow Overview

- **`PR.yml`**  
  Runs on every pull request. Installs dependencies, builds the project, runs testing, and runs linting. Blocks merging unless all checks pass, which ensuring code quality from the start.

- **`firebase-hosting-pull-request.yml`**  
  Builds the app and deploys a **preview version** to Firebase Hosting. Lets the team review changes live before they hit production.

- **`firebase-hosting-merge.yml`**  
  Runs on every push to `main`. Builds and deploys the latest version **directly to production** via Firebase Hosting

### Why It Matters

- **Automatic checks** on every pull request.
- **Live previews** for faster feedback.
- **Instant production deploys** on merge.
- **No stale branches** — merged branches auto-delete.

This setup enforces code quality, reduces human error, and keeps our production site always up-to-date. CI/CD isn’t just a tool — it’s our safety net and speed boost.


## Commits

- Github messages should be present tense!
- Messages should be short and describe what they do, max 50 characters.
- Commit messages can be multi-line, but ALWAYS start with a one-line description.
- Maximum 72 characters per line.

### Examples of good and bad commit messages
#### DO
- ✅ "Fix typo in dashboard title"
- ✅ "Refactor login code for clarity"
- ✅ "Update member report format for clarity"
- ✅ "Fix issue causing incorrect user permissions"
- ✅ "Refactor dashboard styles for consistency"
#### DON'T
- ❌ "fix typo"
- ❌ "update Update login code"
- ❌ "Updates member report, we should discuss if this is rigth next week"
- ❌ Fixed a bug
- ❌ Update stuff

