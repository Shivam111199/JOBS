# Interview Questions & Answers

## Q.1) How would you create a highly available infrastructure?

To create a highly available infrastructure, I would eliminate single points of failure at every layer. I would deploy multiple application instances behind a load balancer, distribute them across multiple availability zones or data centers, use database replication with automatic failover, implement health checks and monitoring using Prometheus and Grafana, and ensure backups and disaster recovery procedures are in place. This way, if one server, application instance, or even an entire zone fails, the service remains available to users.

---

## Detailed Layer-wise Answer

### 1. Load Balancer

- Deploy multiple application servers.
- Place them behind a Load Balancer (NGINX, HAProxy, AWS ALB).
- Configure health checks.
- Traffic automatically shifts if one server fails.

#### 1.a Synthetic Monitoring

- **Proactive health checks** through synthetic transactions that simulate real user behavior.
- Use tools like **Pingdom, UptimeRobot, or Datadog Synthetics** to periodically test critical user journeys.
- Monitor API endpoints, login flows, payment transactions, and critical workflows.
- Set up alerts if synthetic tests fail, indicating potential issues before real users are affected.
- Record metrics like response time, SSL certificate validity, and DNS resolution.
- Helps identify performance degradation and availability issues across different geographic regions.

### 2. Application Layer

- Run multiple application instances.
- Use Kubernetes Deployments with multiple replicas.
- Enable auto-healing and auto-scaling.

### 3. Database Layer

- Primary-Replica setup.
- Automatic failover.
- Regular backups and point-in-time recovery.

### 4. Infrastructure Layer

- Deploy servers across multiple Availability Zones/Data Centers.
- Avoid single points of failure.

### 5. Monitoring & Alerting

- **Prometheus** for metrics collection.
- **Grafana** dashboards for visualization.
- **Alertmanager** for notifications.
- Monitor CPU, memory, disk, latency, and errors.

### 6. Disaster Recovery

- Regular backups.
- Infrastructure as Code (Terraform).
- Recovery procedures tested periodically.

---

## Kubernetes-Specific Answer

In Kubernetes, I would:
- Deploy multiple pod replicas using Deployments.
- Expose them through a Service and Load Balancer.
- Distribute workloads across worker nodes using anti-affinity rules.
- Use readiness and liveness probes for automatic pod restart and traffic routing.
- Implement PodDisruptionBudgets to maintain availability during node maintenance.
- Use StatefulSets for stateful applications with persistent storage.

---

## Q: What is a Single Point of Failure (SPOF)?

A **Single Point of Failure** is a component whose failure can bring down the entire system. For example:
- Having only one application server
- A single database server
- One load balancer
- A single internet connection
- One data center

**High availability** aims to eliminate SPOFs by introducing redundancy and failover mechanisms at every critical layer.

---

## Q.2) Where are you good in monitoring?

I am strong in infrastructure and application monitoring using:

- **Prometheus** - Time-series metrics collection and storage
- **Grafana** - Dashboard creation and visualization
- **Graylog** - Log aggregation and analysis
- **Datadog/New Relic** - APM and comprehensive monitoring

**Experience includes:**
- Creating custom dashboards for application and infrastructure metrics
- Configuring alert rules and notification channels
- Monitoring Linux servers, Kubernetes clusters, and containerized applications
- Setting up log aggregation and distributed tracing
- Performance optimization based on monitoring insights
- Synthetic monitoring and uptime checks
