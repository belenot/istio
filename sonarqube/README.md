# sonarqube

## Description

This configuration exposes sonarqube server.

## Boot

### Prerequisites

Ingressgateway istio-system/istio-ingressgateway should be configured for accepting traffic
on port 9000. (Expose 9000 on service)

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