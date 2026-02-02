# Network Automation Projects

Practical Python and Go automation projects focused on **network reliability**, **observability**, and **configuration management**.

This is a curated set of tools built to demonstrate real-world skills used in **Network Reliability Engineering (NRE)**, **SRE**, and **DevOps** roles.

---

## Focus Areas

- Automating configuration management and device interaction  
- Building observability and monitoring workflws  
- Collecting, storing, and querying telemetry data
- Scaling services using Kubernetes
- CI/CD workflows, including automated testing pipelines
- Applying best practices:
  - structured logging  
  - error handling  
  - CLI interfaces  
  - maintainable, readable code  

---

## Projects

### News Sentiment Comparison
Repo: network-automation-projects/news-sentiment-comparison

Full-stack system that orchestrates scheduled headline collection from multiple sources (REST APIs + RSS), processes sentiment scoring, persists results, and serves them through a REST API with a React dashboard. While the project includes a frontend, the portfolio emphasis is on backend reliability: ingestion pipelines, validation, persistence, observability, and CI/CD.

The API is deployed as a live service using a managed hosting platform (Render), demonstrating environment-based configuration, build pipelines, and runtime logging. Kubernetes manifests are included for orchestration and scaling practice in a local cluster.

**Key features**
- FastAPI backend with clear API contracts and health checks
- Scheduled collection pipeline (batch ingestion → compute → persist → serve)
- MongoDB persistence with resilient read/write patterns
- Observability: Prometheus metrics endpoint and Grafana dashboards
- Docker + Kubernetes manifests for containerization and orchestration practice
CI/CD pipeline with automated linting, testing, secret detection, and smoke validation
- React frontend dashboard for visualization and interaction
- Reuses the Go-Monitor Project to scrape and visualize API usage metrics into Grafana and Prometheus

**Design considerations**
- Explores tradeoffs between document-style and relational data models based on ingestion flexibility, query patterns, and aggregation needs
- Separates ingestion, processing, and API layers for clarity and maintainability
- Designed to fail fast in CI when quality or safety checks do not pass

---

### Go Prometheus Metrics Service
Repo: network-automation-projects/go-monitor

Lightweight Go service exposing custom Prometheus metrics to demonstrate application-level observability, metric instrumentation, and monitoring workflows commonly used in SRE and platform engineering environments.

This project implements a minimal HTTP service written in Go that publishes operational metrics in Prometheus format. It demonstrates how applications expose internal state for scraping, aggregation, and alerting in production monitoring systems.

**Key features**
- Custom Prometheus metrics implemented using the Go Prometheus client
- HTTP server exposing a /metrics endpoint
- Example metrics like:
  - Request counts
  - Request duration
  - Application health indicators
- Designed to integrate with Prometheus scraping and Grafana dashboards
- Used by other projects in this organization (e.g., News Sentiment Comparison) to expose and visualize real API usage metrics.


---

### Kubernetes Fundamentals Lab
Repo: network-automation-projects/docker-kubernetes-demo

Hands-on Kubernetes lab demonstrating core container orchestration concepts using Pods, Deployments, and Services. The lab progresses from fragile single-pod deployments to production-ready, self-healing, load-balanced applications.

**Key features**
- Declarative Infrastructure using YAML manifests
- Pod Lifecycle Management as the basic execution unit
- ReplicaSets & Fault Tolerance through Deployments
- Self-Healing via automatic pod replacement
- Service Discovery with stable networking abstractions
- Load Balancing across multiple replicas
- Safe Teardown & Redeploy Workflows

---

### Config File Automator
Repo: network-automation-projects/file-automator 

Python CLI tool for safe backup and recursive modification of YAML and JSON configuration files.

**Key features**
- Timestamped backups before changes  
- Recursive placeholder replacement in nested structures  
- Comprehensive logging and robust error handling  

**Use case**  
Automating configuration updates across network services or devices.

---

### Automation Preflight Validation Tool
Repo: network-automation-projects/automation-preflight

