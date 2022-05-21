---
title: "2. Create Deployment"
chapter: true
weight: 14
---

## Create a Kubernetes Deployment

{{% notice tip %}}
We create a **deployment** due to the application being stateless. For applications that persists data, a **statefulset** is preferred to store the data across all the nodes.
{{% /notice %}}

:arrow_right: Create a Kubernetes Deployment from manifests
```
kubectl apply -f manifests
```

:arrow_right: Verify the deployment and service
```
kubectl get deployment netflix-clone
kubectl get service netflix-clone-service
```