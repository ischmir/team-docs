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

