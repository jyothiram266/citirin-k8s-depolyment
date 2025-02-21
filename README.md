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

to apply the required Kubernetes configurations from the k8s/ directory

``` 
kubectl apply -f k8s/ 
```
This command depoly Rabbitmq and Database

Verify that the resources are created:

```
kubectl get all -n citrin-os
```

check the following services are running
Wait Untill database up and running

#### 2️⃣ Apply the Helm Chart

Once the necessary resources are created, install the Helm chart (citrin-os):

for Dev
```
helm install dev-citrinos ./citrin-os --values ./citrin-os/values-dev.yaml
```

for Prod

```
helm install prod-citrinos ./citrin-os --values ./citrin-os/values-prod.yaml
```
Confirm that the deployment is running successfully:

```
helm list
kubectl get pods -n citrin-os
```

you can upgrade the values and to reflect the changes run the following command accordingly

```
helm upgrade <HELM_NAME> ./citrin-os --values ./citrin-os/values-<dev-prod>.yaml 
```

#### 4️⃣ Updating the Deployment
If any changes are made to the Kubernetes manifests, reapply them:

```
kubectl apply -f k8s/
```

To upgrade the Helm release with new configurations:

```
helm upgrade citrin-os ./citrin-os
```

## 5️⃣ Cleanup the Deployment
#### To remove the Helm release:

```
helm uninstall <HELM-CHART-NAME>
```
To remove the additional Kubernetes resources:

```
kubectl delete -f k8s/
```

# 📌 Notes
- Apply k8s/ manifests first to create necessary resources (namespace, DB, RabbitMQ).
- Deploy the Helm chart (citrin-os/) afterward to ensure dependent services are available.