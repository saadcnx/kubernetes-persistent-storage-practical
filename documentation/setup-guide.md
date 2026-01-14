# Setup Guide

## Environment Configuration
Local Setup with Minikube

#### Step 1: Install Minikube

# For Linux
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# For macOS
brew install minikube

# For Windows
choco install minikube

### Step 2: Start Minikube Cluster

# Start minikube with adequate resources
minikube start --memory=4096 --cpus=2 --disk-size=20g

# Enable storage addons
minikube addons enable storage-provisioner
minikube addons enable default-storageclass

# Verify cluster status
minikube status

### Step 3: Install kubectl

# Download kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

# Make executable and move to PATH
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# Verify installation
kubectl version --client

### Option 3: Using Kind (Kubernetes in Docker)

# Step 1: Install Kind

# Download kind binary
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Step 2: Create Cluster

# Create cluster configuration
cat > kind-config.yaml <<EOF
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  extraMounts:
  - hostPath: /tmp/kind-data
    containerPath: /data
EOF

# Create cluster
kind create cluster --config kind-config.yaml
Practical Setup Steps

# Step 1: Clone Repository
bash
git clone https://github.com/saadcnx/kubernetes-persistent-storage-practical.git
cd kubernetes-persistent-storage-practical

# Step 2: Create Namespace

# Create dedicated namespace
kubectl create namespace storage-practical

# Set as default context
kubectl config set-context --current --namespace=storage-practical

# Verify namespace creation
kubectl get namespaces | grep storage-practical

# Step 3: Verify Storage Classes

# Check available storage classes
kubectl get storageclass

# Expected output for minikube:
# NAME                 PROVISIONER                AGE
# standard (default)   k8s.io/minikube-hostpath   5m

# Step 4: Prepare Host Paths (Local Clusters)

# Create directories for hostPath volumes
sudo mkdir -p /tmp/practical-data
sudo mkdir -p /tmp/practical-data-2
sudo chmod 777 /tmp/practical-data /tmp/practical-data-2

# For minikube specifically
minikube ssh "sudo mkdir -p /tmp/practical-data && sudo chmod 777 /tmp/practical-data"
minikube ssh "sudo mkdir -p /tmp/practical-data-2 && sudo chmod 777 /tmp/practical-data-2"

# Quick Verification Script
Create a setup verification script:


cat > verify-setup.sh << 'EOF'
#!/bin/bash

echo "=== Setup Verification ==="
echo "Date: $(date)"
echo

echo "1. Checking kubectl..."
kubectl version --client --short || echo "✗ kubectl not found"

echo
echo "2. Checking cluster status..."
kubectl cluster-info && echo "✓ Cluster accessible" || echo "✗ Cannot access cluster"

echo
echo "3. Checking nodes..."
kubectl get nodes

echo
echo "4. Checking storage classes..."
kubectl get storageclass

echo
echo "5. Checking namespace..."
kubectl get namespace storage-practical && echo "✓ Namespace exists" || echo "✗ Namespace not found"

echo
echo "=== Setup Complete ==="
EOF

chmod +x verify-setup.sh
./verify-setup.sh
