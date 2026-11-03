# EX.CO Practice — Flask on Kubernetes

Small Flask service containerized with Docker, deployed on a local kind cluster.

## Run locally
docker build -t exco-app:v1 .
docker run --rm -p 8000:8000 exco-app:v1

## Deploy on kind
kind create cluster --name exco
kind load docker-image exco-app:v1 --name exco
kubectl apply -f k8s/
kubectl port-forward service/exco-app 8080:80
curl localhost:8080/health
