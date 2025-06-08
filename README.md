
# CloudShop Observability Stack

CloudShop Observability Stack is a complete end-to-end monitoring and alerting system for a microservices-based e-commerce application deployed on Kubernetes. It integrates **Prometheus**, **Grafana**, and **Alertmanager** to provide deep insights into both **infrastructure-level** and **application-level** performance metrics.

---

## 🔧 Tech Stack

- **Cloud Platform**: Azure Kubernetes Service (AKS)
- **Microservices**: Node.js, Express.js
- **Monitoring**: Prometheus, Grafana, Alertmanager
- **Metrics Collection**: prom-client (Node.js)
- **Deployment**: Docker, Kubernetes
- **Dashboards**: Custom Grafana JSON import

---

## 📦 Features

- 📈 Application metrics (HTTP requests, errors, latency, heap usage)
- 🖥 Infrastructure metrics (CPU, memory, disk, event loop lag)
- 🚦 Live dashboards in Grafana
- 📡 Prometheus ServiceMonitors for auto-discovery
- 🔔 Ready for Alertmanager integration (optional)
- ⚙️ Cleanly separated Kubernetes manifests
- 🐳 Fully containerized microservices

---

## 📁 Project Structure

```bash
cloudshop-monitoring/
├── manifests/
│   ├── user-service-servicemonitor.yaml
│   ├── product-service-servicemonitor.yaml
│   ├── order-service-servicemonitor.yaml
│   └── prometheus-rules.yaml
├── grafana/
│   └── cloudshop-app-monitoring-dashboard.json
└── README.md
```

---

## 🚀 How to Run

### 1. Deploy the Prometheus stack:

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

helm install prometheus prometheus-community/kube-prometheus-stack \
  --namespace monitoring --create-namespace
```

### 2. Apply ServiceMonitors:

```bash
kubectl apply -f manifests/
```

### 3. Access Prometheus & Grafana

- **Prometheus**: http://localhost:9090
- **Grafana**: http://localhost:3000 (admin / prom-operator)

---

## 📊 Grafana Dashboard

Import the JSON from:
```
grafana/cloudshop-app-monitoring-dashboard.json
```

Includes:
- Total HTTP Requests
- Error Rate (5xx)
- Event Loop Lag
- Heap Memory
- CPU Usage
- Active Handles

---

## 🧠 What You'll Learn

- How to expose custom app metrics with `prom-client`
- How to scrape metrics using Prometheus in Kubernetes
- How to build production-grade Grafana dashboards
- How to observe and analyze system behavior in real time

---

## 🙌 Author

Built by **Shreyash Patil** as a showcase project for SRE/DevOps interviews.
