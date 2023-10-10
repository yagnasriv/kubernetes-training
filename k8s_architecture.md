# .......... Kubernetes Architecture ..........
___________________________________________________________________________________________________

### Why Kubernetes is called K8s ?
- 


___________________________________________________________________________________________________

### Difference between Docker and Kubernetes 
- Kubernetes offers 4 different services which docker doesnot support/provide ,
    1. Cluster in behaviour (Single Host)
    2. Auto healing
    3. Auto scaling
    4. Offers multiple Enterprise level support
        - Advanced load balancing
        - Advanced networking etc..

___________________________________________________________________________________________________
# .......... About Kubernetes Architecture ..........
### Components in Kubernets
Kubernetes has control plane and data plane 

## Control plane ( Master Node ) -->
                    1. API server
                    2. etcd
                    3. scheduler 
                    4. controller manager
                    5. ccm - cloud control manager 
## Data Plane (Worker Node )  -->
                    1. Kubelet
                    2. Kubeproxy
                    3. container runtime

what exaclty all these components are ?
___________________________________________________________________________________________________

### Compairing Creating a Container in a Docker with creating a Pod in Kubernetes cluster

- What happens when a container is created in Docker ? 
    - There is a VM , where you installed docker and you created a Dockerfile and build a Docker image.
    - Later using docker build command you build a container image.
    - for running this docker container image we require 'Container runtime' without container runtime docker containers will not be able to built.
    - Docker requires "Docker SHIN" container runtime for running the containers.
    - Docker brdige - supports networking capabilites in docker

___________________________________________________________________________________________________

### What happens when a Pod is created in a Kubernetes ?

- Below use case explains the scenario about creating one master component and one worker component in a pod and its internal supported components


## Master component :

'These are 5 components present inside the Control plane or Master node'

<NOTE: 'Since we have major components in the data plane like kubelet, kubeproxy and container runtime basically responsible for running an application, then what is the use of control plane>

- Since there are enterprise level tools there are certain specific standardswhich need to be followed ,
- when multiple users are trying to access the node and a Core component of kubernets takes all the incoming requests like , iam, sso, security related stuff - basically does all 
    - API server :
        - Acts a core component in Kubernetes and the purpose is exposes your kubernetes to external world. (Heart of the kubernetes).
        - API server is present in master node/ control plane.

    - Scheduler :
        - When a request is received to a API server for scheduling a pod on a available node, that's where a scheduler comes through. To schedule a component on a node, you require a component called "scheduler".
        - scheduler is responsible for scheduling your pods or resources on a nodes. 

    - etcd :
        - key value store 
        - acts a backup service for entire cluster 
        - without etcd you won't have a cluster related information.

    - Controller Manager :
        - k8s supports auto scaling, k8s has some controllers 
        - <example: replica set, one pod is not enough it need two pods to run this application, so our replica set controller makes sure that our application is running to two pods>
        - Controller manager is the one that makes sure this replica set controller is always running.
        - (In Kubernetes by default there are multiple controllers running and control manager is the one that manages ) 

    - Cloud Controller Manager (CCM) :
        - <example: Kubernetes can run on cloud platforms like EKS - Elastic Kubernetes service on AWS, AKS or GKE>
        - Example there is Request to create a load balancer or storage on EKS
        - Cloud control manager is a open source utility 
        - CCM is not required and does not have to be created on your kuberenetes cluster, if you are running kubernetes on ON-Premise 
    



___________________________________________________________________________________________________
# Worker component: 
- ### Data plane or Worker Node is responsible for running your Application
- ### These are the 3 components present inside the Data plane or worker node

    - KUBELET:
        - For running a POD in the kubernetes, you require a KUBELET and container runtime
        - kubelet' is always responsbile for making sure the pod is running, kubelet helps in deplyoing the pod.
        - If the pod is not running in the worker node, then KUBELET will inform kubernetes that the pod is not running and it has to be fixed or restarted.
    - CONTAINER RUNTIME: 
        - Container runtime environment is required for running the application in that particular supported environment
        - <NOTE 'container-runtime' also known as container engine, is a software component that can run containers on a host operating system,>
        - <Example: If you have a Java application on your host machine and if you dont have Java runtime environment then you wont be able to run your Java application, and that is the reason why a Container Runtime is required for running the application>
    - KUBEPROXY: 
        - similary to docker bridge - Kubernetes has Kubeproxy which supports the networking capabilites and load balancing capabilities.
        - Every pod you are creating in a cluster need to be allocated with an IP address/ IP tables on linux machine, Load Balancing capabilities and it is taken care by 'KUBEPROXY'
