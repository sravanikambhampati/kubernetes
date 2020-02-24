# k8s deployment nginx
#Create an nginx deployment, and verify it was successful.

kubectl run nginx --image=nginx

#Create a service, and verify the service was successful.
kubectl expose deployment nginx --port 80 --type NodePort

#Create a pod that will allow you to query DNS, and verify it’s been created.

kubectl apply -f busybox.yaml

#Perform a DNS query to the service.

kubectl exec busybox -- nslookup nginx

#Recoed the dns name <service-name>.default.svc.cluster.local

#Taint one of the worker nodes to repel work.
kubectl taint node <node_name> node-type=prod:NoSchedule

#Schedule a pod to the dev environment.

kubectl apply -f dev-busybox.yaml

#Allow a pod to be scheduled to the prod environment.

kubectl apply -f prod-busybox.yaml

# delete the taint from node
 kubectl taint node kind-worker node-type=:NoSchedule-
