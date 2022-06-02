---
title: "2. Logging using Elastic Stack"
chapter: true
weight: 11
---

## Logging Using Elastic Stack

"ELK" is the acronym for three open source projects: Elasticsearch, Logstash, and Kibana. Elasticsearch is a search and analytics engine. Logstash is a server‑side data processing pipeline that ingests data from multiple sources simultaneously, transforms it, and then sends it to a "stash" like Elasticsearch. Kibana lets users visualize data with charts and graphs in Elasticsearch.

The Elastic Stack is the next evolution of the ELK Stack.

[ELK Stack Overview](https://www.elastic.co/what-is/elk-stack)

Below are steps to install Elastic Stack in a Kubernetes Cluster

:arrow_right: Create Logging Namespace
```
kubectl create namespace logging
```

:arrow_right: Add Elastic Chart Repository
```
helm repo add elastic https://helm.elastic.co
helm repo update
```

:arrow_right: Install elasticsearch chart
```
helm install elasticsearch elastic/elasticsearch -n logging
```

:arrow_right: Install filebeat chart
```
helm install filebeat elastic/filebeat -n logging
```

:arrow_right: Install logging chart
```
helm install kibana elastic/kibana -n logging
```

:arrow_right: Port-forward to localhost
```
kubectl -n logging port-forward svc/elasticsearch-master 9200:9200
kubectl -n logging port-forward svc/kibana-kibana 5601:5601
```

:arrow_right: GUI to Prometheus and Grafana
```
http://localhost:9200
http://localhost:5601
```
