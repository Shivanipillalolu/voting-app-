# K8s Kind Voting App
A hands-on guide to deploying a microservices-based voting application on a Kubernetes cluster using Kind on an AWS EC2 instance. This project demonstrates the setup of Argo CD for GitOps-style continuous delivery and integrates observability tools for monitoring.

🚀 Overview
This guide walks you through:

Launching an AWS EC2 instance

Installing Docker and Kind

Creating a local Kubernetes cluster using Kind

Installing and configuring kubectl

Setting up the Kubernetes Dashboard

Installing and managing deployments with Argo CD

Connecting and managing the Kubernetes cluster using Argo CD

🧠 Architecture


📊 Observability
Integrated dashboards for metrics and monitoring:

Grafana



Prometheus



🧩 Application Stack
This project includes the following components:

🔵 Frontend App: A Python web application (/vote) for users to cast votes between two choices.

🧠 Redis: Stores incoming votes in real-time — Redis Docker Hub

⚙️ Worker: A .NET background processor (/worker) that reads votes from Redis and writes them to PostgreSQL.

🐘 Postgres: A relational database for storing results — Postgres Docker Hub

🟢 Result App: A Node.js web app (/result) displaying voting results in real-time.

🚀 Deployment Steps
Follow the steps below to set up and deploy the voting app:

1. Launch EC2 Instance
Launch an EC2 instance (Ubuntu preferred) with at least t2.medium and port 30000-32767 open in the security group for NodePort access.

2. Install Docker & Kind
bash
Copy
Edit
sudo apt update && sudo apt install docker.io -y
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
3. Install kubectl
bash
Copy
Edit
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
4. Create Kind Cluster
bash
Copy
Edit
kind create cluster --name voting-cluster
5. Set up Kubernetes Dashboard (Optional)
bash
Copy
Edit
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
6. Install Argo CD
bash
Copy
Edit
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
7. Access Argo CD UI
bash
Copy
Edit
kubectl port-forward svc/argocd-server -n argocd 8080:443
Visit https://localhost:8080 to open Argo CD UI.

8. Deploy the App via Argo CD
Create an Argo CD Application pointing to your GitHub repo.

Sync the app from the Argo UI to deploy all services.
