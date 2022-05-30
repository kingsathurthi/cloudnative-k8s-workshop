---
title: "3. Basic Kubectl Commands"
chapter: true
weight: 4
---

# Kubectl - Command Line Tool

Kubernetes provides a command line tool for communicating with a Kubernetes cluster's control plane, using the Kubernetes API.This tool is named kubectl. We can use kubectl to deploy applications, inspect and manage cluster resources, and view logs.

kubectl is installable on a variety of Linux platforms, macOS and Windows. Refer the below link to install kubectl, 

[Install Kubectl](https://kubernetes.io/docs/tasks/tools/)

:arrow_right: Client and Server version information
```
kubectl version
```

:arrow_right: Cluster Information
```
kubectl cluster-info
```
:arrow_right: Supported API versions on the server
```
kubectl api-versions
```

:arrow_right: List Resources
```
kubectl get nodes
kubectl get nodes
```

:arrow_right: Details of a specific resource
```
kubectl describe node <nodename>
kubectl describe pod <podname>
```

:arrow_right: Create resource
```
kubectl create -f <filename>
```
