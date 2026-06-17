# JOBS

Daily portal checking
Daily Naukri applications
Daily LinkedIn searches & applications
Daily Indeed searches
Daily remote job applications

TASKS
Privancia
Wipro 3
One2n - Update
Wipro 2 Update
Tech M Update
MC Update
NTT DATA INC. - Schedule not received.
Deloitte Client (Cirruslabs PayRoll)
Teksystems (Client HSBC)
Metro Global (Take update 11 JUN)
Galaxy Itech (Apple client)
Metro Global (Friday)
MensaBrands (Friday)
BridgeNext (Friday)

Fintech -


Questions -
Interview 1 (WIPRO) :-
AWK, find, locate, top, htop, kill, pkill
How can we check high CPU usage?
What are joins?
What is image versioning in Docker?

Interview 2 (MC):
Explain your CI/CD exposure?
How did you configure alerts in your system using Splunk?
What is Splunk and how do you utilize it?
What is Dynatrace?
What is synthetic monitoring?


Interview 3 (LTI):
Explain your day-to-day activity?
How can you check high CPU % and resolve it?
Explain one case which you resolved in a production environment?
What is the ITSM process you follow in day-to-day activities?
What is ITIL?
Explain the case where you fixed and provided the solution to the product team?


Interview 4 (Deutsche):
What is REST API?
What are different HTTPS methods and codes you know?
What does 5XX error mean?
Explain OpenTelemetry?


Interview 5 (Wipro 2):
Explain Payment Gateway Workflow?
What happens if the connection activity is lost between issuer and bank?
What is Splunk?
What is the difference between Delete & Truncate?
What are the joins in SQL?

Interview 6 (TECH MAHINDRA)
Explain yourself?
Explain CI/CD workflow?
Do you have knowledge about SQL?


What are joins?
What is indexing?
What are the commands to check high CPU %?
What is branching in Git?

Wipro (3rd)
Explain CI/CD pipelines in your daily work?
What is canary deployment?


LTM (DevOps)
Explain your CI/CD pipeline?
Pipeline in Jenkins and AWS?
Write your CI/CD pipeline?
Write down Docker Compose file?
How are logs stored on Prometheus and how did you set it up in Docker Compose?
What is Prometheus & Grafana?
What is node-exporter?
What is OpenTelemetry?
What are Canary, Blue-Green deployment strategies?
How can you replace a name "Shivam" with "Ghodke" using a Linux command? Write a for loop for this as well.
K8S architecture?
What is OOM (Out of Memory)?
What is K8s Version?

Stripe (Payments Analyst)
How can you check duplicates in a table using SQL?
Explain your roles and responsibilities?


BridgeNext

What is Terraform?
Create an EC2 instance with the help of Terraform?
Explain Crashloopbackoff and how you will resolve it?
How can you create an EC2 instance in AWS?
How can you increase the replicas?
How can we set up auto scaling?
Horizontal autoscaling and VPA?
How did you configure parameters and then use queries and configure dashboards in Grafana?
How are you configuring alerts in your current system?
How do you maintain the RCA?
What are metrics, logs, and traces?
What is Elastic IP on EC2?
What is the use of CloudWatch?
How to unconfigure CloudWatch?
How to view the last 10 logs of a file?
I have a process running on port 9090, how can I kill it?


---

# Metro Global - Senior SRE Level Interview Questions & Answers

## 1. How would you create a highly available infrastructure?

**Answer:**
- Use multiple availability zones (AZs) for redundancy
- Implement load balancing (ALB/NLB) across AZs
- Configure auto-scaling groups for dynamic scaling
- Use managed databases with multi-AZ failover
- Implement health checks and automated recovery
- Use Infrastructure as Code (Terraform/CloudFormation) for consistency
- Implement disaster recovery and backup strategies
- Monitor with Prometheus/Grafana for real-time visibility
- Use Kubernetes with multi-node deployment across zones

## 2. Where are you great at monitoring?

**Answer:**
- Infrastructure monitoring: CPU, Memory, Disk, Network
- Application performance monitoring (APM) using Prometheus & Grafana
- Log aggregation and analysis using Graylog
- Distributed tracing with OpenTelemetry
- Custom dashboards in Grafana with relevant metrics
- Alert configuration using Alertmanager
- SLA/SLO tracking and error budget monitoring
- Real user monitoring (RUM) and synthetic monitoring
- Third-party service monitoring and dependency tracking

## 3. You created an infrastructure manually—is that acceptable?

**Answer:**
- No, manual infrastructure is not scalable or reproducible
- Best practice: Use Infrastructure as Code (IaC)
- Benefits of IaC:
  - Version control and audit trail
  - Reproducibility and consistency
  - Faster deployments and disaster recovery
  - Easy scaling and environment parity
