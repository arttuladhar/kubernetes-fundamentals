# Installing kubectl
brew install kubectl

# Applying KubeCtl Applying Resource Configuration
kubectl apply -f <file1> -f <file2>

# Get Pods
kubectl get pods -n namespace

# List all pods in all namespaces
kubectl get pods --all-namespaces

# Describe Pod
kubectl describe pod pod_name

# List a particular deployment
kubectl get deployment my_deployment

# Delete a Deployment
kubectl delete deployment my_deployment

# dump pod logs (stdout)
kubectl logs my_pod_name

# Port Forward Pod to local Machine
kubectl port-forward redis-izl09 6379

# Get Services
kubectl get services -n namespace

# Describe Service
kubectl describe service service_name