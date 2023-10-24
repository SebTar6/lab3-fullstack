# lab3-fullstack
Lab 3 cloud full-stack programming


This YAML file creates the "lab3" namespace, and then defines a "sidecar-pod" pod with two containers. The first container "busybox-con" uses the BusyBox image and writes the date every 5 seconds to the file "/var/log/date.log". The second container "nginx-con" uses the Nginx image and shares this file via a shared volume of type hostPath.

After using this YAML file, you can validate the correctness of the "sidecar-pod" pod using portforwarding and the "curl" program. Here's how to do it:

1. Apply the YAML file using:
- kubectl apply -f lab3-sprawko.yaml

2. To get information about running pods:
- kubectl get pods -n lab3
  or:
- kubectl describe pod sidecar-pod -n lab3
   
4. Create a portforwarding to access the server:
- kubectl port-forward -n lab3 sidecar-pod 8080:80
  
3. Now you can use "curl" to retrieve the contents of the "/var/log/date.log" file:
- curl http://localhost:8080/var/log/date.log
  
This will retrieve the contents of the "date.log" file from the Nginx server running in the second container in the "sidecar-pod" subdivision.
