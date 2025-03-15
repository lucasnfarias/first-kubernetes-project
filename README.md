# First Kubernetes Project

## Requisites

- kubectl
- kind

## How to run (self-managed)

### CREATE

```sh
# create cluster based on `kind.yaml` config
kind create cluster --config kind.yaml --name my-first-cluster

# create namespace
kubectl create namespace first-app

# create pod based on `pod.yaml` config on namespace `first-app`
kubectl apply -f pod.yaml -n first-app

# create pods with replicaset
kubectl apply -f replicaset.yaml -n first-app

# create pods with deployment
kubectl apply -f deployment.yaml -n first-app

# create the whole shebang
kubectl apply -f k8s -n first-app
```

### DELETE

```sh
# delete replicaset
kubectl delete rs nginx -n first-app

# delete pod
kubectl delete pod nginx -n first-app

# delete cluster
kind delete cluster --name my-first-cluster
```

### GET

```sh
# get nodes
kubectl get nodes

# get pods from namespace first-app
kubectl get pods -n first-app
```

### FORWARD PORTS

```sh
# forward port from pod
kubectl port-forward pod/nginx -n first-app 8080:80

# forward port from service
kubectl port-forward svc/nginx-svc -n first-app 8080:80
```

### History & Rollback

```sh
# get deployment history
kubectl rollout history deployment/app-ts -n first-app

# rollback to the previous version (or use --to-revision to set a specific version to rollback)
kubectl rollout undo deployment/app-ts -n first-app
```

## Docker Hub

We used [Docker Hub](https://hub.docker.com/) to host our container image

```sh
# build image
docker build -t first-cluster-api:v1 .

# push image
docker push lucasnfarias/first-cluster-api
```
