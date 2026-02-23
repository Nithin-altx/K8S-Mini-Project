# 🚀 Kubernetes Mini Project – Docker + Minikube Deployment

A hands-on **Kubernetes deployment project** demonstrating containerization using Docker and orchestration using Minikube.
This project covers complete workflow from building an application → containerizing → deploying to Kubernetes → debugging → load testing.

---

## 📌 Project Overview

This project demonstrates:

* ✅ Docker image creation
* ✅ Kubernetes Deployment configuration
* ✅ Minikube cluster setup
* ✅ Multi-node configuration
* ✅ Service exposure
* ✅ Debugging & logging
* ✅ Load testing using Postman

---

# 🏗️ Step-by-Step Execution Guide

---

## 1️⃣ Build the Application

* Create or use an existing application
* Test locally to ensure it runs correctly

---

## 2️⃣ 🐳 Dockerize the Application

### Create Dockerfile

Place a `Dockerfile` in your project root directory.

### Build Docker Image

```bash
docker build -t kubernetes-test-app:latest .
```

### Verify Image

```bash
docker images
```

### Test Locally

```bash
docker run -p 5000:5000 kubernetes-test-app:latest
```

---

## 3️⃣ ☸️ Create Kubernetes Deployment

Create a file named:

```
deployment.yaml
```

Define your Kubernetes deployment configuration inside this file.

---

## 4️⃣ ⚙️ Install & Start Minikube

### Install Minikube

* Download `.exe` from official site
* Run via PowerShell (Admin mode)
* Restart terminal

### Start Cluster

```bash
minikube start
```

OR

```bash
minikube start --embed-certs
```

---

## 5️⃣ 🛠️ Troubleshooting Minikube

### Common Error

Failing to connect to:

```
https://registry.k8s.io/
```

---

### If Using Proxy

```bash
minikube start --docker-env HTTP_PROXY=http://your-proxy:port \
--docker-env HTTPS_PROXY=https://your-proxy:port
```

---

### If NOT Using Proxy

Unset environment variables:

```bash
unset HTTP_PROXY
unset HTTPS_PROXY
unset NO_PROXY
```

---

### Test Connectivity

```bash
nslookup registry.k8s.io
```

---

### Clean & Restart

```bash
minikube stop
minikube delete --all
```

---

## 6️⃣ Verify Cluster Status

```bash
minikube status
```

```bash
kubectl get all -A
kubectl get pods -A
kubectl get nodes -A
```

---

## 7️⃣ Add Multiple Nodes

```bash
minikube start --nodes=2
```

OR

```bash
minikube start --nodes=2 --embed-certs
```

---

## 8️⃣ Load Docker Image into Minikube

### Verify Images

```bash
docker images
minikube image list
```

### Load Image

```bash
minikube image load kubernetes-test-app:latest
```

---

## 9️⃣ Deploy Application

```bash
kubectl apply -f deployment.yaml
```

### Delete Deployment (If Required)

```bash
kubectl delete deployment kubernetes-test-app
```

---

## 🔟 Test the Application

### Check Pods & Nodes

```bash
kubectl get pods -A
kubectl get nodes -A
```

### Delete Specific Pod

```bash
kubectl delete pod <pod-name>
```

### Access Service

```bash
minikube service kubernetes-test-app
```

### Open Dashboard

```bash
minikube dashboard
```

---

## 🐞 Debugging & Logs

### View Pod Logs

```bash
kubectl logs -f <pod-id>
```

### Check Endpoints & Services

```bash
kubectl get endpoints
kubectl get service
```

---

## 📊 Load Testing with Postman

* Go to **Collection → Runs → Performance**
* Run performance test
* Example configuration:

  * 👥 10 users
  * ⏱️ 1 minute duration

---

## 🛑 Stop Minikube

```bash
minikube stop
```

---

## 🚨 Fix ImagePullBackOff Error

If you face:

```
ImagePullBackOff
```

### Tag Image

```bash
docker tag kubernetes-test-app:latest <your-dockerhub-username>/kubernetes-test-app:latest
```

### Push to Docker Hub

```bash
docker push <your-dockerhub-username>/kubernetes-test-app:latest
```

Update deployment YAML image name accordingly.

---

# 🧠 Key Concepts Covered

* Docker Containerization
* Kubernetes Deployments
* Pods & Services
* Cluster Management
* Multi-node Setup
* Networking & Proxy Handling
* Logging & Debugging
* Load Testing

---

# 📂 Tech Stack

| Technology | Usage                    |
| ---------- | ------------------------ |
| Docker     | Containerization         |
| Kubernetes | Container Orchestration  |
| Minikube   | Local Kubernetes Cluster |
| Kubectl    | Cluster Management       |
| Postman    | API Load Testing         |


