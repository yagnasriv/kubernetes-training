# How to install Kubernetes Cluster and How to Deploy a Kubernetes cluster using MiniKube
___________________________________________________________________________________________________

### creating a Development k8s cluster - Minikube 
- Minikube
- What is Minikube ?
    - Answer: Minikube is a tool that enables you to run Kubernetes clusters locally on your machine can be a AWS EC2 Instance. It's designed for development, testing, and learning purposes, allowing you to set up and experiment with Kubernetes features without needing a full-scale production environment. Minikube runs a single-node Kubernetes cluster inside a virtual machine on your local system. 
    - Minikube is available for Linux, macOS, and Windows systems

- How to install Minikube on Laptop or VM
    - go to minikube official documentation
    - Hypervisor - creating a virtual server 
- How to install Kubectl 
    - With KubeCtl (kubernetes command line interface), you should be able to interact with Kubernetes cluster

- Install Minikube on Linux EC2 instance 
    - Refer to minikube official documentation , refer to : https://minikube.sigs.k8s.io/docs/start/
    - Pre-requisite : Make sure Docker is installed before installing minikube on the device
    - check minikube if it is installed 
        - syntax: minikube start
- Now install kubectl on Linux EC2 instance
    - Refer to Kubernetes offical documentation, https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/