- Tools: Terraform, CloudFormation, Ansible, Helm
- Manual changes should be minimal and documented
- Automate everything possible for reliability

## 4. If you see a Pod in Pending state, what troubleshooting will you do?

**Answer:**
**Steps:**
1. Check Pod logs: `kubectl logs <pod-name>`
2. Describe Pod: `kubectl describe pod <pod-name>`
3. Check resource requests vs node capacity: `kubectl top nodes`
4. Verify node availability: `kubectl get nodes`
5. Check for taints/tolerations mismatch
6. Verify PVC availability if storage is needed
7. Check resource quotas and limits
8. Verify image pull policy and image availability

**Common causes:**
- Insufficient CPU/Memory on nodes
- Node selectors/affinity rules not matching
- PVC not bound
- Resource quotas exceeded
- Taints/tolerations mismatch
- Image pull errors

## 5. Production Patterns & Anti-patterns

**Production Patterns (Best Practices):**
- Rolling deployments for zero downtime
- Health checks (readiness & liveness probes)
- Resource requests/limits properly set
- Horizontal Pod Autoscaling (HPA)
- Multi-AZ deployment
- Proper logging and monitoring
- Circuit breakers and retry logic
- API rate limiting
- Caching strategies

**Anti-patterns (Avoid):**
- Running single replica in production
- No resource limits (risk of OOMKill)
- Hardcoded configurations
- Manual deployments
- Ignoring monitoring and alerts
- No disaster recovery plan
- Storing secrets in code
- Tight coupling between services
- No rate limiting on APIs
- Skipping load testing before production

## 6. Monitor user access without existing monitoring—where is the nearest point?

**Answer:**
**Best monitoring point for user requests:**
1. **API Gateway / Ingress Controller** (first touchpoint)
   - Captures all incoming requests
   - Minimal latency
   - Easy to instrument
   - Can track user authentication/authorization

2. **Application Load Balancer (ALB)** 
   - Can log requests
   - Provides metrics on request counts, latency, errors
   - Cost-effective for initial monitoring

3. **Application level**
   - Instrument application code with OpenTelemetry
   - Track request duration, errors, dependencies
   - Log with correlation IDs

4. **Network level**
   - Use VPC Flow Logs
   - Monitor traffic patterns

**Quick setup:**
- Enable ALB/NLB access logs
- Add OpenTelemetry instrumentation
- Set up basic Prometheus scraping
- Create Grafana dashboards for key metrics

## 7. What is Synthetic Monitoring?

**Answer:**
Synthetic monitoring simulates user interactions to verify application availability and performance.

**Key points:**
- Proactive monitoring (before real users are affected)
- Simulate user workflows from multiple locations
- Check endpoint availability, response times, functionality
- Tools: Datadog Synthetic Monitoring, Grafana k6, Postman
- Types:
  - API testing
  - Web transaction monitoring
  - Mobile app simulation
  - DNS monitoring
- Benefits:
  - Early detection of issues
  - Performance baseline establishment
  - Geographic availability verification
  - SLA compliance validation

## 8. What are the Four Golden Signals?

**Answer:**
The Four Golden Signals are key metrics for monitoring system health:

1. **Latency**
   - Time taken for request to be processed
   - Distinguish between successful and failed requests
   - Measure p50, p95, p99 percentiles

2. **Traffic**
   - Volume of requests hitting the system
   - Measured in requests/sec, HTTP methods, bandwidth
   - Helps identify load patterns

3. **Error Rate**
   - Percentage of failed requests
   - Both HTTP errors (5XX, 4XX) and application errors
   - Monitor absolute errors and error rate percentage

4. **Saturation**
   - How "full" your resources are
   - CPU, memory, disk, network utilization
   - Queue lengths, connection pool usage
   - Indicates when to scale

**Implementation:**
- Use Prometheus for collection
- Visualize in Grafana
- Set alerts based on thresholds
- Track SLOs using these metrics

## 9. VPN Service Not Working—How to Troubleshoot?

**Answer:**
**Troubleshooting steps:**

1. **Verify service status:**
   ```bash
   kubectl get pods -n <namespace>
   kubectl describe pod <pod-name>
   kubectl logs <pod-name>
   ```

2. **Check connectivity:**
   ```bash
   ping <service-ip>
   telnet <service-ip>:<port>
   curl http://<service-ip>:<port>/health
   ```

3. **Verify network policies:**
   ```bash
   kubectl get networkpolicies
   kubectl describe networkpolicy <policy-name>
   ```

4. **Check service configuration:**
   ```bash
   kubectl get svc
   kubectl describe svc <service-name>
   ```

5. **Test from inside cluster:**
   ```bash
   kubectl exec -it <pod-name> -- bash
   curl http://<service-name>:<port>
   ```

