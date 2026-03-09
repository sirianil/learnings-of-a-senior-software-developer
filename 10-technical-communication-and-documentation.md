# Chapter 10: Technical Communication & Documentation

## 10.1 Design Docs & One-Pagers

Before starting any significant engineering project, write a **design doc** or **one-pager**:

- **What problem are we solving?** (Context and motivation)
- **What are the proposed solutions?** (At least two options, with trade-offs)
- **What is the recommended approach?** (And why)
- **What are the risks?** (Security, scalability, operational)
- **What does success look like?** (Measurable outcomes)

Get the doc reviewed and approved by relevant teammates before starting implementation. This surfaces problems early and builds shared understanding.

## 10.2 Technical Reference Documentation (for Developer-Facing Products)

If you are building a product or API consumed by other developers:

- **Clarity and completeness**: Document every endpoint, parameter, error code, and expected behavior.
- **Consistency**: Use consistent naming conventions, response formats, and error structures across your entire API. Inconsistency creates friction for integrators.
- **Consistency between docs and code**: Outdated documentation is worse than no documentation. Consider using **documentation generation tools** that derive docs directly from code (e.g., OpenAPI/Swagger, TypeDoc, Sphinx).
- **Error design**: Make errors consistent and informative. Similar problems should produce similar error shapes so that handling them on the client side is predictable.

## 10.3 FAQs and Team Onboarding

- Maintain a **team FAQ** document for common questions new team members ask. Update it after every onboarding cycle.
- Document: how to set up the dev environment, how to deploy, who to contact for what, and where key resources live.
- Good onboarding docs reduce ramp-up time and free senior engineers from repetitive explanations.

## 10.4 Oral and Written Communication

- **Make requests clear**: State what you need, why you need it, and by when.
- **Be concise**: Respect people's time. Longer does not mean more thorough.
- **Public team Slack channels**: Use a public channel per team so conversations are discoverable and searchable — not buried in DMs.
- **Async by default**: Not everything needs a meeting. Prefer async communication (written updates, Loom videos) to keep engineers in flow.
