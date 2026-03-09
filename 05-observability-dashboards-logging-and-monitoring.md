# Chapter 5: Observability: Dashboards, Logging & Monitoring

## 5.1 Dashboards

A good observability dashboard (e.g., Datadog, Grafana) should give you an at-a-glance view of system health.

**Key metrics to monitor:**

- **HTTP 2xx rate per endpoint**: A drop in successful responses is a leading indicator of trouble, even before error rates rise.
- **HTTP 5xx rate per endpoint**: High server error rates indicate failures in your service.
- **HTTP 4xx rate per endpoint**: Can indicate a bug, an upstream misconfiguration, or a potential attack (e.g., credential stuffing, bad bots).
- **Queries Per Second (QPS)**: A drop in QPS can indicate an upstream issue — traffic may have stopped reaching your service entirely.
- **Endpoint latency (p50, p95, p99)**: Track latency percentiles. Averages hide the tail latency that affects your worst-off users.
- **Error budget burn rate**: How quickly are you consuming your error budget relative to your SLO?

> **Tip**: An unexplained *dip* in requests or 2xx responses is just as concerning as a spike in errors. Always investigate anomalous patterns in both directions.

## 5.2 Automated Alerting

Alerts should be actionable and minimize false positives. Tier them by urgency:

| Alert Priority | Notification Channel |
|---|---|
| **Warn** (non-urgent) | Slack message or email |
| **Triggered** (urgent) | PagerDuty page + Slack |

**Recommended automated monitors:**

- **High 5xx error rate**: Set thresholds (e.g., > 1% over 5 minutes) to avoid false positives from transient errors.
- **High 4xx error rate**: Useful for detecting attacks or sudden API incompatibilities.
- **Zero traffic / no requests**: May indicate an upstream routing failure or misconfigured load balancer.
- **Endpoint latency spike**: Alert on p99 latency crossing defined thresholds.
- **Pod restarts**: Frequent pod restarts signal crashes that need attention.
- **Certificate expiry**: Alert well in advance (e.g., 30 days) of TLS certificate expiration.
- **Dependency package vulnerabilities**: Automated tools (e.g., Dependabot, Snyk, OWASP Dependency-Check) should flag security vulnerabilities in dependencies.

> **Threshold calibration**: Understand your baseline. It may be normal to see 2–3 5xx errors per second. Set thresholds above the noise floor, but low enough to catch real issues early.

## 5.3 Logging

Good logs are your most powerful debugging tool. Follow these principles:

### Log Levels

| Level | When to Use |
|---|---|
| `ERROR` | Unexpected failures that require investigation |
| `WARN` | Unexpected conditions that are handled but worth knowing |
| `INFO` | Normal, significant application events (startup, config loaded, request completed) |
| `DEBUG` | Detailed diagnostic information, disabled in production by default |

### What to Log
- Request IDs (for distributed tracing across services).
- User/session identifiers (anonymized or hashed where required by privacy policy).
- Relevant input parameters and outcomes for significant operations.
- Timing data for slow operations.
- All error stack traces with context.

### What NOT to Log
- Raw passwords, tokens, API keys, or PII (names, emails, SSNs).
- High-volume noise that obscures important signals.

### Structured Logging
**Structured logging** (JSON format) is strongly preferred over plain-text logs — it makes querying and alerting in tools like Datadog, Splunk, or CloudWatch far easier.
