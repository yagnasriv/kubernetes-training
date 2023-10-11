# Services in Kubernetes 
___________________________________________________________________________________________________

- Service is a critical component in k8s
- ***** In prod scenario, we dont deploy a pod, we deploy a deployment  *****.
- once you deploy a deployment, you create a service in the world of kubernetes and why we create service and what is the importance of the service ? 

- ### Why do we need a service in k8s ? 

    - No service, Then --> What if there is no concept of services in k8s , then a scenaio of no service ?
    - usually a developer will deploy a pod as a deployment in k8s and that deployment will create a replica set and that replica set will create a pod, 
    - say we have requirement of creating 3 replicas

        - Deployment.yaml 
            1. creates Replica_Set
            2. creates POD / PODS, Example: IP Address - 172.6.0.1
            3. Auto healing happens
            4. POD recreation
            5. IP Address changes, Exmaple: New IP Address - 172.6.0.5
            6. End user won't be able to connect to Application with new IP Address

        - When you add a "Service / svc" 

        - Deployment.yaml
            1. Adds a Service / svc
            2. create Replica_SET
            3. creates PODs, Example: IP Address: 192.10.0.1
            4. Auto Healing happens
            5. POD get recreated
            6. Ip Address changes, Example: IP Address: 192.10.0.10 
            7. End user will be able to access the Application with the help of "application_name.default.svc" URL


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

___________________________________________________________________________________________________

*** What is an ideal POD size ? it depends on the no. of concurrent users and no. of users/ no. of requests one replica of your application can handle ****

___________________________________________________________________________________________________