Python CLI tool that validates device and environment readiness before automation runs. This project focuses on preventing unsafe changes by separating validation, planning, and execution concerns.

The tool is designed as a guardrail for automation workflows, ensuring prerequisites are met before any configuration or action is attempted.

**Key features**
- YAML-based inventory and configuration loading
- Input validation using structured schemas
- Pre-execution checks (connectivity, OS version, uptime, required variables)
- Dry-run mode to validate inputs without making changes
- Clear exit codes to signal validation outcomes
- Structured logging for auditability and troubleshooting

**Use case**
Reducing risk in network automation by failing fast when prerequisites are not met.

---

### Automation Failure Simulator
Repo: network-automation-projects/automation-failure-simulator

Python-based simulation tool designed to model partial failures and error conditions commonly encountered in automation workflows. This project explores how automation behaves when things go wrong, rather than expecting success.

**Key features**
- Simulated failure scenarios (timeouts, partial responses, invalid state)
- Explicit handling of recoverable vs non-recoverable errors
- Retry and backoff patterns
- Structured error reporting and logging
- Designed to test idempotency and failure handling logic

**Use case**
Practicing resilient automation design by validating behavior under partial failure and degraded conditions.

---

### Network Telemetry Manager
Repo: network-automation-projects/telemetry_db

Python tool for storing, querying, and analyzing mock network telemetry data using SQLite.

**Key features**
- Stores metrics (latency, packet loss, etc.) per device  
- Aggregation queries (e.g. average latency)    
- JSON export for dashboards or APIs  

**Use case**  
Simulates observability pipelines similar to Prometheus, Grafana, or SolarWinds-style workflows.

---

### Netmiko Dashboard
Repo: network-automation-projects/dashboard-netmiko

First version simply imported netmiko class and showed mock data strings.  New version connects to Nokia practice servers using multiple concurrent connections with ThreadPoolExecutor, collects device facts and performs configuration backups in parallel, with data persisted in SQLite and exposed through a REST API.

**Planned features**
- Concurrent SSH connections to multiple network devices using ThreadPoolExecutor
- Device fact collection (hostname, model, OS version, uptime, etc.)
- Automated configuration backups executed in parallel
- Persistent storage of device data and backups using SQLite
- REST API for querying collected device information
- Designed to support both mock data (early development) and live device connections
- Structured logging and error handling for connection and execution failures

**Current state**
Initial version used mocked Netmiko responses for UI and data flow testing
Current version connects to Nokia practice servers and performs real SSH sessions

---

### Ansible Network Automation Demo
Repo: network-automation-projects/ansible_demo

Ansible playbooks for automating common Cisco IOS workflows in sandbox environments.  falls back to mock data when sandbox is not available.

Key features:
- Configuration backups
- Device fact gathering
- Basic validation checks
- Idempotent, repeatable runs

Use case:
Practicing declarative network automation and validating configurations safely using Ansible.

---

### API & Infrastructure Tooling (Hands-on Labs)

In addition to the repositories here, I’ve completed structured hands-on labs focused on building and testing RESTful APIs using Python and FastAPI.

These labs covered:
- CRUD API design
- OAuth-based authentication flows
- MongoDB-backed data models
- Request validation with Pydantic
- Introductory scalability and API testing concepts

This work complements the automation projects by strengthening API design and service integration skills.

---

## Motivation

These tools were built as targeted preparation for roles involving:

- Automation of network provisioning and configuration  
- Interfacing with network devices and APIs  
- Designing internal observability systems  
- Reducing operational toil through reliable scripting  

The projects reflect common expectations such as Python proficiency, familiarity with Netmiko/NAPALM, telemetry data handling, and SRE-oriented thinking.

---

## Maintenance

Maintained by **Rebecca Clarke**  
Software Engineer — Network Automation & Reliability  

Primary portfolio work for this domain lives within this organization.

LinkedIn: https://www.linkedin.com/in/rclarke009/

--- 

Feel free to explore, fork, or star the repositories. Feedback via issues is welcome.
