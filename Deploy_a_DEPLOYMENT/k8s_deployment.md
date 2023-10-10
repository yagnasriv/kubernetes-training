### Kubernetes Deployment Feature

___________________________________________________________________________________________________

- If you can deploy a pod on kubernetes , then why do you need Deployment ?

- Now diff btw a container , pod and deployment 


### Container 
    - created a container using docker, to run this container you provide the specifications on the command line interface 
    - ex: docker run -t "image-name" -p 8080:8080 -v ...
    
___________________________________________________________________________________________________

### POD
    - k8s say instead of writing all these cli you can write all these in yaml file itself, define everything in the yaml file, ex: image name, api_server: name etc
    - pod can be a single or multiple containers
    - why do you create multiple containers ? you have a container which is dependent on other container then you create two/ multiple containers based on the requirement.

___________________________________________________________________________________________________

### Deployment 

    ### then why do we need a deployment when we have a pod ?

    - if you can deploy a container/ application in a pod or application in a pod, then why do we need deployment ? 
    Answer: Deployment is something that supports and provides capabilities like Auto Healing behaviour , Auto scaling behaviour.
    - POD doesnot support this behaviour and Deployment does.
    - zero downtime.
    - Instead of deploying a pod, if you deploy a deployment (zero downtime deployments), it creates a Replica_set and it creates a POD with all these capabilities. 

    <Note: Do Not create a POD directly, Create a POD using Deployment resource and this Deployment resource creates a Replica_Set, which is k8s controller and this will roll out the POD/PODS >

    - Inside of the Deployment yaml file you can say what is the # of replicas of pods you require, sometimes the load will be too high and you might need more replicas. Ex: 100 users should go to pod1 and others to pod2 this is how you achieve High Availability. 

    - Deployment is a yaml manifest 
    - Replica Set will ensure that there are the mentioned pods available 
    <Replica Set is a Kubernetes Controller>
    <Replica Set it wil make sure the desired state is same as the Actuall state on the cluster >
    - Deployment.yaml will roll out the Replica set and it will create the pods.
    - Example: if user deletes 1 pod from 100 and replica set makes sure to re-create the 1 deleted pod and it makes the pod count to 100.

    - There are default controllers and custom controllers available.


<<NOTE: Question, What is the difference between a Container, POD and Deployment >>
<<NOTE: Question, What is the difference between a Container and Replica_Set >>

___________________________________________________________________________________________________

- Once you create a Deployment, it will create a Replica set and Replica sEt will create a POD/PODS for you
- Deployment is an absraction, just create one resource like file.yaml and i will take care of everything. 
- Replica set is Kubernetes controller and k8s controller is a  go-lang application a k8s written which will make sure the specific behavouir is met.
- This is how Kubernetes implements AUTO-HEALING capability by using deployment , replica set and pod.

<NOTE: In real world/Production , you will not create a POD directly, you will create a Deployment and then it creates a Replica set and it creates a POD for you >

___________________________________________________________________________________________________

- Refer to Kubernetes repo in github for examples: https://github.com/kubernetes/examples.git