6. **Check ingress/load balancer:**
   - Verify ingress rules
   - Check ALB/NLB target group health
   - Verify DNS resolution

7. **Check firewall/security groups:**
   - Verify inbound rules on security groups
   - Check VPN gateway settings
   - Verify VPC peering if applicable

**Common issues:**
- Service not ready (pod still starting)
- Wrong port mapping
- Network policy blocking traffic
- DNS resolution failures
- Security group restrictions
- Pod resource exhaustion

## 10. Check Connectivity from Outside VM to Application

**Answer:**
**Commands to verify external connectivity:**

```bash
# 1. Test DNS resolution
nslookup <application-domain>
dig <application-domain>

# 2. Test connectivity to VM
ping <vm-public-ip>
traceroute <vm-public-ip>

# 3. Test application port
telnet <vm-public-ip> <port>
nc -zv <vm-public-ip> <port>

# 4. Test HTTP/HTTPS
curl -v http://<vm-public-ip>:<port>
curl -I http://<application-domain>

# 5. Check route to VM
traceroute <vm-public-ip>
mtr <vm-public-ip>

# 6. Test with specific protocol
curl -k https://<vm-public-ip>:443
wget http://<vm-public-ip>:<port>/health

# 7. Check response headers
curl -v -H "Host: <domain>" http://<vm-public-ip>:<port>
```

**Verification checklist:**
- [ ] DNS resolves correctly
- [ ] VM is reachable (ping successful)
- [ ] Port is listening (`telnet` successful)
- [ ] Application responds (HTTP 200/3xx, not 5xx)
- [ ] Security group allows inbound traffic
- [ ] Network ACLs allow traffic
- [ ] Firewall on VM allows port
- [ ] Application is running and healthy
- [ ] Load balancer health checks passing
- [ ] No rate limiting blocking requests

---

# 1. Linux Administration

### Basic Commands

1. How do you view the last 10 lines of a log file?
2. Difference between `cat`, `less`, `more`, `tail`, and `head`?
3. How do you continuously monitor a log file?
4. How do you search for a string in a large log file?
5. How do you count occurrences of a string in a file?
6. How do you find large files consuming disk space?
7. How do you check disk utilization?
8. How do you check memory utilization?
9. How do you check CPU utilization?
10. How do you identify the top resource-consuming processes?

### Process Management

11. How do you find a process running on port 9090?
12. How do you kill a process?
13. Difference between SIGTERM and SIGKILL?
14. What is a zombie process?
15. What is an orphan process?
16. How do you check running services?

### Networking

17. How do you verify connectivity to a server?
18. Difference between ping and traceroute?
19. How do you check listening ports?
20. How do you troubleshoot network latency?

---

# 2. Kubernetes

### Fundamentals

21. What is Kubernetes?
22. What is a Pod?
23. Where does a Pod actually run?
24. Difference between Container, Pod, Node, and Cluster?
25. What is a Namespace?
26. What is a ReplicaSet?
27. What is a Deployment?
28. What is a Service?
29. Types of Kubernetes Services?
30. What is an Ingress?

### Scheduling

31. How does Kubernetes schedule Pods?
32. What are Taints and Tolerations?
33. What are Node Selectors?
34. What is Pod Affinity and Anti-Affinity?
35. Can multiple Pods run on the same node?

### Troubleshooting

36. Pod stuck in Pending state?
37. Pod in CrashLoopBackOff?
38. ImagePullBackOff?
39. OOMKilled?
40. Node Not Ready?
41. How do you debug Kubernetes issues?

### Health Checks

42. What is a Readiness Probe?
43. What is a Liveness Probe?
44. Difference between Readiness and Liveness?

### Scaling

45. What is HPA?
46. What is Cluster Autoscaler?
47. How does Kubernetes scale applications?

---

# 3. AWS & EKS

### AWS Basics

48. What is EC2?
49. What is VPC?
50. What is Security Group?
51. What is an Internet Gateway?
52. What is a NAT Gateway?
53. What is Route Table?

### EKS

54. What is EKS?
55. Components of EKS?
56. Difference between EKS and self-managed Kubernetes?
57. How do worker nodes join a cluster?
58. What is a Node Group?
59. How do you upgrade EKS?

### Cost Optimization

60. How do you reduce AWS costs?
61. Why would extra EC2 instances appear in EKS?
62. How do you identify infrastructure cost spikes?

---

# 4. Docker

63. What is Docker?
64. Difference between VM and Container?
65. What is a Docker Image?
66. What is a Docker Container?
67. What is Dockerfile?
68. Difference between CMD and ENTRYPOINT?
69. How do you build a Docker image?
70. How do you view container logs?

---

# 5. CI/CD

