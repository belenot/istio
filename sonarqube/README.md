# sonarqube

## Description

This configuration exposes sonarqube server.

## Boot

### Prerequisites

Ingressgateway istio-system/istio-ingressgateway should be configured for accepting traffic
on port HTTPS 443.

Accessible on **https://<ingress-host>:443/sonarqube**

### Deploy

```sh
kubectl apply \
    -f sonarqube-deployment.yaml \
    -f sonarqube-service.yaml \
    -f sonarqube-virtualservice.yaml
```

### Cleanup

```sh
kubectl delete \
    -f sonarqube-deployment.yaml \
    -f sonarqube-service.yaml \
    -f sonarqube-virtualservice.yaml
```