

#### https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

kubectl – A command line tool for working with Kubernetes clusters. 

https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html


eksctl – A command line tool for working with EKS clusters that automates many individual tasks.
https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html



AWS CLI – A command line tool AWS services, including Amazon EKS. 
see Installing, updating, and uninstalling the AWS CLI in the AWS Command Line Interface User Guide. 
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html


After installing the AWS CLI, we recommend that you also configure it. For more information, see Quick configuration with aws configure in the AWS Command Line Interface User Guide.
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-config


There are two getting started guides available for creating a new Kubernetes cluster with nodes in Amazon EKS:

Getting started with Amazon EKS – eksctl – This getting started guide helps you to install all of the required resources to get started with Amazon EKS using eksctl, a simple command line utility for creating and managing Kubernetes clusters on Amazon EKS. At the end of the tutorial, you will have a running Amazon EKS cluster that you can deploy applications to. This is the fastest and simplest way to get started with Amazon EKS.
https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html


Getting started with Amazon EKS – AWS Management Console and AWS CLI – This getting started guide helps you to create all of the required resources to get started with Amazon EKS using the AWS Management Console and AWS CLI. At the end of the tutorial, you will have a running Amazon EKS cluster that you can deploy applications to. In this guide, you manually create each resource required for an Amazon EKS cluster. The procedures give you visibility into how each resource is created and how they interact with each other.
https://docs.aws.amazon.com/eks/latest/userguide/getting-started-console.html


#########################################################################################################################################################################################################################################################


$ eksctl version

# Enable kubectl to communicate to the cluster:
$ aws eks update-kubeconfig --name dev --region us-east-1

$ kubectl version --short --client

# Use eksctl to provision an EKS cluster with 3 worker nodes in us-east-1. Use Kubernetes version 1.20 or later.

$ eksctl create cluster --name dev --version 1.20 --region us-east-1 --nodegroup-name standard-workers --node-type t3.micro --nodes 3 --nodes-min 1 --nodes-max 4 --managed



$ kubectl get pods -o=name -n namepsacename | grep searchedname


# View created dev EKS cluster:

eksctl get cluster

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

