### การ Deploy Java Spring-boot ไปยัง Kubernetes
## 1. สร้าง Secret สำหรับเก็บ username และ password ของ Docker Registry
kubectl create secret docker-registry my-docker-registry \
--docker-server=http://registry.mywebsite.com \
--docker-username=my_docker_account \
--docker-password=WGTSU5V22cEYW9f \
--docker-email=myemail@gmail.com

### 2. สร้าง ConfigMap สำหรับเก็บ Configuration ของ Application
### 2.1 สร้าง .env file (oauth.env)
JAVA_OPTS=-Djava.security.egd=file:/dev/./urandom -Dserver.port=8080 -Dspring.redis.url=redis://.....

### 2.2 Run Command สำหรับสร้าง ConfigMap จาก .env file
kubectl create configmap oauth-config --from-env-file=/deploy/oauth.env

### 2.3 ทดสอบแสดง ConfigMap ในรูปแบบ .yaml
kubectl get configmap oauth-config -o yaml


#### 3. เขียน File .yml เพื่อเตรียม Deploy
### 3.1 เขียน Deployment file 
deployment4.yml

### 3.2 เขียน Service file 
service4.yml

### 4. Deploy
kubectl apply -f deployment.yml
kubectl apply -f service.yml

### 5. ตรวจสอบสถานะการ Deploy
kubectl get pods
kubectl get services

### 6. ทดสอบเข้าใช้งาน Application
http://<MASTER_NODE_IP>:30001
Port 30001 มาจากที่เรากำหนดไว้ใน service.yml
