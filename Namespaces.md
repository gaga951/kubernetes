#  Kubernetes Resources: Namespaces
 

https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/

Namespaces allow us to isolate resources for use by the different users of the cluster, to work on different projects. 
Each `namespace` can be assigned a quota and defined access rules and policies.
 
##  Working with Namespaces
 
To obtain the list of `Namespaces` we execute:
 
 kubectl get namespaces
 NAME STATUS AGE
 default Active 1d
 kube-public Active 1d
 kube-system Active 1d
 
*  `default` : Default namespace.
*  `kube-system` : Namespace created and managed by Kubernetes.
*  `kube-public` : Namespace accessible by all users, reserved for internal use of the cluster.
 
To create a new `Namespace` :
 
 kubectl create ns nwprj1
 namespace "nwprj1" created
 
Another way to create a `Namespace` is from a yaml file with its definition:
 
 apiVersion: v1
 kind: Namespace
 metadata:
 name: nwprj1
 
We can see the characteristics of the new namespace:
 
 kubectl describe ns nwprj1
 Name: nwprj1
 Labels: <none>
 Annotations: <none>
 Status: Active
 
 No resource quota.
 
 No resource limits.
 
And its definition yaml:
 
 kubectl get ns nwprj1 -o yaml
 
 apiVersion: v1
 kind: Namespace
 metadata:
 creationTimestamp: 2018-05-23T16: 19: 58Z
 name: nwprj1
 resourceVersion: "152566"
 selfLink: / api / v1 / namespaces / nwprj1
 uid: 2306825c-5ea5-11e8-ab66-fa163e99cb75
 spec:
 finalizers:
 - kubernetes
 status:
 phase: Active
 
##  Create resources in a namespace
 
To create a resource in a `namespace` we must indicate the name of the namespace in the` namespace` tag in its definition:
 
 apiVersion: apps / v1
 kind: Deployment
 metadata:
 name: nginx
 namespace: nwprj1
 ...
 
We can also create them without the yaml file:
 
 kubectl run nginx --image = nginx -n nwprj1
 
 deployment.apps "nginx" created
 
 kubectl get deploy -n nwprj1
 NAME DESIRED CURRENT UP-TO-DATE AVAILABLE AGE
 nginx 1 1 1 1 15s
 
And we create the associated service:
 
 kubectl expose deployment / nginx --port = 80 --type = NodePort -n nwprj1
 service "nginx" exposed
 
 kubectl get services -n nwprj1
 NAME TYPE CLUSTER-IP EXTERNAL-IP PORT (S) AGE
 nginx NodePort 10.107.121.169 <none> 80: 30352 / TCP 10s
 
##  Setting a default namespace
 
We can indicate in a certain context (a context determines the cluter and the user that we can use) a `namespace` , in such a way that when we use that context the indicated` namespace` will be used , and it will not be necessary to indicate it with the option `-n` . For this, it is necessary to determine the context in which we are working:
 
 kubectl config current-context
 kubernetes-admin @ kubernetes
 
And then I modify the context by adding the namespace that I want to use by default.
 
 kubectl config set-context kubernetes-admin @ kubernetes --namespace = nwprj1
 Context "kubernetes-admin @ kubernetes" modified.
 
##  Deleting a namespace
 
Deleting a `namespace` deletes all the resources that we have created in it.
 
 kubectl delete ns nwprj1
 namespace "nwprj1" deleted
