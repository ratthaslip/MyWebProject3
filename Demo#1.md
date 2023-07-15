### Get Kube version ###
kubectl version -o yaml

### Get pod ###
kubectl get --all-namespaces po

### Get service ###
kubectl get --all-namespaces svc

### Deployment ### 
kubectl create deployment nginx-deployment   --image quay.io/redhattraining/nginx:1.21 --port 80

###  Expose port ###
kubectl expose deployment nginx-deployment   --type LoadBalancer --port 80 --target-port 80

### Get Deployment ####
kubectl get deployment

## Get pod ####
kubectl get po

### Get Service ####
kubectl get svc 

### Delete ###########
### Delete Service ###
kubectl delete svc nginx-deployment
### Delete Deployment ###
kubectl delete deployment nginx-deployment