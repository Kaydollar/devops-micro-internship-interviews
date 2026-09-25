# Week 11 — Observability

Observability is what keeps you from flying blind in production. Interviews test whether you understand the three pillars — metrics, logs, traces — and how they work together to answer different kinds of questions. Knowing Prometheus, Grafana, and FluentBit by name is the start; knowing how Prometheus discovers pods, how FluentBit ships logs without touching your app, and how you wire Alertmanager to PagerDuty is what proves you have operated a real system.

**Appears in:** mid-to-senior rounds for DevOps, SRE, and platform engineer roles. Senior interviews often present an incident scenario and ask how you would have caught it sooner.

## Discussion

New questions and community answers → **[GitHub Discussions → Observability Q&A](../../discussions)**

## Questions

| # | Question | Difficulty | Link |
|---|---|---|---|
| 1 | Metrics vs Logs vs Traces — how they work together | entry | [Open](questions/01-metrics-logs-traces-otel.md) |
| 2 | What are the three pillars of observability? | easy | [Open](questions/02-three-pillars-of-observability.md) |
| 3 | How does Prometheus scrape metrics from your services? | medium | [Open](questions/03-how-prometheus-scrapes-metrics.md) |
| 4 | What do you do when an alert fires in production? | medium | [Open](questions/04-what-to-do-when-alert-fires-production.md) |
| 5 | How does Prometheus scrape metrics from pods in EKS? | medium | [Open](questions/05-prometheus-scraping-in-eks.md) |
| 6 | How does FluentBit collect and forward logs from pods in EKS? | medium | [Open](questions/06-fluentbit-log-aggregation-eks.md) |
| 7 | How do you set up alerting with Prometheus and Alertmanager? | medium | [Open](questions/07-alerting-with-prometheus-alertmanager.md) |
