$ wget -q -o - https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash

$ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
  
$ chmod +x kubectl

$ sudo mv kubectl /usr/local/bin

$ ls /usr/local/bin

$ kubectl version --short

$ k3d cluster create mycluster

$ k3d cluster list

$ k3d node list

$ docker ps

$ k3d cluster stop mycluster

 k3d cluster start mycluster

$ k3d cluster delete mycluster

$ k3d cluster create multinodecluster --agents 3 --servers 1

$ k3d node create myagent --role agent --cluster multinodecluster

$ k3d --help
