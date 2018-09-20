# development/k8s-tick  
This repo is for deploying:  
* influxdb  
* kapacitor  
* telegraf  
* chronograf  
  
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
