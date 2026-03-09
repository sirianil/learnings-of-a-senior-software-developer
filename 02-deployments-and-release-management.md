# Chapter 2: Deployments & Release Management

## 2.1 Deployment Best Practices

- **Track every deployment**: Log what was deployed, by whom, and when. This is the first thing to check during an incident.
- **Use feature flags**: Gate new features behind flags to decouple deployment from release. This allows you to roll back behavior instantly without redeploying code.
- **Keep deployments small and frequent**: Large batches of changes are harder to debug. Prefer small, atomic commits and deployments.

## 2.2 Rollout Strategies

Minimize blast radius by rolling out changes gradually:

| Strategy | Description |
|---|---|
| **Canary** | Route a small percentage of traffic to the new version first |
| **Percentage rollout** | Gradually increase traffic to the new version (e.g., 5% → 25% → 100%) |
| **Geography-based** | Roll out to lower-risk regions first before expanding globally |
| **Time-based** | Deploy during low-traffic windows to reduce exposure |
| **Blue/Green** | Maintain two identical environments; switch traffic instantly |

## 2.3 Rollbacks

- Define and document a rollback procedure before every significant deployment.
- Prefer **conservative rollbacks**: when in doubt, revert first and investigate second.
- Ensure rollbacks are tested — a rollback that doesn't work is worse than none.
- Target rollback time should be minimal (aim for under 5 minutes for critical services).

## 2.4 Feature Flags

Feature flags (feature toggles) are a powerful mechanism to:
- Enable/disable features without a code deployment.
- Perform A/B testing or gradual rollouts.
- Kill a misbehaving feature in production instantly.

CI/CD gates can enforce that significant changes include a feature flag before merging.

## 2.5 Deploy Freezes

Be aware of and communicate:
- **Scheduled freeze windows** (e.g., around major holidays, quarter-end events).
- **Dependent team deployments** that may affect your service.
- **Upstream migrations** that could alter data formats or APIs your service depends on.
