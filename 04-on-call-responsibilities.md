# Chapter 4: On-Call Responsibilities

On-call is a critical rotation for maintaining system health and being the first line of response for production issues.

## 4.1 Core Responsibilities

1. **Deployments**: Oversee and coordinate deployments during your rotation. Verify health after each one.
2. **Active SEVs**: Respond to and drive resolution of any active incidents.
3. **Customer forums & support queues**: Monitor and respond to customer-reported issues in a timely manner.
4. **System health monitoring**: Periodically review dashboards and ensure all services are operating within normal parameters.
5. **SLO tracking**: Verify that the system is meeting its Service Level Objectives (SLOs). If an SLO has slipped, understand why and ensure there is a plan to recover.
6. **Upcoming events awareness**: Know about upcoming deployments, migrations, traffic spikes (e.g., product launches, campaigns), or deploy freezes during your rotation.
7. **Maintenance tasks**: Identify and address infrastructure or dependency upgrades that fall due during the rotation.

## 4.2 Service Level Objectives (SLOs)

An SLO is a measurable target for a service's reliability (e.g., 99.999% uptime, p99 latency < 200ms).

When an SLO is breached:
- Was it caused by an incident? Document it.
- Was it a gradual drift? Identify the underlying cause and create a remediation plan.
- Does the SLO threshold need re-evaluation based on realistic baselines?

## 4.3 On-Call Handoff

A structured handoff ensures continuity. Cover the following at every rotation handoff:

- **Open incidents**: Status and current owner.
- **Recent deployments**: What went out, and anything to watch.
- **Ongoing investigations**: Any anomalies currently being monitored.
- **Upcoming events**: Scheduled deployments, migrations, or traffic events.
- **Pending action items**: From recent postmortems or open maintenance windows.
