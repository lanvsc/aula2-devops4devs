### **DESAFIO AULAS 3-4 - AWS e GitHub Actions.**

## **Aula3**
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
>- 82 #nodePort: 30000
>- 83 -type: LoadBalancer
``` 
kubectl apply -f k8s/deployment.yaml
``` 

## **Aula4**

**Pipeline CI/CD com GitHub Actions**

-   Configuração da Pipeline:
-   Crie uma pipeline CI/CD utilizando GitHub Actions que automatize o processo de build, test e deploy da aplicação no EKS.
-   Configure o pipeline para executar testes automatizados antes do deploy.
``` 
name: CI-CD
on: 
  push:
    branches: ["main"]
  workflow_dispatch:

jobs:
  CI:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout do código fonte
        uses: actions/checkout@v4.1.7

      - name: Login no Docker Hub
        uses: docker/login-action@v3.2.0
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      - name: Construir imagem Docker e envio para Docker Hub
        uses: docker/build-push-action@v6.3.0
        with:
          context: ./src
          push: true
          file: ./src/Review-Filmes.Web/Dockerfile
          tags: |
            lanvsc/review-filmes:v${{github.run_number}}
            lanvsc/review-filmes:latest

``` 

**-  Automação do Deploy:**
-   Garanta que o deploy na AWS seja automático após a aprovação das mudanças no repositório.
-   Implemente notificações e monitoramento para garantir a visibilidade do processo de deploy.
``` 
CD:
    runs-on: ubuntu-latest
    needs: [CI]
    steps:
      - name: Checkout do código fonte
        uses: actions/checkout@v4.1.7
      
      - name: Configuração do AWS Credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1

      - name: Configuração do Kubeconfig
        run: aws eks update-kubeconfig --name eks-aula
      
      - name: Deploy da aplicação
        uses: Azure/k8s-deploy@v5.0.0
        with:
          manifests: |
              ./k8s/deployment.yaml
          images: |
            lanvsc/review-filmes:v${{github.run_number}}
``` 

> Verificar versões das imagens no Docker Hub:
https://hub.docker.com/repository/docker/lanvsc/review-filmes/general
