# blue-green-deployment-on-k8s

This is code that tried blue-green deployment on k8s. it ran on masOS Sierra with minikube.

usage 

1. install minikube.

2. create deployment and service

```bash
kubectl apply -f deployment-b.yaml -f deployment-g.yaml -f service-bg.yaml
```

3. access to service port

```bash
curl 192.168.99.100:8080

> Hello Kubernetes bootcamp! | Running on: http-deploy-b-2645909527-0lh1f | v=1
```

4. edit service.yaml and apply service.

```bash
sed -i -e "s/blue/green/" service-bg.yaml 

kubectl apply -f service-bg.yaml
```

5. check green has been deployed

```bash
curl 192.168.99.100:8080

> Hello Kubernetes bootcamp! | Running on: http-deploy-g-3904659589-s2kz2 | v=1
```
