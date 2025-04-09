Here’s a clean and professional rewrite of your `README.md` content with your identity and project clarity in focus:

---

# K8s Kind Voting App

A hands-on guide to deploying a microservices-based voting application on a Kubernetes cluster using Kind on an AWS EC2 instance. This project demonstrates the setup of Argo CD for GitOps-style continuous delivery and integrates observability tools for monitoring.

---

## 🚀 Overview

This guide walks you through:
- Launching an AWS EC2 instance
- Installing Docker and Kind
- Creating a local Kubernetes cluster using Kind
- Installing and configuring `kubectl`
- Setting up the Kubernetes Dashboard
- Installing and managing deployments with Argo CD
- Connecting and managing the Kubernetes cluster using Argo CD

---

## 🧠 Architecture

![Architecture diagram](k8s-kind-voting-app.png)

---

## 📊 Observability

- Integrated dashboards for metrics and monitoring:
  - **Grafana**
  
    ![Grafana diagram](grafana.png)

  - **Prometheus**

    ![Prometheus diagram](prometheus.png)

---

## 🧩 Application Stack

This project includes the following components:

- 🔵 **Frontend App**: A Python web application ([/vote](/vote)) for users to cast votes between two choices.
- 🧠 **Redis**: Stores incoming votes in real-time — [Redis Docker Hub](https://hub.docker.com/_/redis/)
- ⚙️ **Worker**: A .NET background processor ([/worker](/worker)) that reads votes from Redis and writes them to PostgreSQL.
- 🐘 **Postgres**: A relational database for storing results — [Postgres Docker Hub](https://hub.docker.com/_/postgres/)
- 🟢 **Result App**: A Node.js web app ([/result](/result)) displaying voting results in real-time.

---

Let me know if you'd like me to:
- Add a **"Getting Started"** or **"Deployment Steps"** section.
- Include **your name or GitHub profile** in the footer.
- Help replace the images or generate a custom architecture diagram for your version.
