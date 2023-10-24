# .......... Kubernetes course ..........
___________________________________________________________________________________________________
- companies have started moving towards Microservices
- Docker --> containers
- containers vs Virtual machine
- why containers are light weight in nature ?

### Difference btw docker n kubernetes ? 
- ### About why Docker is not considered as a containerisation tool in production

    - Docker is a container platform - docker is makes the container journey very easy
    - when it comes to Kubernetes  - k8s nothing but a container orchestration platform
    - containers are ephemeral in nature (short life /short living in nature/ containers can die and revive anytime)
    - Life of containers is very short, lack of memory issues the containers might die.

- Issues / problems occured with the use of docker

    - Issue 1: Single Host -->
        - say docker is installed on the host machine and it created multiple containers and one of the container is consuming more memory and it is making another container is not able to come up and running and that is an issue called Single host nature of a Docker container.
        - single host is the problem
    - Issue 2: Auto Healing issue -->
        - a user killed a container - then the application running inside the container will not be avaialble to accessble, - auto healing is a behavour without the users manual intervention your container has to start by itself and this is another issue in Docker.
        - Devops engineer will not be able to take care of all the running containers and there has to be a mechanism required called Auto Healing.
    - Issue 3: Auto scaling --> 
        - Ec2 instance/ host - docker is installed - say only one container is installed and this conatainer has 4gb, 4cpu this is the max capacity. 
        - say application has 10,000 users and on a certain occassion the user got bumped to 100000 users , the load gets increaed , to act upon the load this auto scaling feature is required. 
        - either you manually increase the load from 1 to 10 containers or it has to happen automatically.
    - Issue 4: 
        - Docker doesnot support any of your enterprise level applications support
        - application should have Load balancer
        - firewall 
        - auto scale / scaling
        - auto heal
        - API gateways
        - these are few of enterprise level standards and docker does not support these enterprise level standards.
    - Docker is a simple minimilistic problems 



### These are the problems docker does not support 
1. Single host
2. Auto Scaling
3. Auto healing
4. Enterprise level support
(these are main problems)
___________________________________________________________________________________________________

### Kubernetes solves all these problems, 

- By default kubernetes is a cluster 
    - Cluster is basically - group of nodes
    - installed in a master node architecture
    - to practice k8s you can install as a single node
    - in general it is installed as a cluster

- 1st problem: Previously in docker, when a container is consuming more memory it is trying to kill another container 
    - but in Kubernetes, say it has two nodes, and if on one node there are 1 to 99 containers running and if the 99th container is effected by the other containers or a faulty application then immediately this 99th container is being moved to another second node where this 99th pod can work without any issues

    - Kubernetes has a feature called multi-node architecture where if it finds a container or a pod being effected by a faulty node or a faulty application in the node then it immedietly moves the effected pod to a new or another available node.
- 2nd problem : K8s has something called as replication controller (v1 or v2) - basically kubernetes relays on YAML files.
    - Auto Scaling: Replication controller or ReplicaSet , all that you need to do is go to replica_set.YAML file or even in the deployment.YAML file and {add increase my replicas from 1 to 10} whenever the traffic is increased (also supports HPA - Horizontal pod auto scaler) when ever there is load just spin up one more containers.
- 3rd problem: Auto Healing: 
    - whenever there is a damage kubernetes has to control and fix the damage.
    - Controlling the damage: one of the container or pod is going down and k8s has a feature called auto-healing when k8 detects the container is going down it automatically creates and starts a new container. 
    - from API server understand pod/container is going down, k8s will rollout a new pod/container immedietly, end user won't be able to detect the container has gone down.

- 4th problem: Enterprise support nature:
    - k8s orginited from google, people at google use borg.
    - google built Enterprie level container orchestration platform for support issues.
    - since Docker is not used in prod, only docker swarm might be used
