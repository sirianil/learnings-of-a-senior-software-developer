# Chapter 12: Team & Cross-Functional Collaboration

## 12.1 Working with Platform & Infrastructure Teams

Platform and infrastructure teams own shared foundations (compute, networking, CI/CD tooling, observability). To work with them effectively:

- **Engage early**: Loop them in during design reviews if your work touches infrastructure.
- **Understand their roadmap**: Know what they're changing so you're not surprised.
- **Follow their guidelines**: Use the patterns and tools they provide rather than building your own unless there's a compelling reason.
- **Be a good consumer**: Report issues clearly, with reproduction steps and logs.

## 12.2 Buy vs. Build

Before building something from scratch, ask:

- Does a well-maintained open-source or commercial solution already exist?
- What is the total cost of ownership of building vs. buying? (Include ongoing maintenance, not just build time.)
- Does the build give us a meaningful competitive advantage, or is it undifferentiated infrastructure?
- Does the team have the expertise to build and operate this reliably?

> **General rule**: Buy or adopt for undifferentiated infrastructure. Build for core product differentiators.

## 12.3 Workflow Automation

Connect your tools so they work together seamlessly:

- **Ticketing ↔ Communication**: Integrate your ticketing system (e.g., Jira, Linear) with your chat tool (e.g., Slack) so customer requests or alerts automatically create tickets.
- **Alerts ↔ Incident Management**: Wire monitoring alerts directly into your on-call rotation tool (e.g., PagerDuty).
- **PRs ↔ Tickets**: Link PRs to tickets so code changes are traceable to product decisions.

## 12.4 Engineering Culture Principles

- **Blameless culture**: When things go wrong, focus on fixing systems, not punishing people.
- **Psychological safety**: Engineers should feel safe raising concerns, asking questions, and admitting mistakes without fear.
- **Knowledge sharing**: Regular tech talks, pairing sessions, and written post-mortems spread expertise across the team.
- **Sustainable pace**: On-call burden should be distributed fairly. A team that burns out cannot maintain a reliable system.
