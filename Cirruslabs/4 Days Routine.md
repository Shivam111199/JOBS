This JD is heavily focused on **Production Support + SRE Operations + Kubernetes + Monitoring**.

Based on your background (Graylog, Linux, incident handling, monitoring, production support), you already cover nearly **60-65%** of this role. The biggest gaps are:

1. Kubernetes troubleshooting
2. Prometheus internals
3. Grafana dashboards & alerting
4. SRE concepts (SLI/SLO/Error Budget)
5. Synthetic monitoring
6. Capacity planning & RCA
7. Distributed systems troubleshooting

# Priority Matrix

### 🔴 High Priority (70%)

* Linux Administration
* Linux Troubleshooting
* Kubernetes
* Containers (Docker)
* Prometheus
* Grafana
* Incident Management
* Production Support
* Monitoring & Alerting
* Bash Scripting
* Troubleshooting Scenarios

### 🟡 Medium Priority (20%)

* Python Automation
* Ansible Basics
* SLI/SLO
* RCA/Postmortem
* Capacity Planning
* Telemetry & Exporters
* Synthetic Monitoring

### 🟢 Low Priority (10%)

* ELK/OpenSearch/Loki
* GPU Monitoring
* DCGM
* CI/CD
* Git Workflow

---

# DAY 1

# Linux + Production Support Foundation

## 9:00 – 10:30

### Linux Fundamentals Revision

Topics:

* File permissions
* Ownership
* Users & Groups
* Soft/Hard links
* Systemd
* Cron jobs

Tasks:

✅ Create user

✅ Assign permissions

✅ Create cron entry

✅ Explain systemd service lifecycle

---

## 10:45 – 12:30

### Process Management

Commands:

```bash
ps
top
htop
kill
kill -9
pgrep
pkill
nohup
jobs
bg
fg
```

Tasks:

✅ Kill process on port 8080

✅ Find process consuming CPU

✅ Difference between SIGTERM and SIGKILL

---

## 1:30 – 3:30

### Linux Troubleshooting

Topics:

CPU

Memory

Disk

Load

Network

Tasks:

```bash
free -m
vmstat
iostat
sar
df -h
du -sh
uptime
```

Scenario Practice:

User says application is slow.

How will you troubleshoot?

---

## 3:45 – 5:30

### Networking

Commands:

```bash
ping
traceroute
mtr
curl
netstat
ss
dig
nslookup
tcpdump
```

Tasks:

Find:

* DNS issue
* Network issue
* Port issue

---

## 5:45 – 7:30

### Production Support

Topics:

Incident lifecycle

P1/P2/P3

Escalation Matrix

Runbooks

SOPs

Tasks:

Create:

Incident Response Flow

---

## 7:30 – 9:00

### Mock Interview

Answer 50 Linux Questions

You should answer without looking at notes.

---

# DAY 2

# Kubernetes + Containers

## 9:00 – 10:30

### Docker

Topics:

Image

Container

Volume

Network

Registry

Tasks:

```bash
docker ps
docker exec
docker logs
docker inspect
```

---

## 10:45 – 12:30

### Kubernetes Architecture

Topics:

Master Node

Worker Node

API Server

Scheduler

Controller Manager

ETCD

Kubelet

Kube Proxy

Tasks:

Draw Architecture

Explain component communication

---

## 1:30 – 3:30

### Kubernetes Objects

Topics:

Pod

Deployment

Service

Namespace

ConfigMap

Secret

DaemonSet

StatefulSet

Tasks:

Create YAML examples

Explain use cases

---

## 3:45 – 5:30

### Kubernetes Troubleshooting

Commands:

```bash
kubectl get pods
kubectl logs
kubectl describe
kubectl top
kubectl exec
kubectl get events
```

Scenarios:

Pod CrashLoopBackOff

ImagePullBackOff

OOMKilled

Pending Pod

Node Not Ready

---

## 5:45 – 7:00

### Resource Management

Topics:

Requests

Limits

HPA

Node Resources

Tasks:

Explain:

Why pod gets OOMKilled?

---

