# Chapter 6: Code Quality & Testing

## 6.1 Test Coverage

All production-grade code should have a comprehensive test suite. The standard testing pyramid:

| Test Type | Description | Scope |
|---|---|---|
| **Unit tests** | Test individual functions or classes in isolation | Narrow |
| **Integration tests** | Test how components interact (e.g., service + database) | Moderate |
| **End-to-End (E2E) tests** | Simulate full user flows through the system | Broad |
| **Acceptance tests** | Validate that the system meets defined business requirements | Broad |

**Code coverage:**
- Use coverage tools (e.g., Istanbul/NYC for JS, Coverage.py for Python, JaCoCo for Java) to track line and branch coverage.
- Set minimum coverage thresholds — PRs that fall below these thresholds should be blocked from merging.
- **Branch coverage** is more meaningful than line coverage — ensure conditional logic paths are tested.

## 6.2 Linters & Static Analysis

Linters enforce consistent code style and catch common errors automatically.

- **Configure linters in CI**: Lint failures should block merges.
- **Configure linters in your IDE**: Catch issues as you type, not at review time.
- **Git commit hooks** (e.g., using `husky` + `lint-staged`): Run linters before every commit to give developers fast feedback.

Common tools by language:

| Language | Linting / Formatting |
|---|---|
| JavaScript/TypeScript | ESLint, Prettier |
| Python | Ruff, Flake8, Black |
| Go | `golangci-lint`, `gofmt` |
| Java | Checkstyle, SpotBugs |

## 6.3 Code Reviews

Code reviews are a quality gate and a knowledge-sharing mechanism.

**As an author:**
- Keep PRs small and focused — one logical change per PR.
- Write a clear PR description explaining *what* changed and *why*.
- Self-review before requesting others.
- Link to the relevant ticket or design doc.

**As a reviewer:**
- Review for correctness, security, readability, test coverage, and consistency with existing patterns.
- Be kind and constructive — critique the code, not the person.
- Distinguish between blocking issues and non-blocking suggestions.
- Approve promptly to avoid blocking the team.

**Code ownership** (e.g., via `CODEOWNERS` files in GitHub): Assign owners to directories or files so the right people are automatically requested for review when those paths change.
