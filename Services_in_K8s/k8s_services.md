# Services in Kubernetes 
___________________________________________________________________________________________________

- Service is a critical component in k8s
- ***** In prod scenario, we dont deploy a pod, we deploy a deployment  *****.
- once you deploy a deployment, you create a service in the world of kubernetes and why we create service and what is the importance of the service ? 

- Why do we need a service in k8s ? 
    - No service, Then --> What if there is no concept of services in k8s , then a scenaio of no service ?
    - usually a developer will deploy a pod as a deployment in k8s and that deployment will create a replica set and that replica set will create a pod, 
    - say we have requirement of creating 3 replicas, 

        
        Deployment ---> Replica Set = 3  ---> POD1 --> Ip Address 172.6.10.1   [After autohealing      ---> 172.6.10.11
                        (desired state   ---> POD2 --> Ip address 172.6.10.2  the ip Address of pods   ---> 172.6.10.12   
                        is set to 3)     ---> POD3 --> Ip address 172.6.10.3    get to change]         ---> 172.6.10.15

                        <***** This is where are auto healing the testers or end users will not be able to access
                        the pod since the ip address got changed after auto healing and This is where the Service - SVC comes in>

        
    - SVC feature is added on top of the Deployment, which acts a Load balancer and with the help of kubeproxy the end users will be able to access the PODS

        Deployment --> Service - SVC --> Replica set --> PODS



*** What is an ideal POD size ? it depends on the no. of concurrent users and no. of users/ no. of requests one replica of your application can handle ****