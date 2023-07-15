### Demo deploy web static ###
mkdir -p /Users/Acer/k8s_training/disk/www/disk/www

### Create index file ###
/home/k8s/training/disk/www/index.html 

### Create www-static.yaml 
www-static.yml 

### Name space ###
### Deploy Nginx ###
### SVC Nginx ###

kubectl apply -f www-static.yaml

### Get from "WWW" name space 
kubectl get -n www po
kubectl get -n www svc
kubectl get -n www ing

### Add DNS Again ###
10.6.98.94  www.k8s.com

### Visit Web
https://www.k8s.com/

### Destroy ###
kubectl delete -f www-static.yaml
