#PASSOS E COMANDOS

-Fork e clone do repositório

-Criar Cluster:
k3d cluster create devops4devs -p "8080:30000@loadbalancer"


-Criar imagem da aplicação:
Docker build -t lanvsc/review-filmes:v1 -f src/Review-Filmes.Web/Dockerfile src/

-Enviar imagem para Docker Hub
docker push lanvsc/review-filmes:v1

https://hub.docker.com/repository/docker/lanvsc/review-filmes

-Deploy
kubectl apply -f k8s/deployment.yaml
