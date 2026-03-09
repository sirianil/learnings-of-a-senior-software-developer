# Chapter 7: CI/CD Pipelines

A robust CI/CD pipeline is the backbone of sustainable software delivery. Every PR and merge should automatically run through a pipeline that validates quality before code reaches production.

## 7.1 What a CI Pipeline Should Do

1. **Run linters** — enforce code style and catch static errors.
2. **Run tests** — unit, integration, and any fast E2E tests.
3. **Enforce code coverage** — fail if coverage drops below threshold.
4. **Check for feature flags** — if the change is significant, a feature flag should be present.
5. **Security scanning** — scan for known vulnerabilities in dependencies (e.g., `npm audit`, Snyk).
6. **Build & package** — compile, containerize, or bundle the application.
7. **Clear failure reporting** — link directly to the failing line of code or test log, not just a generic "build failed" message.

## 7.2 What a CD Pipeline Should Do

1. **Deploy to staging automatically** on merge to main.
2. **Run smoke tests** post-deployment to verify the environment is healthy.
3. **Require manual approval** before promoting to production (for most teams).
4. **Support rollback**: One-click rollback to the previous version.
5. **Notify on success/failure**: Ping the deploying engineer and on-call channel.

## 7.3 PR Approval Gates

- Require at least **one (or two) approvals** from teammates before merging.
- Require **CI to pass** before merging (no green build = no merge).
- Configure **CODEOWNERS** so the right domain experts are notified for sensitive changes.
- Consider **required reviewers** for security-sensitive code paths (e.g., auth, billing).

## 7.4 Build Tools

Use established build and package management tools appropriate to your stack:

- **Monorepo tooling**: Tools like **Turborepo**, **Nx**, or **Bazel** can manage task orchestration, caching, and incremental builds across large repositories.
- **Package managers**: **yarn**, **pnpm**, **npm** for Node.js; **pip**/**poetry** for Python; **maven**/**gradle** for Java.
- Ensure build tooling is configured to work reliably in CI (use lockfiles, disable interactive prompts, set deterministic environments).
