# Kubernetes Persistent Storage Practical

A comprehensive hands-on practical guide for managing persistent storage in Kubernetes. This practical covers PersistentVolumes (PV), PersistentVolumeClaims (PVC), and data persistence across container lifecycles.

## 📋 Objectives
By completing this practical, you will be able to:

- Understand the difference between Volumes, PersistentVolumes (PV), and PersistentVolumeClaims (PVC)
- Create and configure PersistentVolumes with different storage classes
- Create PersistentVolumeClaims to request storage resources
- Deploy applications that utilize persistent storage
- Verify data persistence across pod restarts and deletions
- Troubleshoot common storage-related issues in Kubernetes
- Implement best practices for managing persistent data in containerized applications

## 🚀 Quick Start

### Prerequisites
- Basic understanding of Kubernetes concepts (Pods, Deployments, Services)
- Familiarity with YAML syntax and Kubernetes manifest files
- Basic Linux command-line knowledge
- Understanding of file systems and storage concepts
- Kubernetes cluster (minikube, kind, or cloud Kubernetes service)

### Setup Instructions

1. Clone the repository:
git clone https://github.com/saadcnx/kubernetes-persistent-storage-practical.git
cd kubernetes-persistent-storage-practical

2. Create namespace:
kubectl create namespace storage-practical
kubectl config set-context --current --namespace=storage-practical

3. Deploy basic storage setup:
kubectl apply -f manifests/persistent-volume.yaml
kubectl apply -f manifests/persistent-volume-claim.yaml
kubectl apply -f manifests/storage-app-deployment.yaml

📁 Project Structure
.
├── manifests/           # Kubernetes YAML manifests
├── scripts/            # Utility and monitoring scripts

🔧 Practical Tasks

Task 1: Environment Setup

Verify Kubernetes cluster status
Create dedicated namespace
Check available storage classes

Task 2: Persistent Storage Creation

Create PersistentVolume with hostPath storage
Create PersistentVolumeClaim to request storage
Bind PVC to available PV

Task 3: Application Deployment

Deploy application that writes to persistent storage
Create service for application access
Monitor data writing in real-time

Task 4: Data Persistence Verification

Test data persistence across pod restarts
Delete and recreate pods while preserving data
Scale applications with persistent storage

Task 5: Advanced Scenarios

Multiple volume mounting
Storage monitoring and management
Troubleshooting common issues

📊 Monitoring and Management

Included Scripts:
monitor-storage.sh - Monitor PV/PVC status and usage
cleanup-storage.sh - Clean up all resources safely
final-verification.sh - Comprehensive verification script

Best Practices:
Storage class selection strategies

Resource management and quotas
Data persistence strategies
Security considerations
Monitoring and alerting setup

🐛 Troubleshooting

Common Issues:
1. PVC Stuck in Pending State
Check available PV capacity
Verify storage class compatibility
Review access mode requirements
2. Pod Cannot Mount Volume
Verify PVC binding status
Check volume mount paths
Review RBAC permissions
3. Data Not Persisting
Confirm PV reclaim policy
Verify volume mounts
Check storage class configuration

- Detailed troubleshooting guide available in documentation/troubleshooting.md.

🧪 Testing
Run the comprehensive verification:

chmod +x scripts/final-verification.sh
./scripts/final-verification.sh

🧹 Cleanup
Remove all resources:
chmod +x scripts/cleanup-storage.sh
./scripts/cleanup-storage.sh

📚 Learning Outcomes
After completing this practical, you will understand:
How Kubernetes manages persistent storage
The relationship between PVs, PVCs, and StorageClasses
Data persistence strategies for stateful applications
Best practices for storage management in production
Troubleshooting techniques for storage issues

🎓 Real-World Applications
Database deployments (PostgreSQL, MySQL, MongoDB)
Content management systems
File sharing applications
Data analytics pipelines
Backup and recovery systems

🤝 Contributing
Fork the repository
Create a feature branch
Commit your changes
Push to the branch
Open a Pull Request

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
Kubernetes Documentation
Cloud Native Computing Foundation
This practical was completed as part of the cloud computing curriculum at Al Nafi International College.
