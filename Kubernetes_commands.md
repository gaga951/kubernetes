### What is Kubectl?

kubectl is the Kubernetes command-line tool. 
It allows us to run commands against Kubernetes clusters — deploying applications, inspecting and managing cluster resources, and viewing logs.


### Kubectl Cheat Sheet – Viewing Nodes Information

$ kubectl get no

$ kubectl get no -o wide

$ kubectl describe no

$ kubectl get no -o yaml

$ kubectl get node –select or =[ label _name]

$ kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type==”ExternalIP”)].address}’

$ kubectl top node [node_name]

 
### Kubectl Cheat Sheet – Viewing Pods Information

$ kubectl get po

$ kubectl get po -o wide

$ kubectl describe po

$ kubectl get po –show-labels

$ kubectl get po -l app=nginx

$ kubectl get po -o yaml

$ kubect l get pod [ pod_name] -o yaml –export

$ kubect l get pod [pod_name] -o yaml –export > nameoffile.yaml

$ kubectl get pods –field-selector status.phase=Running

Load WordPress Sites in as fast as 37ms!

Kubectl Cheat Sheet – Viewing NameSpaces Information

### Namespaces

$ kubectl get ns

$ kubectl get ns -o yaml

$ kubectl describe ns

### Kubectl Cheat Sheet – Viewing Deployments Information

$ kubectl get deploy

$ kubectl describe deploy

$ kubectl get deploy -o wide

$ kubectl get deploy -o yam

### Kubectl Cheat Sheet – Viewing Services Information

$ kubectl get svc

$ kubectl describe svc

$ kubectl get svc -o wide

$ kubectl get svc -o yaml

$ kubectl get svc –show-labels

### Kubectl Cheat Sheet – Viewing DaemonSets Information

$ kubectl get ds

$ kubectl get ds –all-namespaces

$ kubectl describe ds [daemonset _name] -n [namespace_name]

$ kubectl get ds [ds_name] -n [ns_name] -o yaml


### Kubectl Cheat Sheet – Viewing Events Information

$ kubectl get events

$ kubectl get events -n kube-system

$ kubectl get events -w


### Kubectl Cheat Sheet – Logs

$ kubectl logs [pod_name]

$ kubectl logs –since=1h [pod_name]

$ kubectl logs –tail =20 [pod_name]

$ kubectl logs -f -c [container_name] [pod_name]

$ kubectl logs [pod_name] > pod.log


### Kubectl Cheat Sheet – Service Accounts

$ kubectl get sa

$ kubectl get sa -o yaml

$ kubectl get serviceaccounts default -o yaml > ./sa.yaml

$ kubectl replace serviceaccount default -f. /sa.yaml


### Kubectl Cheat Sheet – ReplicaSets

$ kubectl get rs

$ kubectl describe rs

$ kubectl get rs -o wide

$ kubectl get rs -o yaml


### Kubectl Cheat Sheet – Roles

$ kubectl get roles –all-namespaces

$ kubectl get roles –all-namespaces -o yaml

### Kubernetes Cheat Sheet – Secrets

$ kubectl get secrets

$ kubectl get secrets –all-namespaces

$ kubectl get secrets -o yaml

### Kubectl Cheat Sheet – ConfigMaps

$ kubectl get cm

$ kubectl get cm –all-namespaces

$ kubectl get cm –all-namespaces -o yaml

### Kubernetes Cheat Sheet – Ingress

$ kubectl get ing

$ kubectl get ing –all-namespaces

Kubectl Cheat Sheet – PersistentVolume

$ kubectl get pv

$ kubectl describe pv

$ kubectl get pvc

$ kubectl describe pvc

### Kubernetes Cheat Sheet – StorageClass

$ kubectl get sc

$ kubectl get sc -o yaml

### Kubectl Cheat Sheet – MultipleResources

$ kubectl get svc, po

$ kubectl get deploy, no

$ kubectl get all

$ kubectl get all –all-namespaces


### Kubectl Cheat Sheet – Changing Resource Attributes

### Taint

$ kubectl taint [node_name] [taint _name]

### Labels

$ kubectl label [node_name] disktype=ssd

$ kubrectl label [pod_name] env=prod

### Cordon/Uncordon

$ kubectl cordon [node_name]

$ kubectl uncordon [node_name]

### Drain

$ kubectl drain [node_name]

### Kubernetes Cheat Sheet – Nodes/Pods

$ kubectl delete node [node_name]

$ kubectl delete pod [pod_name]

$ kubectl edit node [node_name]

$ kubectl edit pod [pod_name]


### Kubectl Cheat Sheet – Deployments/Namespaces

$ kubectl edit deploy [deploy_name]
$ kubectl delete deploy [deploy_name]
$ kubectl expose deploy [depl oy_name] –port=80 –type=NodePort
$ kubectl scale deploy [deploy_name] –replicas=5
$ kubectl delete ns
$ kubectl edit ns [ns_name]


## Kubectl Cheat Sheet – Services

$ kubectl edit svc [svc_name]

$ kubectl delete svc [svc_name]

DaemonSets

$ kubectl edit ds [ds_name] -n kube-system

$ kubectl delete ds [ds_name]

ServiceAccounts

$ kubectl edit sa [sa_name]

$ kubectl delete sa [sa_name]

Annotate

$ kubectl annotate po [pod_name] [annotation]

$ kubectl annotate no [node_name]

Adding Resources

Kubectl Cheat Sheet – Creating a Pod

$ kubectl create -f [name_of _file]

$ kubectl apply -f [name_of _file]

$ kubectl run [pod_name] –image=ngi nx –restart=Never

$ kubectl run [ pod_name] –generator =run-pod/v1 –image=nginx

$ kubectl run [ pod_name] –image=nginx –restart=Never


### Kubectl Cheat Sheet – Services Creating a Service

$ kubectl create svc nodeport [svc_name] –tcp=8080:80

Kubernetes Cheat Sheet – Creating a Deployment

$ kubectl create -f [name_of _file]

$ kubectl apply -f [name_of _file]

$ kubectl create deploy [deploy_name] –image=ngi nx


### Interactive Pod

$ kubectl run [pod_name] –image=busybox –rm -it –restart=Never — sh


### Output YAMLto aFile

$ kubectl create deploy [deploy_name] –image=ngi nx –dry-run -o yaml > deploy.yaml

$ kubectl get po [pod_name] -o yaml –export > pod. yaml

### Kubectl Cheat Sheet – Getting Help

$ kubectl -h

$ kubectl create -h

$ kubectl run -h

$ kubectl explain deploy.spec

### Requests API Call

$ kubectl get –raw /apis/metrics.k8s.io/

### Cluster Info

$ kubectl config

$ kubectl cluster -info

$ kubectl get componentstatuses
