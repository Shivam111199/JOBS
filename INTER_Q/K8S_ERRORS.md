 KUBERNETES POSSIBLE ERRORS 

   1. Pod is in Pending state
       What it means: Pod is accepted by the scheduler but cannot run because no suitable node is found.

            Common causes:
             - Insufficient CPU/memory on any node (resource requests > available)
             - Node selector / affinity rules not matching any node
             - PersistentVolumeClaim not bound
             - Taints/tolerations mismatch

            Resolution:
              kubectl describe pod <pod-name>   # Check Events for scheduling failure
             # Add more nodes, reduce resource requests, fix PVC binding, or add tolerations

---

  2. ImagePullBackOff / ErrImagePull
       What it means: Kubernetes cannot pull the container image from the registry.

          Common causes:
           - Wrong image name or tag (typo, missing tag)
           - Image doesn't exist in the registry
           - Private registry without imagePullSecrets
           - Network issues (no access to registry)
           - Registry rate limits or downtime

          Resolution:
            # kubectl describe pod <pod-name> | grep -A5 Events
            # Fix image name, add imagePullSecrets, check network, or use a public accessible image

---

  3. CrashLoopBackOff
        What it means: Container starts, then crashes (exits with non‑zero code), and Kubernetes keeps restarting it.

          Common causes:
           - Application error (bug, config mistake, missing dependencies)
           - Readiness/Liveness probe failing (e.g., endpoint not responding fast enough)
           - Exceeding memory limit (OOMKilled – see below)
           - Misconfigured command/args
           - Missing environment variables or secrets

          Resolution:
            # kubectl logs <pod-name> --previous   # See why it crashed
            # kubectl describe pod <pod-name>      # Check events, restart policy, probe config
            # Fix application config, add missing secrets, increase probes delay, fix args
---

  4. OOMKilled
        What it means: Container exceeded its memory limit and was killed by Linux OOM killer.

          Common causes:
            - Memory leak in application
            - Memory limit set too low (below real usage)
            - Traffic surge causing high memory consumption

          Resolution:
           # kubectl describe pod <pod-name> | grep -i oom
           # kubectl top pod <pod-name>   # check current usage
           # Increase memory limit, fix memory leak, add HPA based on memory


---

 5. Evicted
      What it means: Pod is removed from a node because the node is under pressure (disk, memory, PID).

        Common causes:
        - Node disk space full (image GC, log files)
        - Node memory pressure (node’s memory < eviction threshold)
        - Node having too many terminated pods

       Resolution: 
        # kubectl describe pod <pod-name> | grep -i evicted
        # Check node conditions: kubectl describe node <node-name>
        # Free disk on node (docker system prune, clean logs), increase node resources
---

6. Completed
      What it means: Container exited with 0 exit code and is not expected to restart (e.g., Job, init container, or one‑time task). For a long‑running service, this is an error.

        Common causes (for long‑running pod):
         - Main process exited by itself (e.g., application ended)
         - Command/args set to run a script that exits

       Resolution:

         # kubectl logs <pod-name>   # Check if application intentionally exited
         # If it's a service, ensure the main process runs continuously (e.g., CMD ["node","server.js"], not a script that exits)


---

7. ContainerCreating (stuck)
     What it means: Pod is scheduled but container isn't starting – usually waiting for something.

        Common causes:
         - PVC not bound (still in pending)
         - Missing ConfigMap/Secret referenced by volume mount or env
         - Storage driver issues (network storage not accessible)
         - CNI misconfiguration (network not ready)

        Resolution:
         # kubectl describe pod <pod-name> | tail -20
         # Check PVC status, ensure ConfigMap/Secret exist, verify CNI pods running (kube-system)


---

 8. CreateContainerConfigError
       What it means: There is a problem with the configuration of the container (often environment variables or volume mounts).

    Common causes:
    
        - Referenced ConfigMap or Secret does not exist in that namespace
        - Volume mount path invalid or permission issue
        - valueFrom field has wrong key name

    Resolution:
    
        - kubectl describe pod <pod-name> | grep -A10 Events
        - Check ConfigMap/Secret: kubectl get configmap,secret -n <ns>
        - Fix missing resources or correct key names.


---

 9. RunContainerError
      What it means: Generic error when container cannot start (often before entrypoint).

        Common causes:
         - Binary inside container not executable (permissions)
         - Wrong user (securityContext) cannot access volume
         - Invalid command or args format

       Resolution:
          # kubectl describe pod <pod-name>
          # Check events for specific error. Fix command syntax, permissions, or user.

---

 10. Terminating (stuck)
       What it means: Pod is stuck while being deleted.

          Common causes:
           - Pod has finalizers that are not removed (e.g., from some controllers)
           - gracePeriodSeconds is large and container doesn't handle SIGTERM
           - Bug in kubelet or container runtime

           Resolution:
            # kubectl delete pod <pod-name> --force --grace-period=0   # force delete (last resort)
            # For finalizers: kubectl patch pod <pod-name> -p '{"metadata":{"finalizers":[]}}' --type=merge


---

📋 Interview Cheat Sheet

| Status | Quick check command | Most likely fix |
|--------|---------------------|------------------|
| Pending          | kubectl describe pod      | Resources, PVC binding, taints |
| ImagePullBackOff | kubectl describe pod      | Image name, secrets, registry |
| CrashLoopBackOff | kubectl logs --previous   | App error, probes, limits |
| OOMKilled        | kubectl describe pod      | Increase memory limit, fix leak |
| Evicted          | kubectl describe node     | Free node disk/memory |
| CreateContainerConfigError | kubectl describe pod | Missing ConfigMap/Secret |
| ContainerCreating (stuck) | kubectl describe pod | PVC, CNI, storage |
