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
```

### DELETE

```sh
# delete replicaset
kubectl delete rs nginx -n first-app

# delete pod
kubectl delete pod nginx -n first-app

# delete cluster
kubectl delete cluster -n my-first-cluster
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

## Docker Hub

We used [Docker Hub](https://hub.docker.com/) to host our container image

```sh
# build image
docker build -t first-cluster-api:v1 .

# push image
docker push lucasnfarias/first-cluster-api
```
