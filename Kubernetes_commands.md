### What is Kubectl?

kubectl is the Kubernetes command-line tool. 
It allows us to run commands against Kubernetes clusters — deploying applications, inspecting and managing cluster resources, and viewing logs.


## Getting Cluster Info

$ kubectl cluster-info


### Viewing Nodes Information

$ kubectl get nodes

$ kubectl get nodes -o wide

$ kubectl describe no

$ kubectl get no -o yaml

$ kubectl get node –select or =label _name

$ kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type==”ExternalIP”)].address}’

$ kubectl top node node_name


 
### Viewing Pods Information

$ kubectl get po

$ kubectl get pod

$ kubectl get pods

$ kubectl get pods --all-namespaces

$ kubectl get pods -A

$ kubectl get pods -n NS_NAME

$ kubectl get po -o wide

$ kubectl describe pods POD_NAME -n NS_NAME

$ kubectl get po –show-labels

$ kubectl get po -l app=nginx

$ kubectl get po -o yaml

$ kubect l get pod pod_name -o yaml –export

$ kubect l get pod pod_name -o yaml –export > file_name.yaml

$ kubectl get pods –field-selector status.phase=Running

$ kubectl run POD_NAME -n NS_NAME --image=POD_IMAGE -- {command}

$ kubectl run POD_NAME -n NS_NAME --image=POD_IMAGE --command {command}


### Creating a Pod

$ kubectl create -f name_of_file

$ kubectl apply -f name_of_file

$ kubectl run pod_name –image=ngi nx –restart=Never

$ kubectl run pod_name –generator =run-pod/v1 –image=nginx

$ kubectl run pod_name –image=nginx –restart=Never


### Viewing NameSpaces Information

### Namespaces

$ kubectl get namespaces

$ kubectl get namespaces --show-labels

$ kubectl get ns NS_NAME

$ kubectl describe ns NS_NAME

$ kubectl get ns -o yaml

## Working with other namespaces:

$ kubectl get pods -n NS_NAME

$ kubectl get rs -n NS_NAME

$ kubectl get all -n NS_NAME

## Getting Pods from All Namespaces:

$ kubectl get pods -A

$ kubectl get pods --all-namespaces

## Creating/Deleting

$ kubectl apply -f namespace.yaml

$ kubectl create ns NS_NAME

$ kubectl delete ns NS_NAME

## Labeling Resources

$ kubectl label RESOURCE_TYPE RESOURCE_NAME key=value

------------------------------------------


### Viewing Deployments Information

$ kubectl get deploy

$ kubectl get deploy -o wide

kubectl get deploy --show-labels

kubectl get deploy -n NS_NAME

kubectl get deploy -o yaml

kubectl describe deploy -n NS_NAME

kubectl delete deploy NS_NAME


### Viewing Services Information

$ kubectl get svc

$ kubectl describe svc

$ kubectl get svc -o wide

$ kubectl get svc --all-namespaces

$ kubectl get svc -o yaml

$ kubectl get svc –show-labels

### Viewing DaemonSets Information

$ kubectl get ds

$ kubectl get ds –all-namespaces

$ kubectl describe ds [daemonset _name] -n [namespace_name]

$ kubectl get ds [ds_name] -n [ns_name] -o yaml


### Viewing Events Information

$ kubectl get events

$ kubectl get events -n kube-system

$ kubectl get events -w


### Logs

$ kubectl logs pod_name

$ kubectl logs –since=1h pod_name

$ kubectl logs –tail =20 pod_name

$ kubectl logs -f -c container_name pod_name

$ kubectl logs pod_name > pod.log


### Service Accounts

$ kubectl get sa

$ kubectl get sa -o yaml

$ kubectl get serviceaccounts default -o yaml > ./sa.yaml

$ kubectl replace serviceaccount default -f. /sa.yaml


### ReplicaSets

$ kubectl get rs

$ kubectl describe rs

$ kubectl get rs -o wide

$ kubectl get rs -o yaml


### Roles

$ kubectl get roles –all-namespaces

$ kubectl get roles –all-namespaces -o yaml

### Secrets

$ kubectl get secrets

$ kubectl get secrets –all-namespaces

$ kubectl get secrets -o yaml

### ConfigMaps

$ kubectl get cm

$ kubectl get cm –all-namespaces

$ kubectl get cm –all-namespaces -o yaml

### Ingress

$ kubectl get ing

$ kubectl get ing –all-namespaces

Kubectl Cheat Sheet – PersistentVolume

$ kubectl get pv

$ kubectl describe pv

$ kubectl get pvc

$ kubectl describe pvc

### StorageClass

$ kubectl get sc

$ kubectl get sc -o yaml

### MultipleResources

$ kubectl get svc, po

$ kubectl get deploy, no

$ kubectl get all

$ kubectl get all –all-namespaces


### Changing Resource Attributes

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


### Nodes/Pods

$ kubectl delete node [node_name]

$ kubectl delete pod [pod_name]

$ kubectl edit node [node_name]

$ kubectl edit pod [pod_name]


### Deployments/Namespaces

$ kubectl edit deploy deploy_name

$ kubectl delete deploy deploy_name

$ kubectl expose deploy deploy_name –port=80 –type=NodePort

$ kubectl expose deployment pod-info-app --name=pod-info-svc --type=ClusterIP --port=80 –target-port=80

$ kubectl expose deployment pod-info-app --name=pod-info-svc --type=ClusterIP --port=80 --target-port=80 --dry-run=client -o yaml

$ kubectl scale deploy deploy_name –replicas=5

$ kubectl delete ns

$ kubectl edit ns ns_name


## Services

$ kubectl edit svc [svc_name]

$ kubectl delete svc [svc_name]

### DaemonSets

$ kubectl edit ds [ds_name] -n kube-system

$ kubectl delete ds [ds_name]

### ServiceAccounts

$ kubectl edit sa [sa_name]

$ kubectl delete sa [sa_name]

### Annotate

$ kubectl annotate po [pod_name] [annotation]

$ kubectl annotate no [node_name]


### Services Creating a Service

$ kubectl create svc nodeport [svc_name] –tcp=8080:80


### Creating a Deployment

$ kubectl create -f name_of_file

$ kubectl apply -f name_of_file

$ kubectl create deploy deploy_name –image=nginx:latest

$ kubectl scale deployment deploy_name --replicas 4

### hotizontal pod autosaceler

$ kubectl autoscale deployment deploy_name --min=4 --max=6 --cpu-precent=80

$ kubectl get hpa

### Rollout

$ kubectl set image deployment/deploy_name k8sphp=adv4000/k8sphp:version2 --record

### To quick view running deploy/rollout status

$ kubectl rollout status deployment/deploy_name 

### Showing history of updates

$ kubectl rollout history deployment/deploy_name

### Rollout to prevoius version

$ kubectl rollout undo deployment/deploy_name 

### Rollout on specific chooesd version of history

$ kubectl rollout undo deployment/deploy_name --to-revision=2

### Redeploing current version of image (e.g. latest)

$ kubectl rollout restart deployment/deploy_name 

### Delete Deployment

$ kubectl delete deployments deploy_name



### Interactive Pod

$ kubectl run pod_name –image=busybox –rm -it –restart=Never — sh


### Output YAML to a File

$ kubectl create deploy deploy_name –image=ngi nx –dry-run -o yaml > deploy.yaml

$ kubectl get po pod_name -o yaml –export > pod. yaml

### Getting Help

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
