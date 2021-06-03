# Kubernetes

Sep 1:  Install apt-transport-https.

        sudo apt install -y apt-transport-https
        
        
Step 2: Add the Kubernetes Key.

        curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
        
        
Step 3: And add the Kubernetes Repository by creating a new repo.list file on the '/etc/apt/sources.list.d' directory.

        cd /etc/apt/
        
        sudo vim sources.list.d/kubernetes.list
        
        
Step 4: paste kubernetes repository below.
        deb http://apt.kubernetes.io/ kubernetes-xenial main
        
        
Step 5: Now update the repository and install kubeadm packages using apt commands below.
        sudo apt update
        sudo apt install -y kubeadm kubelet kubectl
        
        
Kubernetes Cluster Initialization

Step 1: Init Kubeadm
        sudo kubeadm init --pod-network-cidr=10.244.0.0/16
        
Step 2 : Create a Directory for the Kubernetes Cluster
         mkdir -p $HOME/.kube
         sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
         sudo chown $(id -u):$(id -g) $HOME/.kube/config
         
         
Step 3: Pod Network Add-On (Flannel)
        kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
        
Join Worker Node to Cluster

Step 1: Copy and past from master node 

Done !

Check:  kubectl get nodes
