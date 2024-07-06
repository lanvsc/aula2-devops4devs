### **AULA 2**

### Informações do desafio
Você foi contratado como engenheiro DevOps na empresa "FilmReviews Inc." e vai participar do desenvolvimento e entrega do principal produto da empresa, o "Review de Filmes".  
Esse projeto é uma aplicação desenvolvida em C# e vocês estão em processo de prova de conceito, onde deve ser testado o deploy da aplicação em um ambiente Kubernetes.  
  
Seu desafio é fazer um fork do projeto original  [**(https://github.com/KubeDev/imersao-devops-cloud-02**](https://github.com/KubeDev/imersao-devops-cloud-02)  e fazer esse deploy em um ambiente local para fins de testes utilizando o K3D.  
  
### **Requisitos**

**1.Criação dos Elementos:**
-   Crie os manifests necessários para o deploy da aplicação no Kubernetes local, incluindo Deployment e Service.
-   Utilize o K3D para criar um cluster Kubernetes local.
  
**2.Eficiência do Deploy e Comportamento:**
-   Garanta que o deploy da aplicação seja eficiente e que a aplicação esteja funcionando corretamente.
-   Implemente a escalabilidade e resiliência da aplicação através do Kubernetes.
-   Teste a capacidade de fazer rollbacks e atualizações sem downtime.
**3. Documentação do Projeto:**
-   Documente todo o processo de configuração e deploy no arquivo `README-DESAFIO.md` do repositório.
-   Inclua os comandos utilizados e screenshots dos resultados.

### **Instruções**
**Faça um fork do repositório original:**
-   Clone o repositório original:  [**(https://github.com/KubeDev/imersao-devops-cloud-02**](https://github.com/KubeDev/imersao-devops-cloud-02)
-   Crie um fork para o seu GitHub.


### **AULA 3-4**

### Informações do desafio Aulas 3 e 4

Depois de apresentar a criação de um ambiente local utilizando K3D, agora, a "FilmReviews Inc." está pronta para levar o projeto "Review de Filmes" para o próximo nível, implementando em um ambiente na AWS utilizando o Amazon EKS (Elastic Kubernetes Service).

Seu novo desafio é configurar e gerenciar a aplicação no ambiente AWS, garantindo a escalabilidade e a resiliência necessárias para um ambiente de produção. Além disso, você deve automatizar o processo de deploy utilizando GitHub Actions para garantir que as entregas contínuas sejam ágeis e seguras.  

Você vai utilizar o mesmo repositório do desafio anterior.

### Objetivos

**1. Configuração do Ambiente na AWS**

**Configuração do EKS:**
- Crie um cluster EKS na AWS utilizando o AWS Management Console, AWS CLI ou Terraform.
-  Configure os nós de trabalho e garanta que o cluster esteja funcionando corretamente.

**Deploy da Aplicação:**
- Crie os manifests necessários para o deploy da aplicação no EKS, incluindo Deployment, Service, Ingress e ConfigMaps.
- Implemente as práticas recomendadas de segurança e gerenciamento de recursos.

**2. Pipeline CI/CD com GitHub Actions**

   **Configuração da Pipeline:**
- Crie uma pipeline CI/CD utilizando GitHub Actions que automatize o processo de build, test e deploy da aplicação no EKS.
- Configure o pipeline para executar testes automatizados antes do deploy.

 **Automação do Deploy: **
- Garanta que o deploy na AWS seja automático após a aprovação das mudanças no repositório.
- Implemente notificações e monitoramento para garantir a visibilidade do processo de deploy.

 **3. Documentação e Demonstração **
- Documentação do Projeto:
- Documente todo o processo de configuração e deploy no arquivo README-DESAFIO.md do repositório.

# Aula 05 

### Comando para obter a senha do Grafana
```
kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode
