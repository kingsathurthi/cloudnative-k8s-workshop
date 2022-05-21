---
title: "1. Create Docker Image"
chapter: true
weight: 11
---

## Create Docker Image

For deployment, we’ll package our application within a container. Kubernetes supports many different container engines, here we’ll use Docker (which is widely used).

The Dockerfile used instructs docker how to build images step by step.

:arrow_right: Fetch application source
```
git clone https://github.com/karthick-kk/netflix-clone
```

:arrow_right: Build Image
```
cd netflix-clone
docker build -t netflix-clone:1.0 .
```

:arrow_right: Push the Image to Docker Registry
```
docker tag netflix-clone:1.0 devregistry:30500/netflix-clone:latest
docker push devregistry:30500/netflix-clone:latest
```
