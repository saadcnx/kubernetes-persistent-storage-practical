# Prerequisites

## Required Knowledge
Before starting this practical, ensure you have:

### Kubernetes Fundamentals
- Basic understanding of Kubernetes architecture
- Familiarity with Pods, Deployments, and Services
- Experience with `kubectl` command-line tool
- Knowledge of YAML syntax for Kubernetes manifests

### Technical Skills
- Basic Linux command-line proficiency
- Understanding of file systems and storage concepts
- Experience with container concepts (Docker/Podman)
- Ability to edit files using CLI editors (vim/nano)

### Previous Experience
- Completion of basic Kubernetes labs
- Experience creating and managing pods
- Understanding of Kubernetes namespaces
- Basic troubleshooting skills

## System Requirements

### Local Development Environment
**Option 1: Local Kubernetes Cluster**
- Minikube v1.25.0+ or Kind v0.14.0+
- Docker Desktop 4.10+ or equivalent
- 4GB RAM minimum, 8GB recommended
- 20GB free disk space

**Option 2: Cloud Kubernetes Service**
- Access to EKS, AKS, GKE, or equivalent
- `kubectl` configured with cluster access
- Sufficient permissions to create PV/PVC objects

### Software Requirements
- kubectl v1.24+
- Git for version control
- Terminal/CLI access
- Text editor (VS Code, vim, nano)

### Network Requirements
- Internet access for pulling container images
- Ability to access Kubernetes API server
- No restrictive firewall blocking port 6443

## Pre-Lab Setup Checklist

### Verify Your Environment
```bash
# Check kubectl version
kubectl version --client

# Verify cluster connectivity
kubectl cluster-info

# Check available nodes
kubectl get nodes

# Verify storage classes
kubectl get storageclass
