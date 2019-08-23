# Canary using openresty on minikube

This is just an example of using openresty to achieve canary release.

## Getting Started

### Prerequisites
* minikube 1.13+
* docker daemon
* kubectl 1.14+

Associate minikube with docker daemon
```
eval $(minikube docker-env)
```

## Build images
```
docker build -t app-ui:proxy-v1 nginx-proxy/.
docker build -t app-ui:stable stable-app/.
docker build -t app-ui:canary .
```
## Deploy to k8s

### Confirm configmap for openresty setting
change the cluster ip in the default.conf 


### Deploy configmap first

```
kubectl apply -f nginx-proxy/nginx-cm.yaml
```
### Deploy applications
```
kubectl apply -f stable-manifest
kubectl apply -f canary-manifest
```
### Deploy proxy
```
kubectl apply -f nginx-proxy/nginx-svc.yaml
kubectl apply -f nginx-proxy/nginx-deploy.yaml
```
