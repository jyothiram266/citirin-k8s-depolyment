## Kubernetes Deployment Guide

This guide provides steps to deploy and manage Kubernetes resources using Helm and Kubernetes manifests.

Clone the Repo
```
git clone https://github.com/jyothiram266/citirin-k8s-depolyment.git
```

### Prerequisites

- Kubernetes cluster (EKS, Minikube, or any K8s setup)
- kubectl installed and configured
- Helm installed 
- Access to the necessary container images and repositories

## 🚀 Deployment Steps

#### 1️⃣ Apply Kubernetes Manifests (Mandatory)

apply the required Kubernetes configurations from the k8s/ directory

``` 
kubectl apply -f k8s/ 
```

Verify that the resources are created:

```
kubectl get all -n citrin-os
```

check the following services are running

#### 2️⃣ Apply the Helm Chart

Once the necessary resources are created, install the Helm chart (citrin-os):

```
helm install citrin-os ./citrin-os
```

Confirm that the deployment is running successfully:

```
helm list
kubectl get pods -n citrin-os
```

## 5️⃣ Cleanup the Deployment
#### To remove the Helm release:

```
helm uninstall citrin-os
```
To remove the additional Kubernetes resources:

```
kubectl delete -f k8s/
```