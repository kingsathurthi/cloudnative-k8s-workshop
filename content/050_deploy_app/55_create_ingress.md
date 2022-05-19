---
title: "3. Create Ingress for External Access"
chapter: true
weight: 15
---

## Create Ingress for External Access

The deployment we created will not be accessible from outside the cluster, unless we use a NodePort service or LoadBalancer or Ingress route. We will create an Ingress object to access the application through a fake DNS

:arrow_right: Add a fake DNS entry
```
LBIP=$(kubectl describe svc ingress-nginx-controller  -n ingress-nginx|grep "Ingress:"|awk '{print $NF}')
echo "$LBIP netflix-clone.kcdchennai.in" | sudo tee -a /etc/hosts
```

:arrow_right: Create an Ingress
```
kubectl create ingress netflix-clone-ingress --rule="netflix-clone.kcdchennai.in/*=netflix-clone-service:80" --class=nginx
```

{{% notice tip %}}
To further secure the endpoint, tls can be enabled for the ingress after creating necessary TLS certificates.
{{% /notice %}}
