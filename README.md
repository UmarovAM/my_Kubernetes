### my_Kubernetes 
Установка с помощью 
kubeadm

# 1. Install k8s to linux install -y kubelet kubeadm kubectl

 sudo apt-get install -y apt-transport-https ca-certificates curl
 

   27  sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
   28  echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo 
tee /etc/apt/sources.list.d/kubernetes.list

   29  sudo apt-get update
   
   30  sudo apt-get install -y kubelet kubeadm kubectl
  
установка и на вторую ноду 

## Ставим docker

28  docker run hello-world
   29  kubeadm init
   30  find / -name *.toml
   31  rm /etc/containerd/config.toml
   32  systemctl restart containerd.service
   33  kubeadm init
   
## команда доюавления других нод в кластер   
export KUBECONFIG=/etc/kubernetes/admin.conf
kubeadm join 192.168.31.30:6443 --token 3kv1tm.jhvhst7oq19f1tkd \       
        --discovery-token-ca-cert-hash sha256:1d6d12aeb0b86eed4a5d00d2be4f0f87ccd44f728bad0a429d119e2c4bea527f
