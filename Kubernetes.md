Kubernetes
KUBERNETES
kubectl proxy --v=4 --address=0.0.0.0 --accept-hosts='^.*' -p port
 
10.95.123.29:8000/api/v1/namespaces/devenvcase-management-v2/services/casemgmtservice/proxy/case-mgmt/v2/debugging
 
kubectl get secret keyname -o yaml  : displays the output in the form of yaml format.
Kubernetes uses liveness probes to know when to restart a container. Kubernetes uses readiness probes to decide when the container is available for accepting traffic.
 
Kinds of controllers : 5
 
1) replica sets - ensure that a specified number of replicas for a pod are running at alltimes
2) Service - helps pods to communicate with one another and to allow the traffic from and to the pods also does loadbalancing
- A service is responsible for enabling network access to a set of pod
3 kinds of services
1) Internal : IP is only reachable within the cluster
2) External : endpoint available through node ip: node port
3) load balancer : Exposes application to the internet with a load balancer.
3) deployment - creates pods
   -  a logical group with some management capabilities tied to it.
   - A deployment is responsible for keeping a set of pods running.
   - provides declarative updates for pods and replicaSets which can be provided using yaml file
4) DaemonSets - ensures that all nodes run a copy of a specific pod.
   - when nodes are added to the cluster, daemon set adds or removes the required pods.        
5) Jobs - Jobs are the constructs that run the container once  
 
note:
ClusterIP – The default value. The service is only accessible from within the Kubernetes cluster – you can’t make requests to your Pods from outside the cluster! internal IP
 
NodePort – This makes the service accessible on a static port on each Node in the cluster. This means that the service can handle requests that originate from outside the cluster. External Ip
 
Config maps - helps pass values dynamically
 
pod shares IP address, volumes etc.
 
delete the pods to restart it again
 
To copy files from pods
kubectl cp /shared/logs/heimdallbox-heimdallbox-0/a.txt heimdallbox-heimdallbox-0:~/a.txt -n inteksheimdall
 
To scale statefulsets
kubectl scale statefulsets arangodb-arangodb --replicas=0 -n coppesteksarangodb
 
To delete evicted pods
kubectl get pod  | grep Evicted | awk '{print $1}' | xargs kubectl delete pod -n namespace
 
COMMANDS:
kubectl get pods redis-bootstrap -n redis-cluster -o jsonpath='{.spec.containers[*].name}*  #lists all the containers in a multicontainer POD
kubectl exec -it podname -c containername bash or sh
kubectl -n policy-demo delete networkpolicy access-nginx
kubectl get namespace
kubectl get pods -n namespace_name
kubectl get nodes
kubectl create -f helloworld.yaml
kubectl get all
kubectl expose deployment helloworld --type=NodePort
minikube service helloworld
--- to add multiple files content into one file.
kubectl get pods --show-labels
kubectl label pod/podname label_key=label_value --overwrite  (to overwrite an existing label for a pod)
kubectl label pod/pod_name label_key-  (to delete the label)
kubectl get pods --selector label_key=label_value,label_key2=label_value2(, acts like and != works like not)
kubectl get pods -l "label_key in (label_value1,lbel_value2)"   => in searches in set given, can use notin operator
kubectl delete pods -l label_key=label_value  (-l<=>--selector)
readiness(booting up time) and liveness(health check) gets restarted many times and finally crashloopbackoff status.
kubectl create -f helloworld.yaml  --record
kubectl set image deployment/navbar helloworld=kar/image_name:tag
kubectl rollout history deploymant/name
kubectl rollout undo deploynent/name
kubectl rollout undo deploynent/name --to-revision='number'
kubectl logs pod_name
kubectl exec -it podname /bin/bash  (after exceuting this cmd we are inside the pod)
kubectl exec -it podname -c containername /bin/bash (if there are many containers running in sigle pod)
 
minikube addons list => lists all the addons that can be installed
minikube addons enable dashboard => enables the dashboard
minikube addons enable metrics-server
minikube addons list
minkube dashboard
 
kubectl create configmap logger --from-literal=log_level=debug  => in yaml file if the env variable is made to read form config files then the config file can be dynamically changed. so that deployment is not created again.
kubectl create secret generic keyname --from-literal=api_key=12334
kubectl get secrets
 
Jobs are the constructs that run the container once
creation is same as deploymnet
 
cron job is kind of job that runs periodically
kubectl get cronjobs
kubectl edit cronjobs/name   => change suspend to true
 
deamon sets: makes sure that all nodes run a copy of a specific  pod
Kops is a very popular way to deploy kubernetes to amazon and looks similar to the way kubectl operates.
 