## 7:00 – 9:00

### Kubernetes Mock Interview

40 Questions

10 Troubleshooting Scenarios

---

# DAY 3

# Monitoring + Observability + SRE

## 9:00 – 10:30

### Monitoring Concepts

Topics:

Golden Signals

Latency

Traffic

Errors

Saturation

Tasks:

Define examples

---

## 10:45 – 12:30

### Prometheus

Topics:

Architecture

Pull Model

Exporter

TSDB

PromQL

Alertmanager

Tasks:

Explain complete flow

Node Exporter → Prometheus → Grafana

---

## 1:30 – 3:00

### PromQL

Practice:

```promql
up

node_cpu_seconds_total

rate()

increase()

sum()

avg()
```

Tasks:

Write 20 queries

---

## 3:15 – 5:00

### Grafana

Topics:

Dashboard

Variables

Panels

Alerts

Annotations

Tasks:

Create:

CPU Dashboard

Memory Dashboard

Node Health Dashboard

---

## 5:15 – 6:30

### Alerting

Topics:

Threshold

Alert Fatigue

Noise Reduction

Alert Routing

Tasks:

Design:

High CPU Alert

Disk Alert

Node Down Alert

---

## 6:30 – 7:30

### Logging

Quick Revision

ELK

OpenSearch

Graylog

Loki

Since you already know Graylog:

Spend only 1 hour.

---

## 7:30 – 9:00

### SRE Concepts

Topics:

SLI

SLO

SLA

Error Budget

Toil

Reliability

Synthetic Monitoring

RCA

Postmortem

---

# DAY 4

# Real Production Scenarios + Final Revision

## 9:00 – 11:00

### End-to-End Troubleshooting

Scenario 1

Website Down

Scenario 2

High CPU

Scenario 3

Disk Full

Scenario 4

Database Slow

Scenario 5

Kubernetes Pod Failure

---

## 11:15 – 1:00

### Automation

Bash

Python

Ansible

Tasks:

Write:

Disk Monitoring Script

Log Monitoring Script

Service Health Check Script

---

## 2:00 – 4:00

### RCA & Postmortem

Topics:

5 Why Analysis

Incident Timeline

Corrective Actions

Preventive Actions

Tasks:

Prepare one RCA document.

---

## 4:15 – 6:00

### Capacity Planning

Topics:

CPU Trends

Memory Trends

Storage Trends

Scaling

Forecasting

Tasks:

Explain how Prometheus data helps capacity planning.

---

## 6:00 – 7:00

### Agile/Kanban

Topics:

Sprint

Kanban

Blockers

Daily Standup

Status Reporting

Risk Reporting

---

## 7:00 – 9:00

### Final Interview Drill

### Round 1 (Linux)

20 Questions

### Round 2 (Kubernetes)

20 Questions

### Round 3 (Monitoring)

20 Questions

### Round 4 (SRE)

20 Questions

### Round 5 (Behavioral)

Tell me about yourself

Current Project

Major Incident Handled

Why SRE?

Why Leaving Current Company?

---

# Interview Topics Most Likely To Be Asked

Focus extra on these:

1. How do you troubleshoot a slow Linux server?
2. What happens when a pod crashes?
3. Difference between Deployment and StatefulSet?
4. Explain Prometheus architecture.
5. How Alertmanager works?
6. Explain Grafana dashboard creation.
7. What are Golden Signals?
8. What is SLI/SLO/SLA?
9. How do you investigate high CPU?
10. How do you investigate memory leak?
11. What is OOMKilled?
12. How do you troubleshoot Node Not Ready?
13. How do you reduce alert noise?
14. What is synthetic monitoring?
15. Describe a production incident you handled.
16. Explain RCA process.
17. How would you monitor Kubernetes?
18. Explain requests and limits.
19. How do exporters work?
20. How do you ensure uptime in production?

If you follow this schedule seriously for 4 days, you'll be prepared for approximately **85-90% of the questions likely to come from this JD**, especially the Linux, Kubernetes, Monitoring, Incident Management, and SRE troubleshooting areas that interviewers usually focus on.
