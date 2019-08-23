# Canary using openresty on minikube

This is just an example of using openresty to achieve canary release.

## Getting Started

### Prerequisites
* minikube 1.3+
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
docker build -t app-ui:canary canary-app/.
```
## Deploy to k8s

### Confirm configmap for openresty setting
```
kubectl cluster-info
#change the cluster ip in the default.conf to your current minikube
set $clusterIp '192.168.99.{your ip}';
```

### Deploy configmap first

```
kubectl apply -f nginx-manifest/nginx-cm.yaml
```
### Deploy applications
```
kubectl apply -f stable-manifest
kubectl apply -f canary-manifest
```
### Deploy proxy
```
kubectl apply -f nginx-manifest/nginx-svc.yaml
kubectl apply -f nginx-manifest/nginx-deploy.yaml
```

