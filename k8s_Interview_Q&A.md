### Kubernetes Interview Q&A's

1. What is the diff btw Docker & K8s ?
    - Docker is container plaform and K8s is a container orchestration platform 
    - What K8s adds to the docker is - containers are ephemeral in nature , to avoid this teams can move from docker to K8s
    - supports capabilities like Auto Healing, Auto scaling, Clustering and Enterprise level support like Load balancing.


2. What are the main components in K8s architecture ? 
    - K8s has 2 components,  data plane and control plane
    - Data plance has Kubelet (responsible for pods health like start or stop state), Kubeproxy (networking component of k8s, typically takes care of ip addresses) and container runtime (example for running a java application we require a java runtine, some of the container runtines are docker shim, containerD, cryo etc...) you have to install container runtine on each n every node. 
    - Control plane has API server, scheduler, controller manager, C-CM, ETCD


3. What are the main difference btw the Docker Swarm and Kubernetes ?
    - K8s is quite popular compare to other orchestration services.
    - K8s is suited for large or mid sized enterprises
    - Docker Swarm is suited for small sized compaines, simple to  install n use, 
    - K8s supports advanced networking capabilites compared to Docker Swarm
    - K8s supports third party services.


4. What is the difference between Docker Container and Kubernetes Pod ? 
    - K8s pod is runtime specification , K8s specification is written in a yaml file
    - Docker container specification is written in DockerFile
    - Pod is runtime specification of a container


5. What is a namespace in Kubernetes ?
    - Namespace is a K8s cluster is being accessed by multiple users in a company, 
    - In simple terms, Namespace is a Logicial isolation of resources, network policies, rbac. 
    - Example: There are two projects using same K8s cluster, One project can use namespace1 and other project can use namespace2 without any overlap and authentication process.


6. 