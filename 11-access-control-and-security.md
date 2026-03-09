# Chapter 11: Access Control & Security

## 11.1 Principle of Least Privilege

Grant the minimum permissions required for someone to do their job:

- **Read access** for those who only need to view data or configurations.
- **Write/admin access** for those who need to modify resources — review these grants regularly.
- **Application owners** and **database owners** should be explicitly named and maintained.
- Rotate and audit access credentials regularly.

## 11.2 Repository Access

- Use **CODEOWNERS** files to assign responsibility for sections of the codebase.
- Require branch protection on `main` / `production` branches — direct pushes should be disallowed.
- Log and audit access to production systems.

## 11.3 Secrets Management

- **Never commit secrets** (API keys, passwords, tokens) to source control.
- Use secrets management tools (e.g., AWS Secrets Manager, HashiCorp Vault, Kubernetes Secrets) to inject credentials at runtime.
- Rotate secrets on a regular schedule and immediately upon suspected compromise.
