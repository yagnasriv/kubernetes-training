# Deploy a POD on Kubernetes Cluster
___________________________________________________________________________________________________

### Pre-requisites 
- Make sure to understand the difference between docker and kubernetes
- Get to know Kubernetes architecture
- Installation of minikube and kubectl

___________________________________________________________________________________________________

<NOTE: Main reason why companies choose Kubernetes over Docker is because of Cluster>

___________________________________________________________________________________________________

- What is a POD in Kubernetes ?
- How to deploy a POD ?
- How to install your application on POD ? 

___________________________________________________________________________________________________

- In kubernetes the lowest level of Deployment is a POD 
- In Kubernetes you will deploy a container in the form of a POD
- POD is described as a definition of how to run a container .
    - Example: In docker you will run a container like : docker run -t container_name -v mount_details -p port_number_details etc direclty in the command line, but in Kubernetes pod while running a container you provide all these variables in a pod.yaml file itself.
- In Kubernetes wrapper/concept similar to container but it abstracts the user defined commands from pod.yaml file
- In kubernetes you will deploy a pod instead of a container, pod can be a single container or multiple container.
- Assume you are building a pod with single container - only difference 
- In Kubernetes you will deal with yaml files only 
    Example: prod, deployments file etc..
- POD is nothing but a one or group of containers 
- most of the times a pod is a single container, but in few scenarios it has multiple containers like side-car containers or init containers in simple terms for supporting the other container.

___________________________________________________________________________________________________

### Benefits of having multiple containers in a single pod

- If a Pod has two containers, example A and B, both of them can share a network, share a storage and also can communicate over the localhost network like http://localhost:3000 . 
- Both the containers in the POD can share the files 
- In simple terms : There is a container in the kubernetes POD  and this POD has been allocated with a CLUSTER IP ADDRESS and this applications inside the container can be accessed with the help of POD CLuster IP Address.
- IP addresses are not generated for a container, but those are generated for the POD.
- Kubeproxy from the Data plane is the one that generates the cluster ip address to the POD.

___________________________________________________________________________________________________

### What is Kubectl ?

- Like for docker we have docker cli for running the xcommands and in kubernetes we have kubectl we can directly interact with k8s clusters. 
- Kubectl is the cli for k8s cluster
- Example: kubectl get nodes - to get the list of nodes 
___________________________________________________________________________________________________

# Install Kubectl and install minikube and How to deploy a POD 

- Firslty instakk Kubeclt , refer to kubectl installation documentation or kubernetes offical documentation for installation 
- Next install local k8s either minikube, k3s , kind , microk8's.
- Kind is another cluster 

- Next install minikube, refer to minikube installation documentation 

- minikube is a commandline tool that will help you creating a cluster. 
- In real time we will have multi node clusters in general 3 - master nodes and n number of worker nodes
- Once the installation of minikube and kubectl is completed then the next is How to deploy a POD ? 
- create a yaml file, by referring to kubernetes pod description, and save it as pod.yaml
- use command: "kubectl create -f pod.yaml" to create the pod in the cluster
- use command : "kubectl get nodes" to view the available nodes
- use command: "kubectl get pods" to view the pods created in the cluster
- Login into the kubernetes cluster using command : minikube ssh and 
curl ip_address_of_the_pod 
'NOTE: (as mentioned previously, the ip address of the pod has been generated from the cluster itself and we can use the pod ip address to login into the cluster to see if the application is running or not)'


- Review kubernetes cheat sheet available on kubernetes official website 

- Installed first pod and accessed the pod by ssh into it using the ip address , now what is next ?

you can also delete the pod using commands : kubectl delete 'pod-name'