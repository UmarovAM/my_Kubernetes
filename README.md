### my_Kubernetes 
Установка с помощью 
kubeadm

# 1. Install k8s to linux install -y kubelet kubeadm kubectl

 sudo apt-get install -y apt-transport-https ca-certificates curl
 
 25  nano /etc/apt/sources.list
 
   26  sudo apt-get update
   27  sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
   28  echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo 
tee /etc/apt/sources.list.d/kubernetes.list
   29  sudo apt-get update
   30  sudo apt-get install -y kubelet kubeadm kubectl
   31  history

установка и на вторую ноду 

## Ставим docker
