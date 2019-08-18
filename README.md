# canary Sample

#!/bin/bash

eval $(minikube docker-env)
cd nginx-proxy && docker build -t app-ui:proxy-v1.0 .
cd ../stable-app && docker build -t app-ui:stable .
cd ../canary-app && docker build -t app-ui:canary .

cd ..

kubectl apply -f stable-manifest
kubectl apply -f canary-manifest
kubectl apply -f nginx-manifest
