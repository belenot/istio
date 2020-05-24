# httpbin

## Description

This configuration represents external resource [httpbin](https://httpbin.org) in ISTIO
service mesh.

## Files

http-service.yaml - Used for adding domain name in kubernetes cluster

httpbin-serviceentry.yaml - Creates rule for envoy to route traffic with specified (httpbin) host
name to specified endpoints. Resolution will be appealed only in service-meshed workloads

httpbin-endpoints.yaml - Creates endpoints for httpbin-service.yaml. Works for all workloads.
Use either serviceentry(service-mesh only) either endpoints(project-wide)

httpbin-virtualservice.yaml - Creates route mesh->istio-egressgateway->httpbin.
Uses istio-system/nginx2-egressgateway gateway

## Boot

### Prerequisites

Should be created nginx2-egressgateway gateway in istio-system namespace with egressgateway service.

### Service + ServiceEntry

```sh
kubectl apply \
    -f httpbin-service.yaml \
    -f httpbin-serviceentry.yaml
```

### Service + Endpoints

```sh
kubectl apply \
    -f httpbin-service.yaml \
    -f httpbin-endpoints.yaml
```

### Route through egressgateway

```sh
kubectl apply \
    -f httpbin-service.yaml \
    -f httpbin-serviceentry.yaml \
    -f httpbin-virtualservice.yaml
```

### Cleanup

```sh
kubectl delete svc,virtualservice,serviceentry -l app=httpbin --ignore-not-found=true
```