# k8s-minecraft-server

Turning on the minecraft-server:
- kubectl apply -f minecraft-service.yaml
- kubectl apply -f volume-storage.yaml
- kubectl apply -f minecraft-server-deployment.yaml

Server backup to S3
- Fill all missing data -> S3 URL, region, AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY
- kubectl scale --replicas=0 deployment/minecraft-server-deployment
- kubectl apply -f volume-storage-backup.yaml
- kubectl apply -f backup-to-pvc.yaml
- kubectl apply -f backup-to-s3.yaml
- kubectl scale --replicas=1 deployment/minecraft-server-deployment