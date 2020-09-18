# Deploying Wordpress application using Kubernetes

## Create Cluster

```
kind create cluster
```

## Apply Kubernetes Resources

```shell
# Config Map
kubectl apply -f secrets.yaml

# Persistent Volume Claims
kubectl apply -f volume.yaml

# Deployment
kubectl apply -f deployment-mysql.yaml
kubectl apply -f deployment-wordpress.yaml

```

### Port Forward

```shell
# Port Forward Remote Port 80 to Local 4433
kubectl port-forward svc/wordpress 4433:80
```

### Connect to MySQL Pod

```
# Getting into the Container
kubectl exec --stdin --tty <podname> -- /bin/sh

# Connect to MySQL
mysql -u root -p

# Run SQL Queries
show databases;
select * from wordpress.wp_users;
```