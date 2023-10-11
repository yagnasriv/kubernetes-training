# Services in Kubernetes 
___________________________________________________________________________________________________

- Service is a critical component in k8s
- ***** In prod scenario, we dont deploy a pod, we deploy a deployment  *****.
- once you deploy a deployment, you create a service in the world of kubernetes and why we create service and what is the importance of the service ? 

- Why do we need a service in k8s ? 
    - No service, Then --> What if there is no concept of services in k8s , then a scenaio of no service ?
    - usually a developer will deploy a pod as a deployment in k8s and that deployment will create a replica set and that replica set will create a pod, 
    - say we have requirement of creating 3 replicas


    $$
                                        ---> POD1 --> IP_Address 172.6.10.1                     ---> 172.6.10.11
        Deployment ---> Replica_Set = 3 ---> POD2 --> IP_Address 172.6.10.2 - Auto_Healing &    ---> 172.6.10.12
                                        ---> POD3 --> IP_Address 172.6.10.3                     ---> 172.6.10.15
    $$


    - This is where are auto healing happens the testers or end users will not be able to access the pods since the ip address got changed after auto healing and This is where the Service - SVC comes in.
    - When a Service AKA SVC is applied on top of a Deployment, you are informing the end users not to login into the pods using the ip address, instead they can go to SVC and from there they can access the PODS.       
    - SVC feature is added on top of the Deployment, which acts a Load balancer and with the help of a component called kubeproxy the end users will be able to access the PODS
    - Instead of going to the ip address, and there are 3 different projects trying to access, when the pod is going down we have auto-healing behaviour and the pods gets re-created with a new ip addresses and instead of providing the new ip addresses to the end-users, you change this behaviour simpy by creating a service on top of it.
    - Service acts as a LOAD BALANCER, it acts as load balancer by using a component called KUBEPROXY.
    - Service is offering Load Balancing. 
    - So the Developer says, instead of accessing the application through ip address, you can access the application using the service URL.
        - Example: application_name.default.svc 
    - This is the name of the service that k8s provided.
    - Now end users can access the applications through the service ip address / load balancer ip address. 
    - KubePROXY is this service equally distributes the load to the pods from the incoming requests. 

        Deployment --> Service - SVC --> Replica set --> PODS

### ADVANTAGES OF SERVICE IN K8S

1. Advantage of Service AKA SVC in Kubernetes it offers Load Balancing.
2. 2nd advantage is Service Discovery - 

________________________________________________________________________________

*** What is an ideal POD size ? it depends on the no. of concurrent users and no. of users/ no. of requests one replica of your application can handle ****

__________________________________________________________________________________
