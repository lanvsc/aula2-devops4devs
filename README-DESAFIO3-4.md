### **DESAFIO AULAS 3-4 - AWS e GitHub Actions.**

**- Aula3:**
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
Painel AWS
```
**- Criar Nodes EKS:**
```
Painel AWS
Seleções:
Instância on demand
T3.medium
Desired size:3
Minimum size:2
Maximum size:4
```
**-Deploy**
Alterar deployment.yaml da aula 2, alterando linhas: 
```
>- 82 #nodePort: 30000
>- 83 -type: LoadBalancer
``` 
kubectl apply -f k8s/deployment.yaml

**- Aula4:**

**- Criar pipeline com GitHub Actions:**
```
**- Configurar pipeline para execução automática:**

```
> Verificar versões das imagens no Docker Hub:
https://hub.docker.com/repository/docker/lanvsc/review-filmes/general
