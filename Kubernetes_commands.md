# Viewing Resource Information

## Nodes

$ kubectl get nodes

$ kubectl get no - o wide

$ kubectl describe nodes

$ kubectl get nodes - o yaml

$ kubectl get node -- selector =[label_name]

$ kubectl get nodes - o jsonpath='{ . items[ * ] . status. addresses [ ?( @. t ype==" External IP" ) ] . address} '

$ kubectl top node [ node_name]

## Pods
$ kubectl get po

$ kubectl get po - o wide

$ kubectl describe po

$ kubectl get po --show-labels

$ kubectl get po - l app=nginx

$ kubectl get po - o yaml

$ kubectl get pod [ pod_name] - o yaml - - export

$ kubectl get pod [ pod_name] - o yaml - - export > nameof f i l e. yaml

$ kubectl get pods --field- selector status. phase=Running


## Namespaces

$ kubect l get ns

$ kubect l get ns - o yaml

$ kubect l descr i be ns

## Deployments
$ kubect l get depl oy
$ kubect l descr i be depl oy
$ kubect l get depl oy - o wi de
$ kubect l get depl oy - o yaml

## Services
$ kubectl get svc
$ kubectl describe svc
$ kubectl get svc - o wide
$ kubectl get svc - o yaml
$ kubectl get svc --show-labels

## DaemonSets
$ kubect l get ds
$ kubect l get ds - - al l - namespaces
$ kubect l descr i be ds [ daemonset _name] - n [ namespace_name]
$ kubect l get ds [ ds_name] - n [ ns_name] - o yaml

## Events
$ kubect l get event s
$ kubect l get event s - n kube- syst em
$ kubect l get event s - w

## Logs
$ kubect l l ogs [ pod_name]
$ kubect l l ogs - - si nce=1h [ pod_name]
$ kubect l l ogs - - t ai l =20 [ pod_name]
$ kubect l l ogs - f - c [ cont ai ner _name] [ pod_name]
$ kubect l l ogs [ pod_name] > pod. l og

## ServiceAccounts
$ kubect l get sa
$ kubect l get sa - o yaml
$ kubect l get ser vi ceaccount s def aul t - o yaml > . / sa. yaml
$ kubect l r e

## ReplicaSets
$ kubect l get r s
$ kubect l descr i be r s
$ kubect l get r s - o wi de
$ kubect l get r s - o yaml

## Roles
$ kubect l get r ol es - - al l - namespaces
$ kubect l get r ol es - - al l - namespaces - o yaml

## Secrets
$ kubect l get secr et s
$ kubect l get secr et s - - al l - namespaces
$ kubect l get secr et s - o yaml

## ConfigMaps
$ kubect l get cm
$ kubect l get cm - - al l - namespaces
$ kubect l get cm - - al l - namespaces - o yaml

## Ingress
$ kubectl geting
$ kubectl geting -- all -namespaces

## PersistentVolume
$ kubectl get pv
$ kubectl describe pv

## PersistentVolumeClaim
$ kubectl get pvc
$ kubectl describe pvc

# ViewingResource Information (cont.)

## StorageClass
$ kubectl get sc
$ kubectl get sc - o yaml

## MultipleResources
$ kubectl get svc, po
$ kubectl get deploy, no
$ kubectl get all
$ kubectl get all -- all -namespaces

# ChangingResourceAttributes

## Taint
$ kubectl taint [node_name] [ taint_name]

## Labels
$ kubectl label [ node_name] disk type=ssd
$ kubectl label [ pod_name] env=prod

## Cordon/Uncordon
$ kubectl cordon [ node_name]
$ kubectl uncordon [ node_name]

## Drain
$ kubectl drain [ node_name] Nodes/Pods
$ kubectl delet e node [ node_name]
$ kubectl delet e pod [ pod_name]
$ kubectl edit node [ node_name]
$ kubectl edit pod [ pod_name]

## Deployments/Namespaces
$ kubect l edi t depl oy [ depl oy_name]
$ kubect l del et e depl oy [ depl oy_name]
$ kubect l expose depl oy [ depl oy_name] - - por t =80 - - t ype=NodePor t
$ kubect l scal e depl oy [ depl oy_name] - - r epl i cas=5
$ kubect l del et e ns
$ kubect l edi t ns [ ns_name]

## Services
$ kubect l edi t svc [ svc_name]
$ kubect l del et e svc [ svc_name]

## DaemonSets
$ kubect l edi t ds [ ds_name] - n kube- syst em
$ kubect l del et e ds [ ds_name]

## ServiceAccounts
$ kubect l edi t sa [ sa_name]
$ kubect l del et e sa [ sa_name]

## Annotate
$ kubect l annot at e po [ pod_name] [ annot at i on]
$ kubect l annot at e no [ node_name]

# AddingResources

## CreatingaPod
$ kubect l cr eat e - f [ name_of _f i l e]
$ kubect l appl y - f [ name_of _f i l e]
$ kubect l r un [ pod_name] - - i mage=ngi nx - - r est ar t =Never
$ kubect l r un [ pod_name] - - gener at or =r un- pod/ v1 - - i mage=ngi nx
$ kubect l r un [ pod_name] - - i mage=ngi nx - - r est ar t =Never

## CreatingaService
$ kubect l cr eat e svc nodepor t [ svc_name] - - t cp=8080: 80

## CreatingaDeployment
$ kubect l cr eat e - f [ name_of _f i l e]
$ kubect l appl y - f [ name_of _f i l e]
$ kubect l cr eat e depl oy [ depl oy_name] - - i mage=ngi nx

## InteractivePod
$ kubect l r un [ pod_name] - - i mage=busybox
- - r m - i t - - r est ar t =Never - - sh

## Output YAML to a File
$ kubectl creat edeploy [deploy_name] --image=nginx --dry-run - o yaml >deploy.yaml
$ kubect l get po [ pod_name] - o yaml - - expor t > pod. yaml

## Getting Help
$ kubectl - h
$ kubectl create - h
$ kubectl run - h
$ kubectl explain deploy.spec

# Requests

## APICall
$ kubect l get - - r aw / api s/ met r i cs. k8s. i o/

## Cluster Info
$ kubect l conf i g
$ kubect l cl ust er - i nf o
$ kubect l get component st at uses


