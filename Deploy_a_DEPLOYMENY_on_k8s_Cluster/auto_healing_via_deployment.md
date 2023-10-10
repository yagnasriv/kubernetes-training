### Auto Scaling and Auto Healing of a Pod

- How to add auto healing and auto scaling capabilites to my cluster ?

- use Deplyoment to get these features 
- Deployment is just a wrapper 
- will work on Deployment.yaml file 
- instead of kind:pod , we use kind:deplyoment for adding auto scaling and auto healing capabilities to a cluster.
- way to deploy apps in k8s
- How to verify the application ? 

    - kubectl log
    - kubectl apply -f pod_name.yaml
    - using kubectl you can debug the applications
    - kubectl logs pods 'pods_name' - you can verify the logs of the pod
    - kubectl describe pod - will print all the information for the everything inside the pod.