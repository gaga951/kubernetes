

$ eksctl version

$ eksctl get cluster

# Enable kubectl to speak to the cluster:
$ aws eks update-kubeconfig --name dev --region us-east-1

$ kubectl version --short --client

# Use eksctl to provision an EKS cluster with three worker nodes in us-east-1. Use Kubernetes version 1.18 or later.

$ eksctl create cluster --name dev --version 1.18 --region us-east-1 --nodegroup-name standard-workers --node-type t3.micro --nodes 3 --nodes-min 1 --nodes-max 4 --managed



kubectl get pods -o=name -n namepsacename | grep searchedname


View the newly created dev EKS cluster:

eksctl get cluster

Enable kubectl to speak to the cluster:

aws eks update-kubeconfig --name dev --region us-east-1


kubectl get deployment
kubectl get pod
kubectl get rs
kubectl get node
kubectl get service

Curl the external IP of the NGINX LoadBalancer Service external IP:

curl <NGINX_SERVICE_EXTERNAL_IP>

---------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    env: dev
spec:
  replicas: 3
  selector:
    matchLabels:
      env: dev
  template:
    metadata:
      labels:
        env: dev
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: nginx-svc
  labels:
    env: dev
spec:
  type: LoadBalancer
  ports:
  - port: 80
  selector:
    env: dev
---------------------------------------

