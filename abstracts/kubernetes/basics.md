# kubernetes.md

## Version
kubectl version --client

## Kind
kind create cluster
kind get clusters
kind delete cluster --name samuelgomes

## Contexts
kubectl cluster-info --context kind-samuelgomes
kubectl config get-contexts
kubectl config use-context kind-samuelgomes

## Pods
kubectl get pods

## Services
kubectl get services
kubectl get svc

## Deployments
kubectl apply -f k8s/deployment.yaml
kubectl get deployments
kubectl rollout undo deployment goserver

## Service Apply
kubectl apply -f k8s/service.yaml

## Port Forward
kubectl port-forward service/goserver-service 3010:3000
kubectl port-forward pod/nginx 9090:80
kubectl port-forward service/goserver-service [i choose the port here]:[service port]

## Exec / Logs
kubectl exec -it [container] bash
kubectl exec -it [pod_name] apk add bash
kubectl exec -it [pod_name] bash
kubectl logs [pod name]

## Ingress / ConfigMap
kubectl describe cm ingress-nginx-controller -n ingress-nginx
kubectl rollout restart deployment -n ingress-nginx ingress-nginx-controller
https://docs.traceable.ai/docs/nginx-ingress

## MongoDB Persistent Volume
https://stackoverflow.com/questions/63047549/how-to-deploy-mongodb-with-persistent-volume-in-kubernetes

## Minikube
minikube ssh -- cat /etc/hosts
https://cloudconfig.hashnode.dev/deploy-a-simple-webapp-and-database-on-minikube
