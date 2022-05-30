---
title: "1. Monitoring using Prometheus Stack"
chapter: true
weight: 11
---

## Monitoring Using Prometheus Stack

Prometheus collects and stores its metrics as time series data, i.e. metrics information is stored with the timestamp at which it was recorded, alongside optional key-value pairs called labels.

Prometheus scrapes metrics from instrumented jobs, either directly or via an intermediary push gateway for short-lived jobs. It stores all scraped samples locally and runs rules over this data to either aggregate and record new time series from existing data or generate alerts. Grafana or other API consumers can be used to visualize the collected data.

Below are steps to install Prometheus Stack in a Kubernetes Cluster

:arrow_right: Create Monitoring Namespace
```
kubectl create namespace monitoring
```

:arrow_right: Add Prometheus Stack Chart Repository
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

:arrow_right: Helm Install Prometheus Stack
```
helm install prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring
```

:arrow_right: Prometheus Stack Pod Status
```
kubectl -n monitoring get nodes -o wide
```

:arrow_right: Port-forward to localhost
```
kubectl -n monitoring port-forward service/prometheus-stack-kube-prom-prometheus 9090
kubectl -n monitoring port-forward service/prometheus-stack-grafana 9091:80
```

:arrow_right: GUI to Prometheus and Grafana
```
http://localhost:9090
http://localhost:9091
```