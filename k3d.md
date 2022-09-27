wget -q -o - https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

k3d --help
  166  chmod +x kubectl
  167  sudo mv kubectl /usr/local/bin
  168  ls/usr/local/bin
  169  ls /usr/local/bin
  170  kubectl version --client
  171  kubectl version --short
  172  k3d cluster create my_learning_cluster
  173  k3d cluster create learningcluster
  174  k3d cluster list
  175  k3d node list
  176  docker ps
  177  k3d cluster create multinode --agents 2 --servers 1

  
  
chmod +x kubectl

sudo mv kubectl /usr/local/bin

kubectl version --client

k3d cluster create mycluster

k3d cluster list

k3d node list

docker ps

k3d cluster stop mycluster

k3d cluster start mycluster

k3d cluster delete mycluster

k3d cluster create multinodecluster --agents 3 --servers 1

k3d node create myagent --role agent --cluster multinodecluster
