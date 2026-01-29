# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Repository Purpose

This is a learning repository for Kubernetes fundamentals. It contains course materials, practical examples, and exercises for understanding Kubernetes architecture, API, and deployment patterns.

## Working with Kubernetes in this Repository

### Prerequisites
- Ensure `kubectl` is installed and configured
- For local development, use Minikube, kind, or Docker Desktop with Kubernetes enabled
- Verify cluster access with: `kubectl cluster-info`

### Common Commands

**Cluster Operations:**
```powershell
# Check cluster status
kubectl cluster-info

# View cluster nodes
kubectl get nodes

# Check available contexts
kubectl config get-contexts

# Switch context
kubectl config use-context <context-name>
```

**Working with Manifests:**
```powershell
# Apply Kubernetes configurations
kubectl apply -f <file.yaml>
kubectl apply -f <directory>/

# Validate YAML without applying
kubectl apply -f <file.yaml> --dry-run=client

# Delete resources
kubectl delete -f <file.yaml>
```

**Inspecting Resources:**
```powershell
# Get resources
kubectl get pods
kubectl get deployments
kubectl get services
kubectl get all -A  # All resources in all namespaces

# Detailed resource information
kubectl describe <resource-type> <resource-name>

# View logs
kubectl logs <pod-name>
kubectl logs <pod-name> -f  # Follow logs
```

**Debugging:**
```powershell
# Execute commands in a pod
kubectl exec -it <pod-name> -- /bin/sh

# Port forwarding for local testing
kubectl port-forward <pod-name> <local-port>:<pod-port>

# Check events
kubectl get events --sort-by=.metadata.creationTimestamp
```

## Repository Organization

When adding Kubernetes examples and exercises:

- Organize by topic/chapter (e.g., `01-pods/`, `02-deployments/`, `03-services/`)
- Use descriptive names for YAML files (e.g., `nginx-deployment.yaml`, `frontend-service.yaml`)
- Include comments in YAML files explaining key configuration choices
- Keep examples simple and focused on demonstrating specific concepts

## YAML Formatting Standards

- Use 2 spaces for indentation (Kubernetes convention)
- Include `apiVersion`, `kind`, and `metadata` fields for all resources
- Add descriptive labels for resource organization
- Use `---` to separate multiple resources in a single file

## Development Environment

This repository uses:
- Windows with PowerShell
- Java 7 at H:\\jdk-7u80 for legacy development (if Java-based examples are added)
- Git for version control

When creating examples that require compilation, ensure compatibility with the available Java version if applicable.
