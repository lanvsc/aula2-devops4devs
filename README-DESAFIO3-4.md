### **DESAFIO AULAS 3-4**
**- Configurar/autenticar AWS CLI:**
```
aws configure
```
**- Criar Stack Cloudformation-AWS:**
Usar template:
```
https://s3.us-west-2.amazonaws.com/amazon-eks/cloudformation/2020-10-29/amazon-eks-vpc-private-subnets.yaml
```
**- Criar EKS:**
```
k3d cluster create devops4devs -p "8080:30000@loadbalancer"
```
**- Criar Nodes EKS:**
```
docker push lanvsc/review-filmes:v1
```
>Link
https://hub.docker.com/repository/docker/lanvsc/review-filmes

**-Deploy**
Alterar deployment.yaml da aula 2, alterando linhas: 
>82 -#nodePort: 30000
>83-type: LoadBalancer
``` 
kubectl apply -f k8s/deployment.yaml