71. What is CI/CD?
72. Explain your deployment pipeline.
73. What is Jenkins?
74. What is GitLab CI/CD?
75. What is GitHub Actions?
76. What is a rollback?
77. How do you automate deployments?

---

# 6. Deployment Strategies

78. What is Rolling Deployment?
79. What is Blue-Green Deployment?
80. What is Canary Deployment?
81. Difference between Rolling and Blue-Green?
82. How do you ensure zero downtime deployments?
83. How do you perform rollback?

---

# 7. Monitoring & Observability

### Golden Signals

84. What are the Four Golden Signals?
85. What is Latency?
86. What is Traffic?
87. What is Error Rate?
88. What is Saturation?

### Monitoring Tools

89. What is Prometheus?
90. What is Grafana?
91. What is Graylog?
92. Difference between Monitoring and Logging?
93. What metrics do you monitor?

### Synthetic Monitoring

94. What is Synthetic Monitoring?
95. Why use Synthetic Monitoring?
96. How do you verify application availability from a user's perspective?

---

# 8. Grafana

97. What is Grafana?
98. How do you create a dashboard?
99. What data sources have you used?
100. How do you create alerts?
101. How do you troubleshoot Grafana issues?

---

# 9. Graylog

102. What is Graylog?
103. How is Graylog implemented in your organization?
104. What are Streams?
105. What are Extractors?
106. How do you search logs?
107. How do you create alerts?
108. How do you create dashboards?
109. How do you troubleshoot missing logs?

---

# 10. Incident Management

110. Describe a Sev-1 incident you handled.
111. How do you perform RCA?
112. How do you manage incident bridges?
113. How do you communicate during outages?
114. What is SLA?
115. What is SLO?
116. What is SLA breach prevention?

---

# 11. Application Troubleshooting

117. Application is down. What is your approach?
118. API returning 500 errors. What will you do?
119. High response time issue?
120. Memory leak issue?
121. Database connectivity issue?
122. Third-party API authentication failure?

---

# 12. Databases

123. Have you worked with databases?
124. Difference between SQL and NoSQL?
125. How do you troubleshoot database connectivity?
126. What is Indexing?
127. What is a Primary Key?
128. What is a Foreign Key?

---

# 13. SQL

129. Difference between INNER JOIN and LEFT JOIN?
130. Explain all SQL Joins.
131. What is a Subquery?
132. What is a CTE?
133. Difference between DELETE, DROP, and TRUNCATE?
134. Write a query to find duplicates.
135. Write a query to get the second highest salary.

---

# 14. Java Basics

136. What is JVM?
137. What is JDK?
138. What is JRE?
139. What is Exception Handling?
140. Checked vs Unchecked Exceptions?
141. What is Multithreading?
142. What is OOP?

---

# 15. Networking

143. What happens when you open a website?
144. Explain DNS resolution.
145. What is TCP?
146. What is UDP?
147. TCP Three-Way Handshake?
148. What is Load Balancer?
149. What is Reverse Proxy?

---

# 16. Security

150. What is IAM?
151. What is RBAC in Kubernetes?
152. What are Secrets in Kubernetes?
153. How do you manage API keys?
154. How do you secure applications?

---

# 17. SRE Concepts

155. What is SRE?
156. Difference between DevOps and SRE?
157. What is Error Budget?
158. What is Toil?
159. What is Reliability Engineering?
160. What is Capacity Planning?

---

# 18. Real-Time Scenario Questions

161. Pod suddenly enters CrashLoopBackOff.
162. Node becomes NotReady.
163. Application latency increases.
164. AWS bill suddenly increases.
165. Production traffic drops.
166. Third-party payment gateway is down.
167. Database connections exhausted.
168. Kubernetes deployment failed.
169. Memory utilization reaches 95%.
170. Load balancer health checks fail.

---

# 19. Behavioral Questions

171. Tell me about yourself.
172. Why are you changing jobs?
173. Why do you want to join our company?
174. Describe a challenging incident.
175. Describe a conflict with a team member.
176. Describe a successful project.
177. How do you handle pressure?
178. Why should we hire you?

---

# 20. Metro Global / Senior SRE Level Questions

179. How do you maintain zero downtime?
180. How do you size Kubernetes resources?
181. How do you choose EC2 instance types?
182. How do you optimize infrastructure costs?
183. How do you troubleshoot production incidents?
184. How do you design highly available systems?
185. How do you handle dependency failures?
186. How do you monitor distributed systems?
187. How do you troubleshoot Kubernetes scheduling issues?
188. How do you scale applications efficiently?
189. How do you balance reliability and cost optimization?

These 189 questions cover approximately 90–95% of the technical topics discussed across all interview preparation conversations and serve as a comprehensive master checklist for SRE/DevOps/NOC/Platform Engineer roles.
