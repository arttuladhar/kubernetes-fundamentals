# Kubernetes Fundamentals

Materiels for Kubernetes Fundamentals Workshop

## Pre-Requisites

* Kubernetes Cluster
* kubectl

### Setup Kubernetes cluster using kind (Locally)

Install kind - Tool for running K8 Cluster using Docker container

```shell
curl -Lo ./kind "https://kind.sigs.k8s.io/dl/v0.8.1/kind-$(uname)-amd64"
chmod +x ./kind
mv ./kind /usr/local/kind
```

### Create Kubernetes Cluster

```
kind create cluster --name myfirst
```

### Delete Cluster

```
kind delete cluster --name myfirst
```