### ทำการสร้างไฟล์ deployment.yaml ขึ้นมา (ดาวน์โหลดไฟล์จาก link) 
https://gist.githubusercontent.com/worldkk1/ce890dfdf575861dd8d889851fb58b61/raw/ddd91428a052726c99a196a07ca6ee0a17cc0f13/deployment.yaml

### Deployment
kubectl apply -f deployment.yaml

### เรียกดูการ deploy ด้วยคำสั่ง
kubectl get deployment

### เรียกดู pod
kubectl get pod

### เรียกดู Service
kubectl get svc

### Expose ออกข้างนอก ด้วย NodePort service
kubectl expose deployment hello-minikube  --type=NodePort --port=8080

### Get Service
kubectl get svc
