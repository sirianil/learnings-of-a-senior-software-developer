# Chapter 9: Developer Productivity

## 9.1 Developer Playpen / Personal Environments

Make it easy for developers to spin up isolated environments for testing and proof-of-concept work:

- Provide tooling to create a **personal staging namespace** (e.g., `staging-<username>`) with minimal friction.
- These environments should mirror production configuration as closely as possible.
- Reduce the feedback loop from idea to running code. Long lead times discourage experimentation.

## 9.2 Git Workflows & Tools

**Feature branches**: Keep features isolated from the main branch until they're ready.

**Git Cherry-Pick**: Apply a specific commit from one branch to another without merging the full branch.

```bash
git cherry-pick <commit-hash>
```

Useful for backporting hotfixes to release branches.

**Git Worktrees**: Check out multiple branches of the same repository simultaneously in separate directories. This allows you to work on (or have an AI agent work on) several features in parallel without stashing or context-switching.

```bash
git worktree add ../feature-branch-dir origin/feature-branch
```

## 9.3 AI Productivity Tools

- Use AI coding assistants (e.g., Claude, Copilot) integrated into your IDE for code generation, test writing, and documentation.
- Combine **git worktrees** with AI agents: have separate worktrees checked out for different features and run AI agents on each independently.
- Use AI to help draft postmortems, design docs, or PR descriptions.

## 9.4 IDE Setup

Invest time in a well-configured IDE:
- Linters and formatters configured to run on save.
- Debugger configured for your primary service.
- Test runner integrated for quick feedback loops.
- Git integration for inline blame, diff viewing, and branch management.
