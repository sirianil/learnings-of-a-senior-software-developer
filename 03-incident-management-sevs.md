# Chapter 3: Incident Management (SEVs)

## 3.1 Severity Definitions

Defining severity levels consistently ensures teams respond proportionally.

| SEV Level | Definition | Example |
|---|---|---|
| **SEV-1** (Critical) | A significant subset of users are completely unable to achieve a core goal | Checkout is down for all users |
| **SEV-2** (Major) | A meaningful subset of users are degraded in achieving a core goal | Checkout is slow for 20% of users |
| **SEV-3** (Minor) | A small subset of users are affected, or the impact is non-critical | An error message shows incorrect text |

> **Key principle**: Err on the side of declaring a higher SEV. It is better to escalate and downgrade than to under-respond.

## 3.2 How to Declare a SEV

- Any engineer can declare a SEV. There should be a low bar to doing so.
- Notify the on-call engineer and relevant stakeholders immediately.
- Create a dedicated incident channel (e.g., `#incident-YYYY-MM-DD-description`).
- Assign a clear **Incident Commander (IC)** to coordinate the response.

## 3.3 First Order of Operations When a SEV Is Declared

1. **Pull in the right stakeholders** — on-call lead, engineering manager, product manager, and any team that might be relevant.
2. **Check recent deployments and configuration changes** — the leading cause of incidents is something that recently changed.
3. **Conservative rollback if required** — if a deployment is suspect, roll back immediately rather than waiting for a definitive root cause.
4. **Communicate that you are investigating** — send an early update to stakeholders and affected users (even if you have no root cause yet).
5. **Observe dashboards and logs** — look at error rates, latency spikes, traffic patterns, and recent log anomalies.
6. **Form a hypothesis** — propose the most likely cause, then validate or disprove it with data.
7. **Mitigate first, fix second** — restore service stability before fixing the underlying bug.
8. **All-clear communication** — once resolved, notify stakeholders that the incident is closed and that a postmortem is forthcoming.

## 3.4 Stakeholder Communication During an Incident

- Send updates on a regular cadence (e.g., every 30 minutes) even if there is no new information — silence is worse than uncertainty.
- Use a status page or shared channel visible to both internal teams and customers.
- Keep messages factual and avoid speculation about root cause in customer-facing updates.

## 3.5 Postmortem

### Client-Facing Report
A concise, jargon-free summary of what happened, how long it lasted, how many users were affected, and what steps are being taken to prevent recurrence.

### Internal Postmortem (5 Whys + Blameless Review)

The goal is systemic improvement, not blame. Ask:

- **Incident timeline & walkthrough**: What happened, in what order, and what actions were taken?
- **Time to detection**: How were we notified? Was it automated monitoring, a customer report, or internal discovery? Could detection time have been halved?
- **Time to recovery**: Could we have recovered twice as fast? What slowed us down?
- **Deployment & configuration**: Was there a recent deployment or configuration change involved? Was a feature flag in place that could have protected this rollout?
- **Backlog & prioritization**: Was there a known issue in the backlog that, if prioritized, could have prevented this?
- **Luck factor**: Could the impact have been significantly worse? Did we get lucky this time?
- **Tooling gaps**: Were there additional tools or visibility that would have helped?
- **Action items**: What concrete tasks need to be done, and how are we prioritizing them?

All action items should be tracked in your ticketing system with owners and due dates.
