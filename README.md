<div align="center">

# 📡 RTT Monitor

### Distributed Network Monitoring Platform

*Real-time latency tracking, ping diagnostics, and DNS resolution checks across distributed anchor nodes — built for engineers who need to catch network failures before users do.*

<br/>

![Python](https://img.shields.io/badge/Python-3.7+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/Django_REST_Framework-FF1709?style=for-the-badge&logo=django&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?style=for-the-badge&logo=celery&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)

![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![Forked](https://img.shields.io/badge/Forked_from-Swarup2908-blue?style=for-the-badge&logo=github)

</div>

---

## 🧭 Overview

**RTT Monitor** is a Django-powered platform that continuously tracks network health from multiple geographic locations using distributed anchor nodes. It runs asynchronous background workers via **Celery + Redis** to perform non-stop ping, DNS, and latency checks — without ever blocking the main application.

Integrated with the **[services.aiori.in](https://services.aiori.in/)** API, it fetches live anchor nodes and domain data to run real-world network diagnostics at scale.

---

## 🧠 What It Monitors

| Check | What's Tracked |
|---|---|
| 📶 **RTT Latency** | Min / Max / Average round-trip time |
| 📦 **Ping** | Packet transmission, packet loss, RTT stats |
| 🌐 **DNS Resolution** | Domain resolution from distributed anchors |
| 🔌 **API Health** | Endpoint availability and response times |
| 🗺️ **Anchor Nodes** | Distributed geographic network testing points |

---

## ⚙️ Tech Stack

**Backend**
- [Django](https://www.djangoproject.com/) — web framework and data layer
- [Django REST Framework](https://www.django-rest-framework.org/) — API endpoints
- [Celery](https://docs.celeryq.dev/) — async task processing
- [Celery Beat](https://docs.celeryq.dev/en/stable/userguide/periodic-tasks.html) — periodic task scheduler
- [Redis](https://redis.io/) — message broker and result backend

**Networking**
- Ping-based latency measurement
- DNS query monitoring
- Distributed anchor-based network testing

---

## 🏗️ Architecture

```
Django Web App
      │
      ▼
Celery Task Queue
      │
      ▼
Redis Message Broker
      │
      ▼
Background Workers
      │
      ▼
External API (services.aiori.in)
      │
      ▼
Network Data Collection
  (Ping / DNS / RTT)
```

The architecture is fully non-blocking — monitoring tasks run in parallel workers, keeping the web layer responsive while continuous checks run in the background.

---

## 🔍 Core Features

### 1. RTT Latency Monitoring
Calculates round-trip time between anchor nodes and target domains.
Tracks **min**, **max**, and **average RTT** to surface latency spikes early.

### 2. Ping Monitoring
Executes real ping commands from anchor nodes and records:
- Packet transmission counts
- Packet loss percentages
- RTT statistics per hop

### 3. DNS Query Monitoring
Validates domain name resolution from distributed anchors to detect:
- DNS propagation failures
- Regional resolution inconsistencies

### 4. Anchor-Based Distributed Testing
Each anchor node independently runs ping, DNS, and command checks — enabling multi-region performance visibility from a single dashboard.

### 5. Async Task Processing
All monitoring tasks are offloaded to **Celery workers** scheduled by **Celery Beat**, enabling:
- Continuous, parallel monitoring
- Scalable endpoint coverage
- Zero impact on web app performance

---

## 📊 Monitoring Workflow

```
1. Fetch domain + anchor data from API
        ↓
2. Celery Beat triggers scheduled tasks
        ↓
3. Workers execute ping + DNS queries
        ↓
4. RTT values are calculated
        ↓
5. Results stored and analyzed
        ↓
6. Network health insights surfaced
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.7+
- Redis server running locally

### Installation

```bash
# Clone the repository
git clone https://github.com/vishalbunn/Rtt_ping.git
cd Rtt_ping

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows

# Install dependencies
pip install -r requirements.txt
```

### Running the Platform

```bash
# Start Redis
redis-server

# Run Django server
python manage.py runserver

# Start Celery worker
celery -A rtt_monitor worker --loglevel=info

# Start Celery Beat scheduler
celery -A rtt_monitor beat --loglevel=info
```

---

## 🌐 External API Integration

The platform integrates with **[services.aiori.in](https://services.aiori.in/)** to:

- Fetch available anchor nodes
- Retrieve monitored domain lists
- Collect distributed command results
- Pull real-time network diagnostics

---

## ✅ Key Benefits

- ⚡ **Real-time** network performance monitoring
- 🗺️ **Distributed** testing from multiple geographic anchors
- 🔄 **Scalable** async processing via Celery workers
- 🔌 **API health** tracking with response time analysis
- 🚨 **Early detection** of latency spikes and endpoint failures

---

## 🤝 Contributing

```bash
# Fork the repo, then:
git checkout -b feature/your-feature
git commit -m "Add your feature"
git push origin feature/your-feature
# Open a Pull Request
```

---

## 📄 License

This project is licensed under the **MIT License**.

---

<div align="center">

*Forked from [Swarup2908/Rtt_monitor](https://github.com/Swarup2908/Rtt_monitor) · Enhanced by [vishalbunn](https://github.com/vishalbunn)*

</div>
