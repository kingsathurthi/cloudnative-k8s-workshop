---
title: "1. Install K3D"
chapter: true
weight: 10
---

## Install K3D

k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker.

k3d makes it very easy to create single- and multi-node k3s clusters in docker, e.g. for local development on Kubernetes.

![K3D Project](../images/k3d.jpg "K3D")

:arrow_right: Install K3D
```
wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

:arrow_right: Validate K3D Installation
```
k3d version
```

Let's move to the next section
