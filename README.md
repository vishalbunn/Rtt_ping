🚀 RTT Monitor – Distributed Network Monitoring Platform
📌 Overview

RTT Monitor is a Django-based network monitoring platform designed to track and analyze Round Trip Time (RTT) and network diagnostics from distributed anchor nodes.

The system performs real-time monitoring of network endpoints, collecting data from APIs and executing ping and DNS queries to evaluate network performance.

It uses Celery and Redis to run background monitoring tasks asynchronously, enabling scalable and continuous monitoring without blocking the application.

The platform integrates with external APIs from:

https://services.aiori.in/

to fetch anchor data, domains, and command results.

🧠 What This Application Monitors

The platform continuously monitors:

• RTT latency values
• Ping responses from distributed anchors
• DNS query resolution
• API response health
• Network endpoint availability

This helps detect network instability, latency spikes, or endpoint failures in real time.

⚙️ Tech Stack

Backend

Django

Django REST Framework

Celery

Celery Beat

Redis

Networking

Ping monitoring

DNS query monitoring

Anchor-based distributed checks

Infrastructure

Python

REST APIs

Async background workers

🏗 System Architecture
Django Web App
      │
      │
      ▼
Celery Task Queue
      │
      │
      ▼
Redis Message Broker
      │
      │
      ▼
Background Workers
      │
      │
      ▼
External API (services.aiori.in)
      │
      │
      ▼
Network Data Collection
(Ping / DNS / RTT)

The architecture ensures high scalability and non-blocking monitoring operations.

🔍 Core Functionalities
1️⃣ API Monitoring

The system continuously fetches data from external APIs to monitor:

• Domain endpoints
• Anchor nodes
• Command execution results

API health and response times are tracked.

2️⃣ RTT Monitoring

RTT (Round Trip Time) is calculated to determine the latency between anchor nodes and target domains.

Metrics collected:

• Minimum RTT
• Maximum RTT
• Average RTT

These metrics help identify network latency issues.

3️⃣ Ping Monitoring

The system runs ping commands to evaluate network connectivity.

Data collected includes:

• Packet transmission
• Packet loss
• RTT statistics

4️⃣ DNS Query Monitoring

DNS resolution checks ensure that domain names resolve correctly from different network anchors.

This helps detect:

• DNS propagation issues
• DNS resolution failures

5️⃣ Anchor-Based Network Testing

The monitoring system uses distributed anchors to run network tests.

Each anchor can perform:

• Ping requests
• DNS queries
• Command executions

This allows testing network performance from multiple geographic locations.

⚡ Asynchronous Task Processing

Monitoring tasks run in the background using Celery workers, which allows:

• Continuous monitoring
• Parallel network checks
• Scalable endpoint monitoring

Celery Beat schedules periodic tasks.

📊 Example Monitoring Workflow

1️⃣ System fetches domain and anchor data from API

2️⃣ Celery worker triggers monitoring tasks

3️⃣ Ping and DNS queries are executed

4️⃣ RTT values are calculated

5️⃣ Results are stored and analyzed

6️⃣ Network health insights are generated

📦 Requirements

Python 3.7+

Django

Celery

Redis

⚙️ Installation
1️⃣ Clone Repository
git clone https://github.com/Swarup2908/Rtt_monitor.git
cd Rtt_monitor
2️⃣ Create Virtual Environment
python -m venv venv

Activate environment

Windows

venv\Scripts\activate

Linux / Mac

source venv/bin/activate
3️⃣ Install Dependencies
pip install -r requirements.txt
4️⃣ Start Redis
redis-server
5️⃣ Run Django Server
python manage.py runserver
6️⃣ Start Celery Worker
celery -A rtt_monitor worker --loglevel=info
7️⃣ Start Celery Beat (Scheduler)
celery -A rtt_monitor beat --loglevel=info
🌐 External API Integration

The system integrates with:

https://services.aiori.in/

Used for:

• Fetching anchor nodes
• Retrieving domain lists
• Collecting command results
• Network diagnostics

📈 Key Benefits

✔ Real-time network performance monitoring
✔ Distributed network testing with anchors
✔ Scalable asynchronous processing
✔ API health monitoring
✔ Detect latency and network issues early

🤝 Contributing

Fork the repository

Create feature branch

git checkout -b feature/new-feature

Commit changes

git commit -m "Add new feature"

Push changes

git push origin feature/new-feature

Create Pull Request

📜 License

MIT License

👨‍💻 Author

Swarup2908

GitHub Repository:
https://github.com/Swarup2908/Rtt_monitor

⭐ Your Contribution (You should add this)

Since you worked on this, you should include something like:

Contributions

• Developed Django backend for RTT monitoring
• Implemented Celery background tasks for continuous network checks
• Integrated external APIs for anchor and domain data
• Built monitoring logic for ping and DNS queries
• Implemented RTT calculation and network diagnostics
• Improved API monitoring and endpoint health checks
