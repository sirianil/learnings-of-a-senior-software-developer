# Chapter 8: Dependency Management

## 8.1 Evaluating a New Dependency

Before adding any external library or service, perform a due-diligence review:

- **Who owns it?** Is it backed by a company, a foundation, or a solo maintainer?
- **Is it actively maintained?** Check the last commit date, open issue response times, and release cadence.
- **What is the community's stance?** Is it widely adopted? Are there known alternatives that are considered more reliable?
- **Does it follow standard guidelines?** Does it use semantic versioning? Does it have a clear deprecation policy?
- **What is its security track record?** Check CVE history and how quickly vulnerabilities have been patched.
- **What is the license?** Ensure it's compatible with your product's licensing requirements.

> **Rule of thumb**: Avoid adding dependencies that are undermaintained or have a small community. The cost of a vulnerable or abandoned dependency is far higher than the time saved by using it.

## 8.2 Keeping Dependencies Up to Date

- Use automated tools (e.g., **Dependabot**, **Renovate**) to receive PRs when dependency updates are available.
- Set up automated alerts when packages reach **end-of-life** or when a **CVE is disclosed** against a version you're using.
- Treat dependency updates as first-class work — allow time for them in sprint planning.
- Pin dependency versions in lockfiles for reproducible builds; use ranges only where intentional.

## 8.3 Separation of Concerns

Design your systems so that internal modules are loosely coupled. Avoid a monolithic `utils/` or `helpers/` directory — these become dumping grounds for unrelated code and make codebase navigation difficult. Instead, group code by domain or responsibility (e.g., `auth/`, `billing/`, `notifications/`).
