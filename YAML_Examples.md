### namespace.yaml:
---
apiVersion: v1
kind: Namespace
metadata:
  name: GGa-1
  labels:
    cost_object: "1200"
    team_code: GGa
---

### Pod Manifest Example:
---
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
spec:
  containers:
  - name: myapp-container
    image: busybox:1.34
    command: ['sh', '-c', 'echo Hello Kubernetes! && sleep 3600']
---
