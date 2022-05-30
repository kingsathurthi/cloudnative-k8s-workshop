---
title: "2. Create Kubernetes Cluster"
chapter: true
weight: 15
---

### Setup your first Kubernetes Cluster using K3D

:arrow_right: 1. Create Kubernetes Cluster

Create a cluster named **devcluster** with just a **single master** node and **3 worker** nodes. We will disable the auto creation of load balancer service and inbuilt traefik ingress controller. A registry node named `devregistry` will also be created as part of the cluster creation. 

Additionally, we will add up a third party Load Balancer(**MetalLB**) and **Nginx Ingress** Controller to the cluster to simulate and access like a realtime kubernetes environment.

```
k3d cluster create devcluster --agents 3 --k3s-arg "--disable=traefik@server:0" --k3s-arg "--disable=servicelb@server:0" --no-lb --wait --registry-create devregistry:30500
```

:arrow_right: 2. Install Kubectl
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" 
sudo mv kubectl /usr/local/bin
```

:arrow_right: 3. Explore Cluster Resources
```
k3d cluster list
k3d kubeconfig get devcluster > ~/.kube/config
export KUBECONFIG=~/.kube/config
kubectl get nodes -o wide

```

:arrow_right: 4. Update /etc/hosts for local registry access
```
echo "127.0.0.1 devregistry" | sudo tee -a /etc/hosts
```

:arrow_right: 5. Install MetalLB
```
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/namespace.yaml
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/metallb.yaml
```

:arrow_right: 5.1 Configure MetalLB
```
sudo apt install jq -y
cidr_block=$(docker network inspect k3d-devcluster | jq '.[0].IPAM.Config[0].Subnet' | tr -d '"')
base_addr=${cidr_block%???}
first_addr=$(echo $base_addr | awk -F'.' '{print $1,$2,$3,240}' OFS='.')
range=$first_addr/29
```

:arrow_right: 5.2 Create MetalLB ConfigMap
```
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: metallb-system
  name: config
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - $range
EOF
```

:arrow_right: 6. Install Nginx Ingress Controller
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.2/deploy/static/provider/cloud/deploy.yaml
```
