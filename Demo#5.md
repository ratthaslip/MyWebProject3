### Ingress file
web-ing.yaml 

### Deploy service
kubectl apply -f web-ing.yaml

###  Get ingress
kubectl get ing

### wait until ip address showing about 1 minute ###

### Access by ip error because ingress access only fqdn ### 

### Map dns name to service IP ### 
10.6.98.94  web-traning.k8s.com

### Access ingress url ###
http://web-traning.k8s.com

### Enable TLS Certificate ingress ###
openssl req -x509 \
            -sha256 -days 356 \
            -nodes \
            -newkey rsa:2048 \
            -subj "/CN=*.k8s.com/C=TH/L=Bangkok" \
            -keyout cert.key -out cert.crt

### Create Secret
kubectl -n kube-system create secret tls --cert cert.crt --key cert.key ingress-nginx-tls --dry-run -o yaml | kubectl apply -f -

### Edir ingress controller
kubectl edit -n ingress-nginx deployment ingress-nginx-controller

### Create config TLS web ###
tls-web-ing.yaml 

### Deploy Ingress
kubectl apply -f tls-web-ing.yaml

### Get Ingress
kubectl get ing

### Add DNS Again ###
10.6.98.94  webs-traning.k8s.com

### Goto web
https://webs-traning.k8s.com/

### delete deployment ###
kubectl delete -f tls-web-ing.yaml 
kubectl delete svc nginx-deployment
kubectl delete deployment nginx-deployment
kubectl delete ing web-ingress
