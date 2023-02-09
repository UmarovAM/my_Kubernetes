### my_Kubernetes 

## Установка с помощью kubeadm

    install k8s to linux install -y kubelet kubeadm kubectl
    sudo apt-get install -y apt-transport-https ca-certificates curl
    sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
    echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

## Устанавливаем пакеты:

    sudo apt-get update
    sudo apt-get install -y kubelet kubeadm kubectl
  
установка и на вторую ноду 

## Ставим docker

docker run hello-world

## Создание кластера
### Инициализируем первую мастер ноду:

    kubeadm init
    swapoff -a
    find / -name *.toml
    rm /etc/containerd/config.toml
    systemctl restart containerd.service
    kubeadm init
   
   echo $KUBECONFIG
   export KUBECONFIG=/etc/kubernetes/admin.conf 
   работает до перезагрузки
   
## Устанавливаем CNI (Например weave):
        kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
   
## Команда добавления других нод в кластер   
        kubeadm join 192.168.31.30:6443 --token 3kv1tm.jhvhst7oq19f1tkd \       
        --discovery-token-ca-cert-hash sha256:1d6d12aeb0b86eed4a5d00d2be4f0f87ccd44f728bad0a429d119e2c4bea527f

        kubeadm join 192.168.31.236:6443 --token ys8zq6.8j37bnwnnhaj4d1p \
        --discovery-token-ca-cert-hash sha256:1241e45f72979940495a598691c4c6b376d76efcea9f8ba28fc0a5f43
## Нормально работающая нода
         watch kubectl get all --all-namespaces
         ![image](https://user-images.githubusercontent.com/118117183/217562866-98603e88-97b5-49aa-87de-42b8070b472c.png)

         kubectl get po -n kube-system
         
![image](https://user-images.githubusercontent.com/118117183/217020377-2aa170bd-1bd9-46ce-981a-0766bc83fc2c.png)

        kubeadm reset #если что то пошло не так
## Helm: деплой проекта
Helm можно использовать как для установки чартов из публичных репозиториев:
Так и для создания и деплоя своих собственных чартов:

         helm repo add brigade https://brigadecore.github.io/charts
         helm install brigade-release brigade/brigade
         helm install my-project

        
