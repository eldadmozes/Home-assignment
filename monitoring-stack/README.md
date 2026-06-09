# Docker Monitoring Stack

## Overview

This project implements a complete monitoring stack using Docker Compose.

The stack includes:

* PostgreSQL
* MongoDB
* Prometheus
* Node Exporter
* PostgreSQL Exporter
* MongoDB Exporter
* Grafana

The monitoring solution provides visibility into:

* Host performance metrics
* PostgreSQL database metrics
* MongoDB database metrics

All services are deployed using Docker Compose and communicate through a dedicated Docker network.

---

## Architecture

```text
+-------------+
|   Grafana   |
+------+------+ 
       |
       v
+-------------+
| Prometheus  |
+------+------+ 
       |
       +--------------------+
       |                    |
       v                    v
+--------------+     +--------------+
| Node Exporter|     | Mongo Export |
+--------------+     +--------------+
       |
       v
+--------------+
| Postgres Exp |
+--------------+

```

---

## Components

### PostgreSQL

* PostgreSQL 16
* Persistent storage
* Exposed on port 5432

### MongoDB

* MongoDB 7
* Persistent storage
* Exposed on port 27017

### Prometheus

* Metrics collection and storage
* Exposed on port 9090

### Node Exporter

Collects:

* CPU metrics
* Memory metrics
* Disk metrics
* Network metrics

### PostgreSQL Exporter

Collects:

* Active connections
* Transactions per second
* Database size
* Cache hit ratio

### MongoDB Exporter

Collects:

* Connections
* Uptime
* Operations per second
* Memory usage

### Grafana

Visualization platform with preconfigured Prometheus datasource.

Exposed on port 3000.

---

## Dashboard Metrics

### Host Metrics

* CPU Usage (%)
* Memory Usage (%)
* Disk Usage (%)
* Network Traffic (Rx/Tx)

### PostgreSQL Metrics

* Active Connections
* Transactions per Second
* Database Size
* Cache Hit Ratio

### MongoDB Metrics

* Connections
* Uptime
* Operations per Second
* Memory Usage

---

## Project Structure

```text
.
├── docker-compose.yml
├── .env
├── README.md
├── prometheus/
│   └── prometheus.yml
└── grafana/
    ├── provisioning/
    │   ├── datasources/
    │   │   └── datasource.yml
    │   └── dashboards/
    │       └── dashboards.yml
    └── dashboards/
        └── monitoring-dashboard.json
```

---

## Deployment

### Prerequisites

* Ubuntu 22.04+
* Docker
* Docker Compose

Verify installation:

```bash
docker --version
docker compose version
```

---

### Start the Stack

```bash
docker compose up -d
```

Verify containers:

```bash
docker ps
```

---

## Access

### Grafana

```text
http://localhost:3000
```

Default credentials:

```text
admin / admin123
```

### Prometheus

```text
http://localhost:9090
```

### PostgreSQL

```text
localhost:5432
```

### MongoDB

```text
localhost:27017
```

---

## Verification

Verify Prometheus targets:

```text
http://localhost:9090/targets
```

Expected status:

```text
UP
```

for:

* node-exporter
* postgres-exporter
* mongodb-exporter
* prometheus

---

## Features

* Docker Compose deployment
* Dedicated Docker network
* Persistent volumes
* Health checks
* Environment-based configuration
* Grafana provisioning
* Prometheus monitoring
* Database monitoring
* Infrastructure monitoring

---


