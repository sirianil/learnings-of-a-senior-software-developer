# Chapter 1: Infrastructure & Kubernetes

## 1.1 Overview

Modern applications are typically deployed in **Kubernetes (K8s)**, where workloads are packaged into containers and run as **pods**. Kubernetes allows teams to scale pods up or down dynamically based on traffic load, ensuring resilience and efficiency.

## 1.2 Key Concepts

- **Pod**: The smallest deployable unit in Kubernetes, containing one or more containers.
- **Deployment**: Declares the desired state (e.g., number of replicas) for a set of pods.
- **Namespace**: Used to isolate resources by environment (e.g., `dev`, `staging`, `sandbox`, `production`).
- **Service**: Exposes pods as a stable network endpoint.
- **Ingress**: Manages external HTTP/HTTPS access to services.

## 1.3 Common Kubectl Commands

```bash
# View pods in a namespace
kubectl get pods -n <namespace>

# Describe a pod for detailed status and events
kubectl describe pod <pod-name> -n <namespace>

# Stream logs from a pod
kubectl logs -f <pod-name> -n <namespace>

# Execute a command inside a running pod (log in)
kubectl exec -it <pod-name> -n <namespace> -- /bin/bash

# Scale a deployment
kubectl scale deployment <deployment-name> --replicas=<n> -n <namespace>

# View recent events in a namespace
kubectl get events -n <namespace> --sort-by='.lastTimestamp'
```

## 1.4 Pod Health & Resource Monitoring

Keep an eye on the following pod-level metrics:

- **CPU utilization (%)**: High sustained CPU can indicate a runaway process or need to scale out.
- **Memory usage (bytes)**: Watch for memory leaks; pods approaching their memory limit will be OOMKilled.
- **Restart count**: Frequent restarts indicate crashes — check logs for root cause.
- **Readiness / Liveness probes**: Ensure probes are configured correctly so Kubernetes can self-heal unresponsive pods.

## 1.5 Environments

Maintain isolated environments to protect production stability:

| Environment | Purpose |
|---|---|
| **Development** | Local or shared sandbox for active feature work |
| **Sandbox** | Freeform testing area; fewer guardrails |
| **Staging** | Production mirror; used for final validation before release |
| **Production** | Live system serving real users |

## 1.6 Multi-Region Hosting

Deploy to multiple geographic regions to:
- Reduce latency for users in different locations.
- Provide redundancy in case of regional outages.
- Meet data residency requirements.

Use latency-based or geolocation-based routing (e.g., via AWS Route 53 or GCP Traffic Director) to direct users to the nearest healthy region.
