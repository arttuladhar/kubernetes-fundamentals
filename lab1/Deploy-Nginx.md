# Deploying an Nginx application using Kubernetes

  - [Pod](#pod)
    - [Interacting with Pod](#interacting-with-pod)
  - [Deployment](#deployment)
  - [Services](#services)
  - [Update Image of Deployment](#update-image-of-deployment)

## Pod

```yml
# pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-first-pod
  labels: 
    app: first-pod
    environment: sandbox 
spec:
  containers:
  - name: nginx
    image: nginx
    ports:
    - containerPort: 80
```

Applying Pod Configuration

```
kubectl apply -f pod.yaml
```

### Interacting with Pod

```bash
# Get All Pods
kubectl get pods

# Get More Info on a Pod
kubectl get pod my-first-pod -o wide

# Describe Pod
kubectl describe pod my-first-pod

# Get Logs
kubectl logs my-first-pod

# Delete Pod
kubectl delete pod my-first-pod
```


## Deployment

```yml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: first-nginx
spec:
  selector:
    matchLabels:
      app: first-nginx
  replicas: 2
  template:
    metadata:
      labels:
        app: first-nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

Applying Pod Configuration

```
kubectl apply -f deployment.yaml
```

```bash
# Port Forward to Local Port
k port-forward pod/my-nginx-5fb68d8c94-26w8w 8080:80
```

## Services

```
kind: Service
apiVersion: v1
metadata:
    name: my-first-service
spec:
    type: ClusterIP
    selector:
        app: first-nginx
    ports:
    - protocol: TCP
      port: 8080
      targetPort: 80
```

```bash
# Applying Service
kubectl apply -f service.yaml

# View Services
kubectl get services

# Port Forward to Local Port
kubectl port-forward svc/my-first-service 8081:8080
```

## Updating Deployments

```bash
# Update nginx Image
kubectl set image deployment/first-nginx nginx=nginxdemos/hello

# See Load Balancing
kubectl run -i --tty curl --image=curlimages/curl -- sh
```
