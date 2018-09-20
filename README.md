# telegraf-tick-k8s  
  
This repo contains relevant information for deploying tick stack on kubernetes with:    
* influxdb  
* kapacitor  
* telegraf  
* chronograf  
  
This deployment is simple and just meant to get the tick stack up and running quickly with a LB front-end  
All the persistent volumes use local storage and require about 30GB to work correctly.  
  
It's based on this deployment:  
https://vinta.ws/code/deploy-tick-stack-on-kubernetes-telegraf-influxdb-chronograf-and-kapacitor.html  
  
Deploy in the following order:  
  
kubectl create -f all the pv files  
kubectl create -f all the service files  
kubectl create -f influx-statefulset.yaml  
kubectl create -f telegraf-statefulset.yaml  
kubectl create -f kapacitor-statefulset.yaml  
kubectl create -f chrono-statefulset.yaml  
  
connect to influxdb:  
kubectl exec -i -t influxdb-0 --namespace tick -- influx  
  
You will need to update MASTERIPADDRESS for the LoadBalancer in telegraf-service.yaml prior to use.  
