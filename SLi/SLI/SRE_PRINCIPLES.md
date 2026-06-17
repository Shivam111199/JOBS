Google SRE introduced many concepts beyond the Four Golden Signals. Here are the most important ones:

## 1. Service Level Indicators (SLIs)

An **SLI** is a quantitative measure of service performance.

Examples:

* Request success rate
* API latency (95th percentile)
* Availability percentage
* Throughput

Example:

* 99.95% of requests return HTTP 200 within 300 ms

SLIs answer: **"How are we measuring service quality?"**

---

## 2. Service Level Objectives (SLOs)

An **SLO** is the target value for an SLI.

Examples:

* 99.9% availability per month
* 95% of requests under 200 ms
* Error rate below 0.1%

Example:

* SLI: API availability
* SLO: 99.95% uptime

SLOs answer: **"What level of reliability are we aiming for?"**

---

## 3. Service Level Agreements (SLAs)

An **SLA** is a contractual commitment to customers.

Example:

* 99.9% uptime guaranteed
* Service credits if uptime falls below target

Relationship:

```
SLI → measured metric
SLO → internal target
SLA → external promise
```

---

## 4. Error Budgets

One of the most influential SRE concepts.

If your SLO is 99.9% availability:

* Allowed downtime = 0.1%
* That 0.1% is your **error budget**

Monthly example:

* Total minutes = 43,200
* 0.1% downtime allowed = 43.2 minutes

Usage:

* If budget remains → release features faster
* If budget is exhausted → prioritize reliability

This creates balance between:

* Innovation
* Stability

---

## 5. Toil

**Toil** is repetitive, manual operational work.

Examples:

* Restarting services repeatedly
* Manually provisioning servers
* Running the same recovery steps daily

Characteristics:

* Manual
* Repetitive
* Automatable
* Doesn't create lasting value

Goal:

* Reduce toil through automation.

---

## 6. Observability

Ability to understand internal system state from outputs.

Three pillars:

### Metrics

Numerical measurements.

Examples:

* CPU
* Memory
* Request count

### Logs

Event records.

Examples:

* Application logs
* Audit logs
* Error logs

### Traces

Request flow through distributed systems.

Example:

```
User
  ↓
API Gateway
  ↓
Auth Service
  ↓
Payment Service
  ↓
Database
```

Distributed tracing helps locate bottlenecks.

---

## 7. Alerting Philosophy

Google SRE discourages alerts based solely on infrastructure metrics.

Bad:

* CPU > 80%

Better:

* User requests failing
* SLO burn rate increasing
* Latency exceeding target

Alert on **user impact**, not just resource usage.

---

## 8. Burn Rate

Measures how quickly you're consuming your error budget.

Example:

SLO:

* 99.9% availability

Error budget:

* 0.1%

Current error rate:

* 1%

Burn rate:

```
1% / 0.1% = 10x
```

Meaning:

* Error budget will be exhausted 10 times faster than expected.

Useful for early warning alerts.

---

## 9. Incident Management

Key concepts:

### Severity Levels

* SEV1: Major outage
* SEV2: Significant degradation
* SEV3: Minor impact

### Incident Commander

Single person coordinating response.

Responsibilities:

* Communication
* Prioritization
* Coordination

### Postmortem

Written analysis after incident.

Focus:

* What happened?
* Why?
* How to prevent recurrence?

Not:

* Who to blame

---

## 10. Blameless Postmortems

A core SRE principle.

Instead of:

❌ "Who caused the outage?"

Ask:

✅ "Why did our system allow this mistake to cause an outage?"

Focus on:

* Process improvements
* Better automation
* Better safeguards

---

## 11. Capacity Planning

Predict future resource needs.

Examples:

* CPU growth
* Storage growth
* Network growth
* Database growth

Questions:

* Can we handle Black Friday traffic?
* What happens if traffic doubles?

---

## 12. Canary Releases

Deploy changes to a small percentage of users first.

Example:

```
1% users
  ↓
10%
  ↓
50%
  ↓
100%
```

Benefits:

* Limits blast radius
* Detects issues early

---

## 13. Availability vs Reliability

Availability:

```
Service up or down?
```

Reliability:

```
Does service consistently meet expectations?
```

Example:

A service can be:

* 99.99% available
* But extremely slow

Available ≠ Reliable

---

## 14. Production Readiness Review (PRR)

Before launching a service, evaluate:

* Monitoring
* Alerting
* Capacity planning
* Runbooks
* Backups
* Disaster recovery

Goal:

* Ensure operational readiness before production.

---

## 15. Runbooks and Playbooks

### Runbook

Step-by-step instructions.

Example:

```
Database failover procedure
```

### Playbook

Response strategy for broader scenarios.

Example:

```
DDoS attack response plan
```

---

### The "must-know" SRE concepts for interviews

If you're preparing for SRE, DevOps, Platform Engineering, or Production Engineering interviews, focus on:

1. Four Golden Signals
2. SLI / SLO / SLA
3. Error Budgets
4. Burn Rate Alerts
5. Observability (Metrics, Logs, Traces)
6. Incident Management
7. Blameless Postmortems
8. Toil Reduction & Automation
9. Capacity Planning
10. Canary / Blue-Green Deployments

These form the core of modern reliability engineering practices and are frequently discussed in interviews and real-world operations.
